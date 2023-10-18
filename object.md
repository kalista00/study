# 3. Object

* 자바 클래스 선언시 extends 로 다른 클래스를 상속하지 않으면 암시적으로 java.lang.Object 를 상속하게 됨. (자바의 최상위 부모 클래스)

## 1) toString()

#### "객체의 문자 정보를 리턴하는 매소드"
* 기본적으로 "클래스명@16진수해시코드" 로 구성된 문자 정보를 리턴
* 오버라이딩하여 유익한 정보들을 리턴하도록 되어있음
  * ex) java.util 패키지의 Date 클래스는 toString() 매소드를 오버라이딩함 (날짜와 시간 정보 리턴)

#### String 클래스는 toString() 매소드를 오버라이딩 하여 저장하고 있는 문자열 리턴

```java
  Object object = new Object();
  Date date = new Date();
  System.out.println(object.toString()); // 출력 결과 ex) java.lang.Object@1b15692
  System.out.println(date.toString()); // 출력 결과 ex) Wed Oct 18 15:00:00 KST 2023
```

#### 직접 오버라이딩

```java
public class SmartPhone {
    private String company;
    private String os;

    public SmartPhone(String company, String os) {   // 생성자
        this.company = company;
        this.os = os;
    }

    @Override
    public String toString() {  // toString 오버라이딩
        return company + ", " + os;
    }
}
```

## 2) hashCode()

#### "객체 해시코드: 객체를 식별할 하나의 정수값"
* hashCode() 매소드는 객체의 메모리 번지를 이용 -> 해시코드 만들어서 
* 논리적 동등(내용물이 같은 지) 비교 시 오버라이딩

### hashCode() 오버라이딩
* 오버라이딩 하는 이유
  * 객체 동등성 비교 : 두 객체가 논리적 내용을 가지지만 서로 다른 객체로 취급되어서 원하지 않는 동작을 일으키는 것을 방지
  * 해시 기반 컬렉션(HashMap, HashSet...)의 성능 향상 : 데이터를 빠르게 검색하고 저장할 수 있도록 오버라이딩 하여 성능 향상
  * 커스텀 해시 코드 : 객체의 내용에 따라 고유한 해시 코드를 생성
  * 클래스 계층 구조와 상속 : 클래스 계층 구조에서 서브클래스와 슈퍼클래스 간의 일관성을 유지
  
#### 오버라이딩 하는 방법
```java
  // 키 = Key 객체 , 값 = String 을 저장하는 HashMap 객체 생성
  HashMap<Key, String> hashMap = new HashMap<Key, String>();
  hashMap.put(new Key(1), "김창희");
  String value = hashmap.get(new Key(1)); //value 변수에 null 값이 들어감 (새로 생성한 new Key(1) 의 해시코드가 서로 다르기 때문)
```
```java
  public class Key{
    public int number;
    public Key(int number){
      this.number = number;
    }

    @Override 
    public int hashCode(){ //이렇게 hashCode()를 오버라이딩 해주면 
      return number;  // number 변수의 값을 return 해주기 때문에 위의 value 에 null 값이 들어가지 않고 "김창희"가 들어감
    } // 클래스 변수의 고유 hashCode()로 재정의 해줘도 됨 ex) id.hashCode()
  }
```
#### Object 의 equals() 매소드만 재정의 하지 말고 hashCode() 매소드도 재정의 해서 논리적 동등 객체일 경우 해시코드도 동일하게 리턴되도록 해야 함

### 해시 알고리즘
#### "임의의 길이를 가진 데이터를 고정된 길이의 해시 값으로 변환하는 알고리즘"
* 다음과 같은 목적으로 사용
  * 데이터 무결성 검사
  * 데이터 식별
  * 암호화
  * 암호 인증
  * 자료구조

## 3) equals()
* 논리적으로 동등하다 : 내용물이 같다(저장하고 있는 데이터)

#### ex) 내용물이 같은 서로 다른 객체 obj1, obj2 가 있다면 아래의 값이 나옴
```java
obj1 == obj2 // false
obj1.equals(obj2) // true
```
#### String 클래스가 Object의 equals() 매소드를 재정의(오버라이딩) 해서 문자열 비교로 변경했기 때문

### equals() 매소드 재정의
* 재정의 하려면 먼저 동일한 타입의 객체인지 확인 해야 함
```java
  @Override
  public boolean equals(Object obj){
    if(obj instanceof Member){ //매개값 obj가 Member 타입인지 확인
      Member member = (Member) obj; //Member 타입으로 강제 타입 변환
      if(id.equals(member.id)){ // id 필드 값이 동일한지 검사, 동일하다면 true 리턴
        return true;
      }
    }
    return false; // 매개값 obj가 Member 타입이 아니거나 id 필드값이 다른 경우 false
  }
```

## 4) clone()

#### "자신을 복제하여 새로운 인스턴스를 생성"
* clone() 매서드를 오버라이딩 하려면 Cloneable 을 implements해야 함
* implements 하지 않으면 예외 발생

#### 오버라이딩 예시
```java
class Point implements Cloneable {
    int x, y;
    
    Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
    
    @Override
    public String toString() {
        return "x : " + x + ", y : " + y;
    }
    
    @Override
    public Object clone() {
        Object obj = null;
        try {
            obj = super.clone();// clone()은 반드시 예외처리를 해주어야 함
        } catch (CloneNotSupportedException e) {}
        return obj;
    }
}

public class CloneTest {
    public static void main(String[] args) {
        Point original = new Point(3, 5);
        Point copy = (Point)original.clone();
        System.out.println(original);
        System.out.println(copy);
    }
}
```
### [[목차]](https://gitlab.theuber.co.kr:8989/study/ch.kim/-/blob/main/study/index.md)