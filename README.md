## **COW L2 백엔드 과정 JAVA 객체지향프로그래밍 과제**

## 📮 미션 제출 방법

- 미션 구현을 완료한 후 GitHub을 통해 제출해야 한다.
    - 해당 리포지토리를 fork/clone 
    - 미션 구현
    - 미션 구현 과정에서 학습한 내용, 고민했던 점 등을 기록한 본인 깃헙 아이디 이름 md파일 작성(ex. KoSeonJe.md)
    - 구현 완료 한 코드는 해당 리포지토리에 pr 작성
      - pr 타이틀: [#주차]객체지향 코드 연습(깃헙 아이디) 
        - ex. [1주차] 객체지향 코드 연습(KoSeonJe)
    - 미션 구현에서 기록한 md파일은 [COW-Spring-3](https://github.com/COW-edu/COW-Spring-3/tree/main/week02) 리포지토리에 pr 작성
    - 미션 구현 pr 링크 첨부 

## **프로젝트 설명**

자바로 객체 지향 프로그래밍을 배운 후 프로젝트에서 필요한 객체들을 설계하고 이를 구현합니다 . 기본 예금 계좌와 적금 계좌을 가진 뱅킹시스템을 구현하고 각 계좌의 성격에 대한 차이를 다형성을 이용하여 구현해 봅니다. 또한 입력값에 따른 계좌생성, 출금, 입금, 송금 기능을 호출하고 자바에서 제공되는 컬렉션 프레임워크들을 활용하여 뱅킹시스템을 관리할 수 있습니다. 이러한 프로젝트를 구현함으로써 실무에서 객체를 설계하는 방법, BigDecimal 데이터 타입을 이용하여 금액을 다루는 법, 객체 지향 프로그래밍의 장점을 활용하는 방법 그리고 여러 필요한 기능들을 구현하는 방법들을 익힐 수 있습니다.

### **프로젝트 과제 상세**

**계좌 클래스 설계와 구현**

1. 계좌(일반 예금 계좌)에는 일반 예금 계좌와 적금 계좌가 있습니다. 계좌 클래스의 속성은 계좌종류(N: 예금계좌, S:적금계좌), 계좌번호, 소유자, 잔액, 활성화 여부 다섯 가지 입니다.
2. 적금 계좌 클래스는 일반 예금 계좌 클래스에서 상속을 받고 목표 금액 속성이 추가 됩니다.
3. 일반 예금 계좌 클래스의 각 속성에 getter/setter를 제공하고, 계좌 정보를 보여주는 getAccountInfo() 메서드를 구현합니다. 적금 계좌 클래스는 이 메서드를 재정의 하여 목표 금액 정보도 보여주도록 합니다.
4. 뱅크 클래스에서 호출할 출금, 입금 기본 메서드를 생성합니다.

**뱅크 클래스 설계와 구현**

1. 계좌 클래스에서 구현한 기본 클래스를 이용하여 계좌생성, 출금, 입금, 송금 메서드를 구현합니다. 메서드 내부적으로 입력값을 받는 액션이 있습니다.
2. 적금 계좌는 적금 계좌는 잔액이 목표 금액(%s원) 이상이어야 출금 가능하도록 상속받은 출금 메서드를 조금 다르게 구현해줍니다.

**인터페이스 설계와 구현**

1. 일반 예금 계좌와 적금 계좌의 이자율 정책은 다릅니다. (여기서의 이자 계산은 잔액의 x%를 추가로 제공해주는 것으로 한정합니다. 현실세계의 포인트 개념과 비슷합니다.) 일반 예금 계좌인 경우 1000만원 이상은 이자율이 50%, 500만원 이상은 7%, 100만원 이상은 4%, 1만원 이상은 2%, 그 외에는 1% 이자를 제공해줍니다. 적금 계좌의 경우 100만원 이상은 이자율이 50%, 그 외에는 1% 이자를 제공해줍니다.
2. 각 할인 정책을 구현하기 위해 InterestCalculator 인터페이스에 계좌 잔액에 대한 이자금액을 반환하는 메서드(BigDecimal getInterest(balance))를 선언하고, 이를 구현한 일반 예금 계좌 이자 계산 정책과 적금 계좌에 대한 이자 계산 정책 클래스를 만듭니다.

**계좌 관리를 위한 컬렉션 프레임 워크 사용하기**

1. 모든 계좌를 관리하기 위한 중앙은행 클래스를 만듭니다. 계좌를 배열에 관리하기 위해 ArrayList를 활용합니다.
2. 계좌별 이자 정책을 관리하기 위해 HashMap을 활용하고, Key에 category, Value에 각 category의 InterestCalculator 인스턴스 를 담습니다.

**예외 처리**

1. 입금할 금액을 적으라고 했는데 한글로 입력할 경우
2. 없는 계좌로 송금, 입금, 출금을 시도할 경우
3. 계좌 생성 시 계좌 형식에 알맞지 않는 경우

→ 이 외에도 생각나는 다양한 예외처리를 해주시기 바랍니다.

**마치며..**

❗**중요**

위의 주어진 요구사항들은 구현하는데 방향성을 준 것이나 다름 없습니다. 위 코드의 요구사항을 그대로 따르지 않으셔도 됩니다. 다만, 위 요구사항과 다르게 작성한 코드가 있거나, 추가적으로 기능을 추가하신 게 있으시다면 md파일에 함께 작성해서 제출해주시면 감사하겠습니다.

(예를 들어 계좌를 관리하기 위해 무조건적으로 ArrayList를 사용할 필요는 없다는 것입니다. 다만, 다른 방법으로 코드를 작성하셨다면 바뀐 부분을 md파일에 필수로 추가해주시길 바랍니다)

위 요구사항들로만 뱅킹 시스템을 구현하기에는 턱없이 부족한 정보일 수 있습니다. 주도적으로 추가해서 하나의 괜찮은 뱅킹 시스템을 만들어주세요.

❗**과제 주의사항**

이 과제는 객체지향적인 코드 작성하는 것을 연습하기 위함입니다.

하지만 객체지향적인 코드를 작성하는 것도 중요하지만, 객체지향적인 코드를 작성하기 위해 과제를 완성시키지 못한다면 의미가 없습니다.

과제의 완성을 1차 목표로 두시고, 완성하신 뒤 저희들의 피드백을 통해 리팩토링 과정을 거쳐나가도 충분합니다.

그래도 이 과제를 하며 객체지향 코드에 대해 많이 고민해보셨으면 하는 바램입니다.

[Reference]
- https://github.com/devwon/BankingSystem
