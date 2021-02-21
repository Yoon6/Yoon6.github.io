---
title: Basic Java OOP concepts
date: 2021-02-21 19:18:00 +0900
categories: [Programming, Java]
tags: [oop, object-oriented programming, java]     # TAG names should always be lowercase
---

# What is the OOP?
OOP(object-oriented programming) is the concept of creating program focused on 'Object'.
Here, the word 'object' means something in real world, such as TV, smartphone, air conditioner, etc...
These properties of object are defined in computer world.

### So, why we use OOP?
OOP has four main features.
1. Inheritance
2. Encapsulation
3. Abstraction
4. Polymorphism

Thanks to these, OOP has advantages.
1. Reusable
2. Maintenance
3. Remove overlapping code.

See the following code.
These codes are not efficient.
```java
public class oop1 {
    public static void main(String[] args) {
        // implement calculator
        int a,b,c;
        a = 1;
        b = 2;
        c = a + b;
        System.out.println(a+"+"+b+"="+c);

        a = 5;
        b = 2;
        c = a - b;
        System.out.println(a+"-"+b+"="+c);

        a = 3;
        b = 6;
        c = a * b;
        System.out.println(a+"*"+b+"="+c);
    }
}
```
Let's use the class to make calculator.
```java
class cal{
    int a, b;
    public cal(int a, int b){
        this.a = a;
        this.b = b;
    }

    int add(){
        return a+b;
    }
    int subtract(){
        return a-b;
    }
    int multiply(){
        return a*b;
    }
    int divide(){
        return a/b;
    }
}

public class oop1_class {
    public static void main(String[] args) {
        cal[] c = new cal[3];
        c[0] = new cal(1,2);
        c[1] = new cal(5,2);
        c[2] = new cal(3,6);
        System.out.println(c[0].add());
        System.out.println(c[1].subtract());
        System.out.println(c[2].multiply());
    }
}
```
Assuming that we do a billion calculations, class is more efficient than before.

---
# Class vs Object

### Class
- Class is definition of object.
- Class is used to create object.

### Object
- Object is created in the memory as defined in the class.

For example, a real product such as TV can be called object, and this design(blue print) can be called class.

In addition, class is also called combination of datas and functions, or user-defined type.

---
# Object vs Instance

Normally, the object is used in the same meaning as the instance.
But, it is a very little different.

The process of making class to object is called 'instantiate'.

Object represents all instances. so that, object has comprehensive meaning.

The object of a particular class is called instance.

For example, assume that we have TV, We can be called that "TV is the object".
And then, we can be call that "TV is instance of the TV class".

If you want to know more about it, read this [post](https://alfredjava.wordpress.com/2008/07/08/class-vs-object-vs-instance/).

---
# Property and Function of Object

The object components are property and function.

For example, assume that we have a simple smartphone.
This smartphone has property such as volume, brightness, power...
Features are volume up, down and brightness up, down, and power on, off. 

Let's code.
```java
class Smartphone{
    boolean power;
    int volume;
    int brightness;
    
    void power(){
        power = !power;
    }
    void volumeUp(){
        volume++;
    }
    void volumeDown(){
        volume--;
    }
    void brightnessUp(){
        brightness++;
    }
    void brightnessDown(){
        brightness--;
    }
}
```

We call this function and property as method and variable.

---
# Create and use instance

To use class, you create instance.

First, to create instance, you define reference variable.
Reference variable is the address that contains the address of the instance of the class.

Next, use the `new` keyword to create instance.

Finally, to use this class's variable and method, use `.`(dot).

```java
// Java
Smartphone sp;
sp = new Smartphone();

// or
Smartphone sp = new Smartphone();

sp.volume = 7;
sp.volumeUp(); // sp.volume == 8
sp.power(); // sp.power == true, default is false.
```