# 8. DB

## 1) 스키마(Schema)

#### "데이터베이스의 논리적 구조와 제약 조건에 대한 명세를 기술 한 것(설계도)"
* 논리 스키마(개념 스키마)
    * 데이터 베이스의 전체적 구조를 기술
        * ex) 데이터 타입, 개체 간의 관계, 제약 조건 등...
    * 내부 스키마와 외부 스키마의 중간
    * 모든 외부 스키마를 제공할 수 있도록 설계되어야 함 
* 물리 스키마(내부 스키마)
    * 실제 물리적으로 저장되는 구조(data type, size 등 지정)
    * 사용자 눈에는 보이지 않음
* 외부 스키마(서브 스키마)
    * 사용자에게 보여지는 외적구조
    * 최종 사용자(End User)와 관련
    * 사용자의 요구사항을 도출하는 과정
    ex) 회사 경비실에서는 회사원의 이름과 부서를 읽기만 할 수 있다.
    * 사용자의 관점에서 보고자 하는 정보의 집합

## 2) 도메인(Domain)

#### "엔티티의 속성들이 가질 수 있는 값들의 집합"
* 엔티티(Entity)
    * 업무에 필요하고 유용한 정보를 저장하고 관리하기 위한 "어떤 것(Thing)"
    * 데이터베이스 테이블이라고 생각
#### "대부분의 DBMS에서 도메인이란 속성에 대응하는 컬럼에 대한 데이터 타입(Data Type)과 길이를 의미"

* 도메인을 이용한 컬럼 데이터 타입 지정
```sql
CREATE DOMAIN SEX CHAR(1)
       DEFAULT 'M'
       CONSTRAINT VALD-SEX CHECK (VALUE IN('M'.'F'));
       
       
CREATE TABLE EMP (
empid	   int(7),
emp_name   varchar(20),
manager	   int(7),
address    varchar(100),
SEX	   SEX
);       
```


## 3) JOIN

#### "테이블 조인이란 복수의 테이블을 결합하는 것"
### INNER JOIN
* 테이블 데이터 간 교집합을 말함
#### 이렇게 Table A, Table B가 있으면
![img](https://velog.velcdn.com/images/newdana01/post/f698a65c-bc7e-44f0-85f2-268215e9876d/image.png)

#### 상품코드라는 컬럼을 공통으로 가지고 있고 이를 결합 조건으로 하여 아래와 같이 쿼리문을 작성
```sql
SELECT A.상품코드 상품코드, A.상품명 상품명, B.재고수량 재고수량 //조회할 컬럼
	FROM TableA as A       	// 결합할 테이블 명. as 이후는 별칭
    	INNER JOIN TableB as B   // 결합할 테이블 명. as 이후는 별칭
    	ON A.상품코드 = B.상품코드  // 결합 조건
```

#### 이렇게 합쳐지는 것
![img](https://velog.velcdn.com/images/newdana01/post/2b57131d-003f-4287-9f46-11a93a460478/image.png)

* 테이블 조인에 대한 조건은 ON, 데이터 필터링에 대한 조건은 WHERE을 사용한다.

### OUTER JOIN
* 공통 데이터 외에 어느 한 테이블에만 존재하는 데이터도 함께 결합하여 조회하고자 할 때 사용하는 방법을 말함
    * LEFT JOIN(왼쪽 테이블을 기준)
    * RIGHT JOIN(오른쪽 테이블을 기준)
    * FULL JOIN(위 두 결과를 합친 결과)

#### FULL JOIN 예시
```sql
SELECT A.상품코드 상품코드, A.상품명 상품명, B.재고수량 재고수량 
	FROM TableA as A       
    	FULL JOIN TableB as B   
    	ON A.상품코드 = B.상품코드
```

![img](https://velog.velcdn.com/images/newdana01/post/8f3d6b95-dddb-424d-a034-15566f7b74d2/image.png)
* 값이 없는 부분은 null로 채워짐

## 4) 식별, 비식별 관계

#### "외래 키를 사용하여 테이블 간 관계를 정립해 줄 때 사용하는 전략은 크게 식별 관계, 비식별 관계 전략이 있음"

### 식별 관계

#### 부모 테이블의 기본키 또는 유니크 키를 자식 테이블이 자신의 기본키로 사용
![img](https://blog.kakaocdn.net/dn/YioAe/btqFPriMerk/FrSpo08ZHl2KpDTg2ReIxK/img.png)

### 비식별 관계

#### 부모 테이블의 기본키 또는 유니크 키를 자신의 기본키로 사용하지 않고, 외래 키로 사용하는 관계

![img](https://blog.kakaocdn.net/dn/cFZ1cV/btqFOWQQR80/5bf3sjjPznGDUz0kSIpQck/img.png)

## 5) 주제 영역

#### "주제 영역은 기업이 사용하는 데이터의 최상위 집합임"
##### * ex) , 제조 업체의 -> 인사, 생산, 자재, 판매 등

### 주제 영역 명명
* 보편적 업무 용어 사용
* 단수형 명사 사용
* 데이터 그룹을 의미하는 용어 사용

### 주제 영역 목적
* 데이터의 계층적 구조 파악에 용이
* 품질 확보에 기여(분석의 최상위 단위 역할을 함)
* 주제 영역 계층과 업무 기능 계층간의 대응 관계를 확인

### 주제 영역 장점
* 프로젝트 관리 용이
* 모델 개발 조성 용이
* 리포지터리 관리 용이
* 상세 사항의 전개 혹은 축약 가능

### [[목차]](https://gitlab.theuber.co.kr:8989/study/ch.kim/-/blob/main/study/index.md)
