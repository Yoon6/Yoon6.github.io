---
title: 선형회귀; Linear Regression
date: 2020-10-16 23:40:00 +0900
categories: [Programming, ML]
tags: [machine-learning, linear-regression]     # TAG names should always be lowercase
---

- 회귀
- 선형 회귀
- 가설, 가설함수
- 비용, 비용함수
- 비용 최소화 - 머신러닝의 핵심

## 회귀; Regression

> "Regression toward the mean"

여기서 mean은 전체 평균을 의미한다.

크거나, 작거나, 어떤 값이 있더라도 전체적으로 보면 평균으로 회귀(되돌아가는)하는 특징, 속성이있다.

## 선형 회귀; Linear Regression

데이터들을 가장 잘 대변하는 직선(일차함수)를 구하는 것이다.

$y=ax+b$ 

위의 식에서 기울기인 a값과 y절편인 b값을 구하는 것이 목적이다.

## 가설; Hypothesis

![Untitled.png](/assets/img/post/4/Untitled.png)

![Untitled%201.png](/assets/img/post/4/Untitled%201.png)

$H(x)=Wx+b$

가설 함수는 이처럼 표현한다. W는 weight, b는 bias를 나타낸다.

주어진 데이터에 가장 적합한 가설함수(일차방정식)를 찾는 것이 목표이다.

## 비용; Cost

그러면 가장 적합한 함수는 어떻게 구하나?

비용 개념을 알아야한다. 각각의 데이터에서 가설 함수가 얼만큼 떨어져 있는지를 알면된다. 그 오차값을 점점 줄여나가는 것이다.

![Untitled%202.png](/assets/img/post/4/Untitled%202.png)

$H(x)-y$ 값은 음수가 될 수 있기 때문에, 이 차이값을 나타내는 척도는 제곱을 이용하여 정의한다.

$\dfrac{(H(x_1)-y_1)^2+(H(x_2)-y_2)^2+(H(x_3)-y_3)^2}{3}$으로 나타낸다.

일반화 하면

$cost(W) =\dfrac{1}{m}\displaystyle\sum_{i=1}^m(Wx_i-y_i)^2$ 이렇게 나타낸다.

비용 함수는

$cost(W, b)=\dfrac{1}{m}\displaystyle\sum_{i=1}^m(H(x_i)-y_i)^2$ 이다.

## 목표

결국 선형회귀를 사용하는 머신러닝의 목표는 $cost(W,b)$를 최소화하는 $W$와 $b$를 찾는 것이다.

## 추가 설명; 그러면 컴퓨터는 어떻게 학습을 하는가?

만약 $y=2x$에 라는 함수를 구한다고 해보자. a=2, b=1이 되어야하는 것이다.

위의 함수는 모른채로 x=1,2,3,4,5,... y=2,4,6,8,10,... 이렇게 주어진다면,

처음에는 임의의 숫자를 세팅한다. 만약 a=0, b=0로 세팅된다면 무슨 값을 넣든 0이 나올 것이다.

이 때 나오는 결과값과, 데이터값을 비교하여, a와 b를 조절해나간다. 

비용 함수를 최소화하는 방향으로 a,b를 조절한다.

### 경사 하강법; Gradient Descent

그렇다면 비용을 최소화하는 지점을 구하려면 어떻게 해야하나?

만약 비용 함수의 그래프가 아래와 같은 형태라면 목표지점, 즉 비용이 가장 낮아지는 지점의 a와 b값을 구하면 되는 것이다.

![Untitled%203.png](/assets/img/post/4/Untitled%203.png)

이 때 미분을 사용하여(a와 b로 미분한다.) 기울기 값의 증감에 따라 a,b값을 조절해가면서 목표지점에 가까워지게 하는 것이다.

더 자세히 알아보자.

처음에 설정한 직선을 H(x)=Wx라 두고, 이 것의 비용 함수를 최소로하는 W를 찾는 것이 목적이다.

![Untitled%204.png](/assets/img/post/4/Untitled%204.png)

W는 처음에 초기화한 상수이다. 

α는 learning_rate로 학습속도를 조절하는 상수이다. 이 역시도 초기화한다. 

α은 적절하게 조절해주어야한다. 너무 작으면 목표값을 찾는것이 오래걸리게 되고, 너무 크면 목표값을 지나쳐버릴 수 있기 때문이다. W값 업데이트 가중치라고 생각하자.

그리고 남은 부분은 비용 함수를 W로 편미분 한것이다.

(편미분은 다변수 함수의 특정 변수를 제외한 나머지 변수를 상수로 생각하여 미분하는 것이다.)

결국 비용 함수를 편미분한 것을 통해 W를 변화시켜 최적의 W를 구하는 것이다.

위에서 본 것과 같이 W에 변화에 따라 비용 함수가 그려지기 때문에, 최소가 되는 지점, 즉 접선의 기울기가 0과 가까운 지점에서의 W가 목표값이 된다고 할 수 있다.

만약 가설 함수에 y절편이 있는 H(x) = Wx + b 형태라면, b를 W2라고보고 문제를 푼다.

즉 H(x) = Wx + W2x를 풀어야한다.

이 때는 비용함수가 3차원이 된다. 이후의 과정은 머신러닝이 해결해준다.

![Untitled%205.png](/assets/img/post/4/Untitled%205.png)

---

## 참고자료

[[TensorFlow] Lec-02-Simple Liner Regression](https://youtu.be/Mx7oqTKwhIA)

[[머신러닝] 컴퓨터가 학습을 하는 원리](https://youtu.be/ZY6eBxyEOq0)

[5. 머신러닝 알고리즘 : 선형회귀(linear regression)](https://nittaku.tistory.com/284)