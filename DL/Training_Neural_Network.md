# **1. 신경망 학습 (Training Neural Network)**

<br>

## **1. 신경망 학습 과정**

<br>


신경망 학습 과정은 다음과 같다.

<br>

1. *입력된 데이터들이 가중치 연산을 거친다.*
2. *이후 활성화 함수를 거쳐 출력된다.*
3. *출력된 값을 바탕으로 손실함수를 사용하여 손실을 계산한다.*
4. *역전파와 경사하강법을 통해 가중치를 업데이트 한다.*
5. *학습 기준을 만족할때 까지 1번~4번을 반복한다.*

<br>

위의 1번~2번을 순전파, 3번을 손실 계산, 4번을 역전파라고 할 수 있다. 즉, 학습 과정을 크게 **순전파 → 손실 계산 → 역전파**로 나눌 수 있는 것이다. 또한 1번~4번 과정을 **Iteration**이라고 부르고 각 Iteration마다 **가중치가 갱신된다.**

<br>
<br>

### *1) 순전파 (Forward Propagation)*

<br>

*순전파는 입력층에 전달된 신호들이 은닉층의 연산을 거쳐 출력층에 출력되는 과정을 말한다.* 자세한 과정은 다음과 같다.

<br>

1. *입력층에서 은닉층으로 신호를 보낸다.*
2. *은닉층에서 가중치-편향 연산을 수행한다.*
3. *연산을 통해 구해진 가중합이 출력층에서 활성화 함수를 통해 출력된다.*

<br>
<br>

### *2) 손실함수 (Loss function)*

<br>

신경망은 손실함수를 통해 계산된 **손실을 최소화하는 방향으로 가중치를 갱신한다.** 그렇기에 가중치를 제대로 갱신하기 위해서는 적절한 손실함수를 설정하는 것이 중요하다.

<br>

출력층에서 출력된 값을 손실함수에 넣어 손실을 계산하는데, 일반적으로 사용하는 손실함수는 다음과 같다.

<br>

* *회귀 → MAE, MSE*
* *이진 분류 → binary_crossentropy*
* *다중 분류 → categorical_crossentropy, sparse_categorical_crossentropy*

<br>
<br>

### *3) 역전파 (Backward Propagation)*

<br>

역전파는 말그대로 순전파와 반대로 진행된다. 역전파는 계**산된 손실 정보를 출력층에서 입력층까지 전달하면서 가중치를 어떻게 업데이트할지 구하는 알고리즘이다.**

이때 가중치를 어느 방향으로 갱신할지 결정해주는 것이 바로 **경사하강법**이다.

<br>
<br>

### *4) 경사하강법 (Gradient Descent)*

<br>

경사하강법은 말 그대로 가중치를 기울기가 작아지는 방향으로 이동하면서 손실이 가장 낮은 지점을 찾는 방법이다.

매 Iteration 마다 해당 가중치 지점에서 손실함수의 미분값(기울기)을 구하고 기울기가 작아지는 방향으로 가중치를 갱신하는 것이다. 가중치는 다음과 같이 갱신되는데 이때 역전파의 주요 메커니즘인 편미분과 연쇄 법칙(Chain rule)을 사용한다.

<br>

***업데이트된 가중치 = 현재 가중치 - 학습률 X 손실함수를 해당 가중치로 편미분한 값***

<br>
<br>
<hr>
<br>
<br>

## **2. 옵티마이저 (Optimizer)**

<br>

옵티마이저는 쉽게 말해서 경사를 내려가는 방법을 결정하는 것이라고 했다. 옵티마이저에는 다양한 종류가 있지만, 오늘은 **확률적 경사 하강법 (SGD)과 미니 배치(Mini-batch) 경사하강법**에 대해 배웠다.

<br>

### *SGD :*

일반적인 경사하강법은 매 Iteration마다 모든 데이터를 입력하고 이를 바탕으로 가중치를 갱신한다. 데이터가 적을 경우에는 문제가 없겠지만, 데이터가 많을 경우 가중치 갱신에 너무 오랜 시간이 걸리거나 메모리 과부화 등의 문제가 발생한다.

이를 해결하기 위해 등장한 것이 바로 확률적 경사 하강법 (SGD) 이다. SGD는 매 Iteration 마다 **전체 데이터에서 하나의 데이터를 입력하여 가중치를 갱신한다.** 그렇기에 매우 빠르게 가중치를 갱신한다. 하지만 하나의 데이터가 전체 데이터의 특성을 모두 반영할 수는 없기에 **학습 과정에서 불안정하게 경사를 내려온다는 단점이 있다.**

<br>

![sgd vs gradi](https://user-images.githubusercontent.com/89771322/146775479-58064724-5a39-4b79-ad63-1826e32aaa21.png)

<br>
<br>

### *미니 배치 경사하강법 :*
SGD의 단점을 보완하기 위해 일반적인 경사하강법과 SGD를 적절히 융화한 것이 바로 미니 배치 경사하강법이다.

미니 배치는 매 Iteration 마다 하나의 데이터를 뽑아서 입력하는 것이 아니라 **N개의 데이터로 미니 배치를 구성하여 입력하고 이를 바탕으로 가중치를 갱신하는 방법이다.** 이때 이 N개를 '배치 사이즈' 라고 부른다.

<br>

![sgd](https://user-images.githubusercontent.com/89771322/146775401-76f9fee7-4638-4165-a148-2ad4fcf45976.png)

<br>
<br>

### *배치 사이즈*:
배치 사이즈는 일반적으로 2의 배수로 설정한다. 배치 사이즈가 큰 경우와 작은 경우에는 각각 장단점이 있다.

<br>

**배치 사이즈가 작은 경우** 

→ **경사하강법을 통해 가중치를 갱신하는 과정이 불안정하기에 많은 Iteration이 필요하다**는 단점이 있다. 하지만 이러한 특성으로 인해 **지역 최저점(Local Minima)에서 빠져나올 가능성이 높아질 수도 있다.**

<br>

**배치 사이즈가 큰 경우**

→ 경사하강법을 통해 가중치를 갱신하는 과정이 안정적이기 때문에 학습 속도가 빨라진다. 하지만 너무 클 경우 Out-Of-Memory 문제가 발생할 수 있다.

<br>

전체 데이터와 배치 사이즈 그리고 Iteration은 아래와 같은 식을 만족한다.

***전체 데이터 = 배치 사이즈 X Iteration***

<br>

이렇게 전체 데이터를 다 돌았을 때가 1 epoch가 진행된 때이다. 예를 들어, 1,000개의 데이터가 있을때 배치 사이즈를 100으로 설정하고 `epochs=5`로 설정하면 총 Iteration은 *10X5(epochs)* 가 되는 것이다.