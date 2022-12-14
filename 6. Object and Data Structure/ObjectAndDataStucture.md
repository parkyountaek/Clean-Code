# 객체와 자료 구조
변수를 private로 정의하는 이유가 있다. 이는 남들이 변수에 의존하지 않게 만들고 싶어서다. 그렇다면 왜 getter와 setter를 당연하게 public 메서드로 구현해 private 변수를 외부에 노출할까?

>🤔 **객체지향적 프로그래밍**을 하다보면 **캡슐화**와 **정보은닉**이라는 단어를 듣고 함부로 변경이나 정보를 노출시키지 않도록 한다. 첫 부분을 보면서 당연하게 생각하고 있던 부분에 대해서 이유를 답하기 쉽지 않았다. 왜 그런지에 대해 이번 장을 읽고 정리를 해야겠다.

## 자료 추상화