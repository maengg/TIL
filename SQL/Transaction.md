# Transaction(트랜잭션)

<br>

## **1. 트랜잭션**

<br>

**트랜잭션**은 *데이터베이스의 상태를 변화시키는 작업들의 모음이다.* 예를 들자면, 'A가 B에게 100만 원을 계좌 이체하는 것.' 이 하나의 트랜잭션이다. A가 B에게 100만원을 이체하기 위해서는 다음과 같은 작업들이 필요하다.

<br>

A의 계좌가 활성화 되어있나? → A의 계좌에 100만 원이 있나? → A의 계좌에서 100만 원 출금 → B의 계좌가 활성화되어있나? → B의 계좌에 100만 원 입금. **이러한 과정을 하나의 트랜잭션이라고 말한다.**

<br>

이러한 트랜잭션의 안정성을 보장하기 위해 필요한 성질이 4가지 있다. **바로  원자성(Atomicity), 일관성(Consistency),  고립성(Isolation), 지속성(Durability)이고 이 4가지를 ACID라고 부른다.**

<br>

## **2. ACID**

<br>

### *1). 원자성*

<br>

원자성은 트랜잭션을 구성하는 작업들은 부분적으로 실행되면 안되고 **모두 성공하거나 모두 실패해야 된다는 성질이다.** 

<br>

다시 100만원을100만 원을 이체하는 상황을 생각해보자. 이때 A의 계좌에서 100만 원을 출금했는데 B의 계좌가 활성화되어있지 않은 경우 모든 작업이 실패로 끝나지 않으면 A의 계좌에 있던 100만 원만 없어진 꼴이 된다. *그렇기에 트랜잭션을 구성한 작업들 중 하나가 실패하면 모든 작업들이 실패로 끝나야 된다.*

<br>

### *2). 일관성*

 

일관성은 우리가 트랜잭션을 진행한 후 데이터베이스의 상태는 이전과 같이 유효해야 한다는 것이다. 이를 이해하기 위해서는 데이터베이스의 규칙과 제약에 대해서 알아야 한다.

<br>

~~~sql
CREATE TABLE A(
	id VARCHAR(10) PRIMARY KEY,
	name varchar(10)
);
~~~

<br>

 위에 만든 A라는 테이블의 경우 id와 name이 있어야 하는 제약이 있는 것이다. *이런 경우 id가 없는 데이터를 추가하거나 하나의 레코드에서 name만을 지워버린다거나 하는 트랜잭션 결과는 있어서는 안된다는 것이 일관성이다.*

<br>

### *3). 고립성*

<br>

고립성은 **트랜잭션이 서로 독립적이어야 한다는 거다.** 즉, 동시에 여러 트랜잭션을 실행해도 연속적으로 실행한 것과 같은 결과를 가져와야 된다는 것이다.

<br>

다시 계좌이체를 예로 생각해보자. 만약 100만 원이 있는 A라는 계좌에서 동시에 60만 원씩 B와 C라는 계좌로 이체하는 트랜잭션을 실행한다고 생각해보자. 고립성이 지켜지지 않는다면, 60만 원씩 동시에 이체하여 -20만 원이 될 것이다. 만약 해당 통장이 마이너스 통장이 아니라면 고객 입장에서는 황당한 상황일 수 밖에 없다. 반대로 고립성이 있는 경우에는 우선 60만 원을 하나의 계좌에 보내고 잔액부족으로 60만 원을 보내지 못하게 될 것이다.

<br>

### *4.) 지속성*

<br>

트랜잭션이 성공적으로 수행됐다면 해당 트랜잭션에 대한 기록이 남고 시스템적인 오류가 발생되더라도 해당 기록은 영구적이어야 한다는 뜻이다. 예를 들어 A가 B에게 성공적으로 100만원을 이체한 뒤 은행의 데이터베이스에 문제가 생겨도 해당 기록은 영구적으로 남아있어야 한다는 것이다.

<br>
<hr>
<br>

## **3. Commit**

<br>

*이러한 트랜잭션을 SQL에서 어떻게 데이터베이스에 반영하는지 알아보자.*

<br> 

트랜잭션이 데이터베이스에 반영되기 위해서는 확정 신호를 줘야 하고 확정 신호는 바로 **commit** 이다. 

<br>

~~~sql
INSERT INTO user VALUES ('id1', 'user1');
COMMIT;
~~~

<br>

만약 두번째의 COMMIT;이라는 확정 신호를 주지 않으면 해당 트랜잭션은 **데이터베이스에 반영되지 않고 Git에서의 staging area처럼 memory에만 남아있는 것이다.**

<br>

이렇게 commit을 하기 전에 **Rollback**을 사용하여 트랜잭션을 memory에서 뺄 수도 있다.

<br>

~~~sql
INSERT INTO user VALUES ('id1', 'user1');
ROLLBACK;
INSERT INTO user VALUES ('id2', 'user2');
COMMIT;
~~~

<br>

이렇게 Rollback을 사용하면, id1과 관련된 트랜잭션은 데이터베이스에 반영되지 않고 id2와 관련된 트랜잭션만 데이터에 반영된다.