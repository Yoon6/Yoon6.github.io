---
title: MIPS 기본
date: 2020-10-05 21:30:00 +0900
categories: [Programming, Assembly]
tags: [assembly, mips]     # TAG names should always be lowercase
---
## Hello Assembly

MIPS에는 `data`영역과 `text`영역이 있다. `.data` `.text`로 표기한다.

data영역에는 모든 데이터 포함된다. 예를들어 고급 언어의 변수 선언부와 같다.

text영역에는 명령어를 작성한다.

```
.data
	myMessage: .asciiz  "Hello World \n"

.text
	li $v0, 4 # 프로그램에게 출력하겠다고 알려주는 것 
	# myMessage 변수를 출력하고 싶다.
	# 레지스터에 넣어서 출력해야한다. a0사용 
	la $a0, myMessage
	syscall # do it
```

## Printing an Integer

어떻게 정수를 정의하는 지.

`word`는 32비트 4바이트이다. 정수형을 정의할 때는 32비트, 4바이트, 즉 1워드가 필요하다.

```
.data
	age: .word 20 # this is a word or integer.

.text 
	#print integer on the screen.
	li $v0, 1 # Integer, 1word를 출력할 준비를 해라.
	lw $a0, age # lw = load word, a0= argument레지스터 사용. 
	syscall # call do it
```

## Adding Integer

정수의 덧셈.

2개의 변수를 정의한다. 이는 메모리에 임의로 접근한다.

덧셈은 프로세서에서 이루어지기 때문에, 레지스터로 로드해서 사용해야한다.

`lw` 는 load word의 약자로 값(a word)을 메모리에서 가져와서 레지스터로 넣어라는 명령어이다.

```
.data
	number1: .word 5
	number2: .word 10

.text
	lw $t0, number1($zero)
	lw $t1, number2($zero)
	
	add $t2, $t0, $t1 # t2 = t0 + t1
	
	li $v0, 1
	add $a0, $zero, $t2
	syscall
```

## Multiplying Integers

`mul`과 `mult` 명령어로 곱셈을 수행한다.

또 `sll` 명령어도 있다. 이는 매우 효과적이지만 능동적이지 못하다. 

`addi`는 immediate값(변수x, 정수)과 덧셈 연산을 수행한다.

```
.data
	
.text
	addi $s0, $zero, 10
	addi $s1, $zero, 4
	
	mul $t0, $s0, $s1
	
	
	# display 
	li $v0, 1
	add $a0, $zero, $t0
	syscall
```

## Introduction to Functions

같은 내용을 여러 번 호출할 때 사용.

`main:` 레이블은 프로그램의 메인함수, 메인 모듈이라고 할 수 있다.

`jr $ra` : 리턴 주소이다.

`caller`(여기서는 main) 프로그램의 끝을 알려주는 코드가 있어야한다. 

`jal displayMessage` : displayMessage함수로 jump한다. callee(dis~함수) `jr $ra`가 호출되면 이부분으로 돌아온다.

```
.data
	message: .asciiz "Hi, everybody.\nMy name is Yoon.\n"
.text
	main: #caller
		jal displayMessage
			
		addi $s0, $zero, 5
		
		# print
		li $v0, 1
		add $a0, $zero, $s0
		syscall
	
		#tell the system that program is done
		li $v0, 10
		syscall
	
	displayMessage: # callee
		li $v0, 4
		la $a0, message
		syscall
		
		jr $ra
```

## Conditional statement

if문의 기능.

```
.data
	message: .asciiz  "The numbers are equal."
	message2: .asciiz  "Nothing happened"
.text
	main:
		addi $t0, $zero, 20
		addi $t1, $zero, 20
		
		# if t0==t1? , branch equal
		beq $t0, $t1, numbersEqual
		
		# branch not equal
		#		bne $t0, $t1, numbersDifferent
		
		# Syscall to end programs
		li $v0, 10
		syscall
	
	numbersEqual:
		li $v0, 4
		la $a0, message
		syscall
		
	numbersDifferent:
		li $v0, 4
		la $a0, message2
		syscall
```

## While Loop

while문의 기능.

`while:` 과 `exit:` 이 필요하다.

```
.data
	message: .asciiz  "After while loop is done"
	space: .asciiz  ", "
.text
	main:
		# i=0
		addi $t0, $zero, 0
		
		while:
			# t0 < 10 -> exit
			bgt $t0, 10, exit
			
			jal printNumber
			
			# i++
			addi $t0, $t0, 1
			
			# 반복시키는 명령어, while로 jump
			j while 
		
		exit:
			li $v0, 4
			la $a0, message
			syscall
		
		
		# end of program
		li $v0, 10
		syscall
		
	printNumber:
		li $v0, 1
		add $a0, $t0, $zero
		syscall
		
		li $v0, 4
		la $a0, space
		syscall
		
		jr $ra
```
---

# 참고 자료
[MIPS Assembly Programming Simplified](https://www.youtube.com/playlist?list=PL5b07qlmA3P6zUdDf-o97ddfpvPFuNa5A)