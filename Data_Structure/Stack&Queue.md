# **스택과 큐**

<br>

## **1. 스택(Stack)**

<br>

![스택2](https://user-images.githubusercontent.com/89771322/151664014-651f17b1-2fb0-45ba-a74b-4cac1347cb57.png)

<br>

스택은 위 사진 처럼 아래가 막혀있는 공간에 **데이터를 차곡차곡 쌓아가는 자료구조**이다. 이러한 구조를 가졌기에 목록의 끝을 통해서만 데이터에 접근할 수 있다. 스택 구조에서 목록의 끝을 통해서 데이터를 삽입하는 것을 `push`라 하고 목록의 끝을 통해서 데이터를 삭제하는 것을 `pop`이라고 한다. 

현실에서도 아래가 막힌 상자에 책을 차곡차곡 쌓은 뒤 책을 꺼내려면 맨 위에서부터 꺼내야 하는 것과 마찬가지로 pop을 통해서는 가장 마지막에 삽입된 데이터가 삭제된다.

이러한 스택의 구조를 **LIFO(Last In First Out)** 라고 한다.

<br>

>이러한 스택이 활용되는 예시로는 **인터넷 뒤로가기**나 이전 상태로 돌아가는 **control+z** 등이 있다.

<br>

## **2. 큐(Queue)**

<br>

![큐](https://user-images.githubusercontent.com/89771322/151664457-74b9cc70-2022-4529-92de-9ee89e99e624.png)

<br>

큐는 스택과 달리 **데이터가 삽입되고 삭제되는 곳이 다르다.** 영어로 queue는 표를 사기 위해 사람들이 일렬로 서있는 줄을 말하기도 한다고 한다. 즉, **FIFO(First In First Out)** 맨 처음 들어온 사람이 제일 빨리 나가는 구조인 것이다.

큐에서 데이터의 삭제가 이뤄지는 곳을 **front**, 삽입이 이뤄지는 곳을 **rear**라고 한다. rear통해 데이터를 삽입하는 것을 `enQueue`라고 하고 fornt를 통해 데이터가 삭제되는 것을 `dnQueue`라고 한다.

> 큐는 자료의 순서를 보장하는 구조이기 때문에, **자료를 순서대로 처리해야할때 주로 사용된다고 한다.** 예를 들어 프린터기의 출력작업, 은행 업무 등이 있다.

<br>
<br>
<hr>

### *참고자료*
https://ko.wikipedia.org/wiki/%ED%81%90_(%EC%9E%90%EB%A3%8C_%EA%B5%AC%EC%A1%B0) <br>
https://ko.wikipedia.org/wiki/%EC%8A%A4%ED%83%9D <br>
https://devuna.tistory.com/22 <br>
https://mygumi.tistory.com/357 <br>