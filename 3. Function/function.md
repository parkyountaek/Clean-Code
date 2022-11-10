# 함수
프로그램 초창기에는 시스템을 루틴과 하위 루틴으로 나눴다. 어떤 프로그램이든 가장 기본적인 단위가 함수다.

<br/>

## 작게 만들어라
함수를 만드는 첫째 규칙은 작게다.

<br/>

## 볼록과 들여쓰기
if 문/else 문/while 문 등에 들어가는 블록은 한 줄이어야 한다. 블록안에서는 함수를 호출하면 코드는 더 명확해지고 깔끔해진다.

<br/>

## 한가지만 해라
**함수는 한 가지를 해야한다. 그 한가지를 잘해야한다. 그 한가지만을 해야한다.** 

지정된 함수 아래 추상화 수준이 하나인 단계만 수행한다면 그 함수는 한 가지 작업만 한다.

>🤔 여기서 "추상화 수준"이라는 단어가 생소했다. 추상화 수준이란 **해당 코드를 읽으면서 파악할 수 있는 정보의 수준**을 의미한다.

<br/>

## 함수당 추상화 수준은 하나로!
함수가 확실히 한 가지 작엄만 하려면 함수 내 모든 문장의 추상화 수준이 동일해야한다.

<br/>

## 위에서 아래로 코드 읽기 : 내려가기 규칙
한 함수 다음에는 푸상화 수준이 한 단계 낮은 함수가 온다. 즉, 위에서 아래로 프로그램을 읽으면 함수 추상화 수준이 한 단계씩 낮아진다.


<br/>

## Switch 문
Switch 문은 작게 만들기 힘들다. 일반적으로 Switch 문은 분기처리를 하기 때문에 SRP에 위반되고 한 가지 작업만 수행하지 않기도 하고 새로운 분기처리를 하기 위해 새로운 조건을 추가해줘야 하므로 OCP에도 위반된다.

책에서는 switch 문을 추상 팩토리<sup>abstract factory</sup>에 숨긴다.


>🤔 **추상 팩토리 패턴**이란 서로 관련이 있는 객체들을 통째로 묶어서 팩토리 클래스로 만들고, 이들 팩토리를 조건에 따라 생성하도록 다시 팩토리를 만들어서 객체를 생성하는 패턴

<br/>

## 서술적인 이름을 사용하라!
함수가 하는 일을 좀 더 잘 표현하는 이름이 좋다. 이름이 길어도 괜찮다. 길고 서술적인 이름이 짧고 어려운 이름보다 좋다.

<br/>

## 함수 인수
매개변수가 3개 이상일 경우는 피하는 것이 좋다. 최선은 입력 인수가 없는 경우이며, 차선은 입력 인수가 1개 뿐인 경우다.

### 많이 쓰는 단항 형식
+ 인수에 질문을 던지는 경우

  ex) `boolean fileExistst("MyFile")`

+ 인수를 뭔가로 변환해 결과를 반환하는 경우
  
  ex) `InputStream fileOpen("MyFile")`

+ 이벤트 함수

  이벤트라는 사실이 코드에 명확히 드러나야한다.

  ex) `passwordAttemptFailedNtimes(int attempts")`

그 외의 경우에는 단항 함수는 가급적 피하도록 한다. 입력 인수를 변환하는 함수라면 결과는 변환값으로 돌려준다.

### 플래그 인수
함수로 부울 값을 인자로 넘기는 경우는 추하다고 한다. 함수가 참, 거짓에 따라 한가지 역할을 하는 것이 아닌 여러가지 역할을 진행하기 때문이다.

### 이항 함수
인수가 2개인 함수는 인수가 1개인 함수보다 이해하기 어렵다. `assertEqauls(expected, acutal)`에 문제가 있다고 한다. 어떤 순서로 기대하는 값과 실제값을 넣어줘야하는지에 대해 알고 있어야 하기 때문이다.

>🤔 단항 함수에 비해서 인자값의 순서를 알아야하는데 있어서 과연 더 이해하기가 힘들까? IDE가 잘 되어있기때문에 각각의 매개인자에 어떤 값들이 들어가야하는지 설명이 잘 되어있는데 말이다..

### 삼항 함수
인수가 3개인 함수는 인수가 2개인 함수보다 훨씬 더 이해하기 힘들다. 순서, 주춤, 무시로 야기되는 문제가 두 배이상 늘어난다. 

`assertEquals(message, expected, actual)`함수에서 첫번째 인자가 expected로 예상했지만 멈칫하고 주춤하게 된다.

### 인수 객체
인수가 2~3개 필요하다면 일부는 독자적인 클래스 변수로 선언할 가능성을 짚어본다면 이는 눈속임이라 보일지라도 그렇지 않다.
독자적인 클래스 변수로 선언하면서 그에 대한 내용이 들어간다면 말이다.

```java
Circle makeCircle(double x, dobule y, double radius);
Circle makeCircle(Point center, double radius);
```

### 동사와 키워드
함수의 의도나 인수의 순서와 의도를 제대로 표현하려면 좋은 함수 이름이 필수다.

+ 단항 함수는 함수와 인수가 동사/명사 쌍을 이뤄야 한다.

  ```java
  wirte(name);
  writeField(name);
  ```

  `write(name)`보다 `writeField(name)`이 더 명확하다.

+ 함수 이름에 키워드를 추가한다.

  ```java
  assertEquals()
  assertExpectedEqualsActual()
  ```
  `assertEqauls()` 보다 `assertExpectedEqualsActual()`이 인수 순서를 기억하기 쉬워 조금 더 좋은 함수명이다.

<br/>

## 부수 효과를 일으키지 마라
함수에서 한 가지를 하겠다고 약속하고 다른 것도 하는 경우를 방지해야한다. 이는 **시간적인 결합**이나 **순서 종속성**을 
초래한다. 
```java
public class UserValidator {
  private Cryptographer cryptographer;

  public boolean checkPassword(String userName, String password) {
    User user = UserGateway.findByName(userName);
    if(user != User.NULL) {
      String codedPhrase = user.getPhraseEncodedByPassword();
      String phrase = cryptographer.decrypt(codedPhrase, password);
      if("Valid Password".equals(phrase)) {
        Session.initialize();
        return true;
      }
    }
    return false;
  }
}
```

여기서 함수가일으키는 부수 효과는 `Session.initialize()` 호출이다. `checkPassword()`는 이름만 봐서는 세션을 초기화한다는 사실이 드러나지 않는다. 그래서 함수 이름만 보고 호출하는 경우 세션이 초기화될 위험이 있다.

함수가 한 가지만 한다는 규칙을 위반하지만 checkPasswordAndIntializeSession 이라는 함수명이 훨씬 좋다.

### 출력 인수
일반적으로 인수를 **함수 입력**이라고 해석한다.
