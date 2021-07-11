## 02. 의미 있는 이름
### 들어가면서
- 소프트웨어에서의 이름은 정말 중요하다.
- 변수, 함수, 클래스, 인수 등등 모든 곳에 이름이 쓰이기 때문이다.
- 이 장에서는 이름을 잘 짓는 규칙을 설명한다.
---

### 의도를 분명히 밝혀라
- 의도가 분명한 이름이 정말로 중요하다.
- 변수나 함수 그리고 클래스 이름을 보고 다음과 같은 굵직한 질문에 답할 수 있어야 한다.
> 1. 변수(혹은 함수나 클래스)의 존재 이유는?
> 2. 수행 기능은?
> 3. 사용 방법은?

- 만약 따로 주석이 필요하다면 의도를 분명히 드러내지 못한 것

- **나쁜 예시**
  - 코드가 하는 일을 짐작하기 어렵다. 이유는❓ 코드의 함축성 때문
  - 코드 맥락이 코드 자체에 명시적으로 드러나지 않는다.   
```java
public List<int[]> getThem() {
  List<int[]> list1 = new ArrayList<int[]>();
  for(int[] x : theList)
    if(x[0] == 4)
      list1.add(x);
  return list1;
```
  - 위의 코드 샘플에는 다음과 같은 정보가 드러나지 않고 있다.   
  > 1. `theList`에 무엇이 들었는가?   
  > 2. `theList`에서 0번째 값이 어째서 중요한가?   
  > 3. 값 `4`는 무슨 의미인가?   
  > 4. 함수가 반환하는 리스트 `list1`을 어떻게 사용하는가?

- **좋은 예시**

  - 코드의 단순성은 변하지 않았지만 코드가 훨씬 명확해졌다.
  - 단순히 이름만 고쳤는데도 함수가 하는 일을 이해하기 쉬워졌다.
```java
public List<int[]> getFlaggedCells() {
    List<int[]> flaggedCells = new ArrayList<int[]>();
    for (int[] cell : gameBoard) {
        if (cell[STATUS_VALUE] == FLAGGED) {
            flaggedCells.add(cell);
        }
    }
    return flaggedCells;
}
```
---

### 그릇된 정보는 피하라
- 프로그래머는 코드에 그릇된 단서를 남겨서는 안 된다.
- 그릇된 단서는 코드의 의미를 흐린다.
  - 예를 들어 직각삼각형의 빗변을 구현할 때 `hp`를 변수 이름으로 사용한다면 중의적인 의미를 띄우므로 좋지 않은 변수 이름이다.
- 특수한 의미를 가지는 단어(ex.`List`)는 이름에 붙이지 말자.
- 서로 흡사한 이름을 사용하지 않도록 주의한다. (개념 차이가 명백해야 함)
- 일관성이 떨어지는 표기법은 그릇된 정보이다. (ex. `DeviceManager`와 `ProtocolController`를 같이 쓰는 경우)
- 예시
```java
int a = l;  // l은 숫자 1처럼 보이고
if (O == l) // O는 숫자 0처럼 보인다.
a = O1;
else
l = 01;
```
---

### 의미 있게 구분하라
- 연속된 숫자를 덧붙이거나 불용어(noise word)를 추가하지 말자.
- 이름이 달라야 한다면 의미도 달라져야 한다.
- 예를 들어 `Product`라는 클래스가 있다고 가정하면 `ProductInfo` 혹은 `ProductData`는 잘못된 것이다.
  - Info, Data는 a, an the와 같은 의미가 불분명한 불용어이다.
  - 하지만 의미가 분명히 다르면 a, an, the를 사용해도 무방하다.
- 구분이 안되는 변수 예시들

  - `Name` VS `NameString`
  - `money` VS `moneyAccount`
  - `customer` VS `customerInfo`
---

### 발음하기 쉬운 이름을 사용하라
```java
// 나쁜 예
class DtaRcrd102 {
    private Date genymdhms;
    private Date modymdhms;
    private final String pszqint = "102";
    /* ... */
};
```
```java
// 좋은 예
// 훨씬 알아보기 쉽고 지적인 대화가 가능해진다.
class Customer {
    private Date generationTimestamp;
    private Date modificationTimestamp;
    private final String recordId = "102";
    /* ... */
};
```
---

### 검색하기 쉬운 이름을 사용하라
- 이름 길이는 범위 크기에 비례해야 한다.

  - 간단한 메서드에서 로컬 변수만 한 문자를 사용한다.
  - 변수나 상수를 코드 여러 곳에서 사용한다면 검색하기 쉬운 이름이 바람직하다.
---

### 인코딩을 피하라
- 헝가리식 표기법
  - 변수 이름에 타입을 인코딩하지 말자 (ex. `phoneString`)
- 멤버 변수 접두어
  - 멤버 변수 앞에 접두어를 붙이지 말자 (ex. `m_dsc`)
- 인터페이스 클래스와 구현 클래스
  - 인터페이스 클래스와 구현 클래스 이름 중 하나를 인코딩해야 한다면 구현 클래스 이름을 인코딩 하자
---

### 자신의 기억력을 자랑하지 마라
- 변수 이름을 자신이 아는 이름으로 변환하지 말자
- 루프에서 반복 횟수를 세는 변수 `i`, `j`, `k`는 전통적으로 한 글자를 사용하기 때문에 괜찮지만 다른 것들은 ❌
---

### 클래스 이름
- 클래스 이름과 객체 이름은 **명사나 명사구**가 적합하다 (ex. `Account`, `Customer`)
- `Manager`, `Processor`, `Data`, `Info` 등과 같은 단어는 피하고, 동사는 사용하지 ❌
---

### 메서드 이름
- 메서드 이름은 **동사나 동사구**가 적합하다 (ex. `deletePage`, `save`)
- 접근자, 변경자, 조건자는 javabean 표준에 따라 값 앞에 `get`, `set`, `is`를 붙인다.
```java
string name = employee.getName();
customer.setName("mike");
if(paycheck.isPosted())...
```
---

### 기발한 이름은 피하라
- 이름이 너무 기발하거나 구어체, 속어, 농담을 섞은 이름은 쓰지 말자
- 의도를 분명하고 솔직하게 표현하라
---

### 한 개념에 한 단어를 사용하라
- 추상적인 개념 하나에 단어 하나를 선택해 이를 고수한다
  - ex) 똑같은 메서드를 클래스마다 `fetch`, `retrieve`, `get`등으로 제각각 부르는 경우
  - 일관성 있는 어휘를 쓰자
---

### 말장난을 하지 마라
- 한 단어를 두 가지 목적으로 사용하지 마라
  - ex) 지금까지 `add` 메서드는 모두 기존 값 두개를 더하거나 이어서 새로운 값을 만든다고 가정하자
  - 새로 작성하는 메서드는 집합에 값 하나를 추가한다   
    👉 메서드를 `add`라고 할 수 없다 (다른 목적)  
    👉 `append` or `insert`로 대체 가능
---

### 해법 영역에서 가져온 이름을 사용하라
- 코드를 읽는 사람도 프로그래머라는 사실을 명심하자
- 그러므로 전산 용어, 알고리즘 이름, 패턴 이름, 수학 용어 등을 사용해도 OK
---

### 문제 영역에서 가져온 이름을 사용하라
- 적절한 '프로그래머 용어'가 없다면 문제 영역에서 이름을 가져오자
- 문제 영역 개념과 관련이 깊은 코드라면 문제 영역에서 이름을 가져오자 
---

### 의미 있는 맥락을 추가하라
- 의미를 클래스, 함수, 이름 공간에 넣어 맥락을 부여한다
- 모든 방법이 실패하면 마지막 수단으로 접두어를 붙인다
```java
// 나쁜 예
// 그냥 메서드만 훑어서는 세 변수 (number, verb, pluralModifier)의 의미가 불분명하다.
private void printGuessStatistics(char candidate, int count) {
    String number;
    String verb;
    String pluralModifier;
    if (count == 0) {  
        number = "no";  
        verb = "are";  
        pluralModifier = "s";  
    }  else if (count == 1) {
        number = "1";  
        verb = "is";  
        pluralModifier = "";  
    }  else {
        number = Integer.toString(count);  
        verb = "are";  
        pluralModifier = "s";  
    }
    String guessMessage = String.format("There %s %s %s%s", verb, number, candidate, pluralModifier );

    print(guessMessage);
}
```
```java
// 좋은 예
// GuessStatisticsMessage라는 클래스 안에 세 변수를 넣었다. => 세 변수의 맥락이 분명해진다.
public class GuessStatisticsMessage {
    private String number;
    private String verb;
    private String pluralModifier;

    public String make(char candidate, int count) {
        createPluralDependentMessageParts(count);
        return String.format("There %s %s %s%s", verb, number, candidate, pluralModifier );
    }

    private void createPluralDependentMessageParts(int count) {
        if (count == 0) {
            thereAreNoLetters();
        } else if (count == 1) {
            thereIsOneLetter();
        } else {
            thereAreManyLetters(count);
        }
    }

    private void thereAreManyLetters(int count) {
        number = Integer.toString(count);
        verb = "are";
        pluralModifier = "s";
    }

    private void thereIsOneLetter() {
        number = "1";
        verb = "is";
        pluralModifier = "";
    }

    private void thereAreNoLetters() {
        number = "no";
        verb = "are";
        pluralModifier = "s";
    }
}
```
---

### 불필요한 맥락을 없애라
- 일반적으로 짧은 이름이 긴 이름보다 좋다. (**단, 의미가 분명한 경우에 한해서**)
- 이름에 불필요한 맥락을 추가하지 않도록 주의하자 (의미가 좀 더 분명해지도록!!)
- ex) 클래스 인스턴스 이름 : `accountAddress` / 클래스 이름 : `Address`
---

### 마치면서
- 좋은 이름을 선택하는 능력을 터득하기 어렵다
- 그렇기에 다른 개발자들의 반대 때문에 두려워하지 말고 서로를 존중하며 좋은 이름으로 바꿔보자
- 좋은 이름을 사용하다보면 읽히는 코드를 짜는 데만 집중할 수 있다
---

### 느낀점
- 지금까지 코드를 짜면서 속도에만 신경썼던 나에게 정말 많은 것을 깨닫게 해주었다.
- 지금부터라도 이름을 선택하는 것에 대해 신중해져야겠다고 생각하게 되었다.
