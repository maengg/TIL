# **검색 알고리즘**

<br>

## **1. 선형 검색**

<br>

검색은 어떤 데이터를 추가하거나 삭제하거나 할때 선행되는 작업이다. 우리가 'ㄱ-ㅎ' 순으로 잘 정리된 책장에 'ㄷ'으로 시작하는 책을 꽂고 싶을때 우리는 'ㄱ'으로 시작하는 책에서 부터 천천히 'ㄷ'으로 시작하는 책을 찾은 뒤에 책을 알맞은 위치에 놓을 것이다. 여기서 **책을 알맞은 위치에 놓은 것은 데이터를 삽입하는 작업이**고 이를 위해 **'ㄱ'에서 'ㄷ'까지 천천히 책을 찾아갔던 과정을 검색(탐색)** 이라고 할 수 있다.

<br>

### ***선형 검색 (Linear search)***

선행 검색은 **데이터의 시작 점부터 차례 대로 비교해가며 원하는 값을 검색**하는 방법이다. 즉, 앞에서 말했던 'ㄱ'에서 'ㄷ'까지 찾는 검색 방법을 선행 검색이라고 할 수 있다. 선행검색의 경우 데이터의 처음부터 순차적으로 검색을 진행하기에 시간복잡도는 **O(n)** 이다.

<br>

<img width="599" alt="linearSearch" src="https://user-images.githubusercontent.com/89771322/151350593-5885d0e9-dcdd-4940-af46-acfd504535ce.png">


*그림은 선행 검색으로 J를 찾는 과정을 보여준다.*

<br>

***선행 검색은 아래와 같이 구현할 수 있다.***


```python
def linear_search(arr, search_value): 
    for idx in range(len(arr)):
        if arr[idx] == search_value:
            return idx # 찾고자 하는 값의 인덱스 반환.
```

<br>

## **2. 이진 검색 (Binary search)**

<br>

이진 검색의 경우 검색하고자 하는 범위를 반으로 줄여가며 검색을 진행한다. 검색하는 과정은 다음과 같다.

<br>

![binary_search](https://user-images.githubusercontent.com/89771322/151357737-8a763b6c-91b9-4bab-a34f-96622d9e6fdd.gif)

*(아래 그림은 선형 검색)*

<br>

1. 데이터의 범위에서 가운데 있는 값을 찾는다.
2. 찾은 값과 검색하고자 하는 값을 비교한다.
3. 찾은 값이 검색하고자 하는 값보다 크다면 찾은 값을 최대값으로 반대의 경우 최소값으로 설정하여 검색 범위를 좁힌다.
4. 재설정된 범위에서 위의 과정을 반복한다.

<br>

이진 검색은 가운데에 위치한 값과의 대소 비교를 통해 범위를 좁혀간다. ***즉, 데이터가 우선적으로 정렬이 되어 있어야 사용할 수 있다.***

이진 검색의 시간 복잡도는 **O(log n)** 이 나온다. 이를 알기 위해서 1-8까지의 데이터에서 8을 찾는 과정을 생각해보자.

이진 검색을 진행하면 탐색해야할 데이터의 범위는 8→4→2→1로 줄어든다. 즉, 총 3번의 시행으로 원하는 값을 찾을 수 있는 것이다. 정리하면, **탐색하고자 하는 데이터의 개수가 2^n개인 경우 이진 검색을 활용하면 n번의 시행으로 데이터를 찾을 수 있다.** 그렇기에 시간 복잡도가 O(log n)이 되는 것이다.

<br>

***이진 검색은 아래와 같이 구현할 수 있다.***

```python
def binary_search(arr, value):
    high = len(arr)-1 # 제일 마지막 index
    low = 0 # 제일 첫번째 index
    while low <= high:
        mid = (high+low)//2 # 가운데 index
        if arr[mid] == value: # 값을 찾으면 index 반환
            return mid
        elif arr[mid] > value: # mid 값이 더 크면 범위 수정
            high = mid-1
        else: # mid 값이 더 작으면 범위 수정
            low = mid+1
    return '값이 없습니다' # 반복문을 빠져나온 건 값을 찾지 못했다는 말
```

<br>
<br>
<hr>

### *참고자료*
https://velog.io/@nninnnin7/logN%EC%9D%98-%EC%8B%9C%EA%B0%84-%EB%B3%B5%EC%9E%A1%EB%8F%84-%ED%8E%8C <br>
https://neos518.tistory.com/145