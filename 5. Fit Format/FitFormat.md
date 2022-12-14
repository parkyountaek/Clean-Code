# 형식 맞추기
어수서한 형식보다는 질서있는 형식이 보기 좋다. 프로그래머라면 형식을 깔끔하게 맞춰 코드를 작성해야한다.

## 형식을 맞추는 목적
코드 형식은 의사소통의 일환이다. 의사소통은 전문 개발자의 일차적인 의무이다. 코드의 가독성으로 인해 코드의 품질이 바뀌게 된다.

## 적절한 행 길이를 유지하라.
500줄을 넘지 않고도 200줄 정도인 파일로도 커다란 시스템을 구축할 수 있다. 일반적으로 큰 파일보다 작은 파일이 이해하기 쉽다.

### 신문 기사처럼 작성하라.
신문 기사를 보면 독자는 위에서 아래로 기사를 읽는다. 요약 내용을 먼저 제시하고 세세한 니용은 후에 나온다. 이를 토대로 소스 파일 첫 부분은 고차원 개념과 알고리즘을 설명한다. 아래로 내려갈수록 의도를 세세하게 묘사하고 마지막에는 가장 저차원 함수와 세부 내용이 나오게 한다.

### 개념은 빈 행으로 분리하라.
패키지 선언부, import 문, 각 함수 사이에 빈 행을 넣어 가독성이 좋게 유지한다.

### 세로 밀집도
줄바꿈이 개념을 분리한다면 세로 밀집도는 연관성을 의미한다. 즉 서로 밀접한 코드 행은 세로로 가까이 놓여야 한다.

### 수직 거리
함수 연관 관계와 동작 방식을 이해하려고 이 함수에서 저 함수로 오가며 소스 파일을 위아래로 뒤지는 행동으로 인해 혼란이 올 수 있다. 이를 방지하게 위해 서로 밀접한 개념은 세로로 가까이 둔다.

> **변수 선언**
>
> 변수는 사용하는 위치에 최대한 가까이 선언한다.

> **인스턴스 변수**
>
> 인스턴스 변수는 클래스 맨 처음에 선언한다.

> **종속 함수**
>
> 한 함수가 다른 함수를 호출한다면 두 함수는 세로로 가까이 배치한다. 또한 가능하다면 호출하는 함수를 호출되는 함수보다 먼저 배치한다.

> **개념적 유사성**
>
> 개념적 친화도가 높을수록 가까이 배치한다.

## 가로 형식 맞추기
프로그래머는 짧은 행을 선호한다. 최대 120자 정도로 행 길이를 제한한다.

### 가로 공백과 밀집도
가로로는 공백을 사용해 밀접한 개념과 느슨한 개념을 표현한다. 수식을 사용하거나 값을 할당하는 부분 등에 공백을 넣어 가독성을 높이자.

### 들여 쓰기
if문이나 짧은 while문 등에 들여쓰기를 무시할 수 있다. 하지만 들여쓰기를 이용하여 범위를 제대로 표현하도록 하자.

## 팀 규칙
괄호를 넣는 위치, 들여쓰기는 몇 자로 할지, 클래스와 변수, 메서드 이름을 어떻게 지을지 등의 팀 규칙을 정한다. 그리고 나서 IDE 코드 형식기를 설정하여 개발을 진행한다.

# 5장 정리 - 생각
책에서 설명하는 대부분은 스스로 점검했을때 잘 지키고 있는 것 같다. 다만 좀 더 주의를 해야할 부분은 함수를 호출하는 곳을 먼저, 호출되는 함수를 아래에 놓는 규칙을 좀 더 봐야함을 느꼈다.

짧은 이름으로 짓기 어려워 긴 이름으로 작성하여 가로 길이를 넘을땐 어떻게 좀 더 가독성을 높일지에 대해 고민하게 된다.