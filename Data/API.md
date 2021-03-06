# **API**



<br>
<br>

## **1. API 란?**

<br>

API는 Application Programming Interface 약자로 프로그램들이 소통할 수 있는 Interface로 어떤 프로그램을 다룰 수 있는 메뉴얼과 비슷하다. API를 이해하기 위해서는 **'클라이언트'** 와 **'서버'** 를 짚고 넘어가야 한다.

<br>

### *클라이언트와 서버*

<br>

클라이언트는 요청을 하는 자라고 생각하고 서버는 요청에 응하는 자라고 생각하면 되는데, 음식점을 예로 들어보자. 

<br>

음식점 고객들이 요청을하면 그 요청을 주방에 있는 셰프가 음식으로 응한다. 그렇기에 음식점에서 클라이언트는 고객, 서버는 셰프라고 생각할 수 있다. 앞에서 API는 어떤 프로그램을 다룰 수 있는 메뉴얼과 비슷하다라고 했는데, 그렇다면 음식점에서 AP는 뭐라고 할 수 있을까? 바로 '메뉴'다. 

고객들은 메뉴를 보고 이 음식을 주문하면 대충 어떤 음식이 나올 것이라 예상할 수 있고 그렇기에 직접 주방에가서 요리하는 것이 아니라 셰프에게 요청을 할 수 있는 것이다. 즉, 메뉴판이라는 API를 통해 클라이언트와 서버가 소통을 하는 것이다.

<br>

위에서 서버는 셰프라고 했는데, 생각해보면 우리는 셰프에게 직접 요청을 하는 것이 아니라 웨이터를 거쳐 셰프에게 음식을 요청한다. 셰프가 주문도 받고 조리도 한다면 손님이 몰리는 순간 그 음식점은 고객들의 요청을 응하기 매우 어려울 것이다. 그렇기에 고객의 요청을 전달하는 웨이터가 있는 것이다. 서버도 마찬가지이다. 서버는 **API Server(웨이터)** 와 **Servicce Server(셰프)** 로 나눌 수 있다.

API Server는 클라이언트가 API를 통해 Service Server에게 요청을 보낼 수 있도록 하는 중간다리 역할을 한다. API Server가 클라이언트의 요청을 전달하면 Service Server는 그 요청에 응한 결과를 API Server에게 전달해주고 API Server가 해당 결과를 전달해주는 것이다. *(여기서 결과에는 해당 요청이 성공했는지, 실패했는지 등의 여부도 포함되어 있다.)*

<br>

### *API 응답*

<br>

이렇게 요청을 보내면 응답을 받게 되는데 기본적으로 받는 응답으 형태는 JSON 형태이다. JSON은 자바스크립트에서 오브젝트를 표기하는 방식안데, 생김새가 파이썬의 딕셔너리와 유사하다. 즉, key와 value값으로 이루어져 있는 형태이다.

<br>

~~~jabascript
{
    "name" : "maneg"
    "age: : "18" 
    "country" : "Korea"
}
~~~

위의 자료는 JSON의 예시인데, 파이썬의 딕셔너리와 유사한 형태인 걸 볼 수 있다. 

<br>

<hr>

<br>

## **2. HTTP API**

<br>
<br>

### *HTTP*

<br>

**HTTP는 컴퓨터의 통신 규약 중 하나로 웹에서 사용되는 통신 규약이다.** 쉽게 생각하면 각 나라의 언어를 생각하면 된다. 예를 들어 한국에 오면 한국어로 소통하고 미국에 가면 영어로 소통하듯이 웹에서는 HTTP로 소통하는 것이다. HTTP는 크게 요청(HTTP Request)과 응답(HTTP Response)으로 나누어진다. 즉, 클라이언트가 HTTP Request 하고 서버가 HTTP Response 하는 것이다.

<br>

#### *HTTP Request*

클라이언트는 HTTP 메소드를 사용해서 서버에 요청을 보낸다. 데이터를 다룰 수 있는 CRUD에 사용되는 메소드는 다음과 같다.

<br>

* POST : 서버에 있는 특정 리소스를 저장하고 싶을 때. ***(CREATE)***
  * 예시: 회원 정보 저장.
* GET : 서버에 있는 특정 리소스를 달라고 할 때. ***(READ)***
  * 예시: 회원 정보 가져오기.
* PUT/PATCH : 서버에 있는 특정 리소스를 업데이트 할 때. (PUT 은 데이터 전부를 PATCH 는 부분적으로)  ***(UPDATE)***
  * 예시: 회원 닉넴임 변경.
* DELETE : 서버에 있는 특정 리소스를 삭제할 때. ***(DELETE)***
  * 예시: 회원 탈퇴.

이 외에도 다양한 요청 메소드가 있다.


#### *HTTP Response*

<br>

HTTP Response는 응답코드를 가지고 있다. 가장 중요한 성공 응답은 200 번대이다. 상태코드는 [HTTP Status Code](https://developer.mozilla.org/ko/docs/Web/HTTP/Status)서 확인 가능하다.


<br>
<hr>
<br>

## **3. REST API**

<br>

HTTP는 앞에서 말했듯 규격이다. 그런데 사실 요청을 보낼때 GET을 통해서 얻는 결과를 POST를 통해서도 얻을 수 있기에 이러한 규격은 잘 지켜지지 않았다. 그렇기에 똑같은 결과를 얻으려고 해도 A라는 API를 사용할 때는 GET을 B라는 API를 사용할 때는 POST를 써야하는 문제가 발생했다. 이러한 문제를 해결하기 위해 나타난 것이 ***'REST'*** 이다. 

REST에는 6가지 가이드라인이 있고 이 6가지 가이드라인을 모두 지킨 API를 **'RESTful API'** 라 한다. 다 지키지 못하더라도 몇개의 가이드라인을 지킨다면 **'REST API'** 라고 부른다. 6가지 가이드라인을 모두 지킨 RESTful API의 경우 보내는 주소만으로도 대략 어떤 요청인지 파악이 가능하다.

REST API를 작성했다고 하면 보통 HTTP를 다음과 같이 사용하기도 한다.

* GET : 데이터를 조회

* POST : 데이터를 생성
  
* PATCH : 데이터를 업데이트 (일부 변경)
  
* PUT : 데이터를 업데이트 (전체 변경)
  
* DELETE : 데이터 삭제

REST에서 주로 사용되는 응답 코드는 [여기](https://restfulapi.net/http-status-codes/)서 확인 가능하다.