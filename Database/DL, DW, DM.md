# **데이터 레이크, 데이터 웨어하우스, 데이터 마트**


<br>

*데이터 레이크와 데이터 웨어하우스를 데이터 분석가의 입장에서 보자면, 분석하고자 하는 데이터를 한 곳에 모아 두는 건 똑같다. 하지만 저장하는 방식에 차이가 있다.*

<br>

![test](https://user-images.githubusercontent.com/89771322/144604375-13e221f7-ffc9-4502-98cc-e5e9f21a2ba7.png?raw=true)
***[이미지 출처](https://www.grazitti.com/blog/data-lake-vs-data-warehouse-which-one-should-you-go-for/)***

<br>

## *1. 데이터 웨어하우스*
: 데이터 웨어하우스는 데이터를 저장하기 위해 하나의 스키마를 만들고 이 스키마를 활용해서 데이터를 저장한다. **즉, 정제된 데이터가 저장된다는 뜻이다.** 이렇게 데이터 웨어하우스에 데이터를 저장하는 과정을 자세히 보면 다음과 같다. 

<br>

  1. 정리되지 않은 데이터를 읽기 전용으로(데이터가 변형되면 안되니까) 가져온 뒤 추출(Extract)
<br>

2. 데이터를 분석하기 알맞게 변형(Transform)
<br>

3. 저장(Load)

<br>

이러한 과정을 **ETL**이라고 표현한다.

<br>

## *2. 데이터 레이크*
:반면, 데이터 레이크의 경우 raw 데이터 (비정형 데이터) 등을 정리하지 않고 그대로 저장한다. **즉, 데이터가 가지고 있는 원래 형태를 그대로 보존한 채로 저장하는 것이다.** 

처음 이 개념을 들었을때 당연하게 데이터 레이크의 개념이 먼저 생기고 데이터 웨어하우스의 개념이 생긴 줄 알았다. 근데 찾아보니 데이터 웨어하우스라는 개념이 먼저 존재하다가 이후에 데이터 레이크가 나온 걸 알게 되었다. (틀렸다면 말해주세요!) 

이러한 이유는 아마도 데이터 웨어하우스에 데이터를 저장하기 위해 정리하는 과정에서 **데이터 손실**도 생기고 하나의 스키마로 국한된 것이 아니라 데이터 분석가의 역량에 따라 **다양한 관점에서 데이터를 분석하고 싶은 욕구**가 있었기 때문인 것 같다.

<br>

## *3. 데이터 마트*
: 데이터 웨어하우스 회사의 모든 부서와 관련된 데이터가 저장되어 있다. **반면, 데이터 마트는 데이터를 각 부서 별로 정리해 둔 곳이다.**


<br>
<br>
<hr>
<br>

### *참고자료 :*
https://brunch.co.kr/@pubjinson/52

### *이미지 출처 :*
https://www.grazitti.com/blog/data-lake-vs-data-warehouse-which-one-should-you-go-for/