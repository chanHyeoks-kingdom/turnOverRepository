## 1. 연구 주제
- java 예외처리

## 2. 잘 이해가 안가던 것들
- 예외처리 종류
- 예외처리 잘, 올바르게 사용하는 방법


## 3. 꼭 의견 교류나 피드백 받고 싶은 부분

> #### 1. java의 예외처리 
- 프로그램이 오류로 인하여 `비정상적인 종료되지 않도록 예방`하기 위하여 예외처리를 함
- 프로그램의 갑작스런 종료를 막고 `정상적인 실행상태를 유지`할 수 있도록 함.

<br>

> #### 2. Error의 종류
1. 컴파일 에러 : 컴파일시에 발생하는 에러 {ex : 문법 구문 오류(syntax error)}
2. 런타임 에러 : 실행시에 발생하는 에러
3. 논리적 에러 : 실행은 되지만 의도와 다르게 동작

<br>

> #### 3. Exceptions - Runtime Exception - Other Exception
                 
- Exception 클래스
  - 모든 Exception들의 부모 클래스

![image](https://github.com/chanHyeoks-kingdom/turnOverRepository/assets/68278903/afb0fe78-7e86-434e-87ee-e8a4b797cbaf)



- RuntimeException 클래스
  - 프로그래머의 실수로 발생하는 예외 (Unchecked Exception)
  - 명시적인 처리를 하지 않아도 `실행은 됨 하지만 처리하지 않을시 문제가 발생할 수 있음`
  - 런타임 단계에서 확인 가능


  - ex.
    - IndexOutOfBoundException 배열범위 벗어남
    - NullPointerException 값이 null인 멤버 호출
    - ClassCastException 클래스 간의 형 변환 잘못됨
    - ArithmenticException  정수를 0으로 나누는 산술오류

- ~~Exeption 및 하위 클래스~~ Other Exception (RuntimeException 외에 Exception을 상속받는 나머지: checkedException)
  - ~~사용자의 실수와 같은 외적인 요인에 의해 발생하고~~ 컴파일 시 체크되는 `checked Exception`이다.
  - 반드시 예외를 처리해야함
  - 컴파일 단계에서 확인함

`ex. FileNotFoundException, ClassNotFoundExcption, DataFormatException`


<br>

> #### 4. java 예외처리 방식 
- *try - catch문*
  - **try** 블록 안에 예외가 발생할 가능성이 있는 코드를 작성한다.
```
try{
    // 문제 발생할 만한 코드 작성
} catch (해당 코드에서 발생할 익셉션 클래스) {
    // 문제 상황 핸들링
} fianlly {
    // 문제가 터지든 안터지든 무조건 해야 하는 것. (ex. 자원 해제, 로깅 등..)
}
```

  - **catch**
    - try블록에서 예외가 발생할 경우 실행되는 코드 블록, 모든 예외에 대하여 처리하고 싶을 경우 Exception,
    - 특정 예외에 대해 처리하고 싶을 경우 해당 exception을 작성하면 됨.
    - catch 블록이 여러 개일 경우 해당하는 catch문만 실행됨
    - 하위 예외 클래스를 먼저 배치함 (순차적으로 진행되기 때문에 상위객체가 위에 있을 경우 하위 클래스 예외처리는 실행되지 않음)
  
  - **finally**
    - 예외 발생 여부와 상관없이 반드시 실행됨.
    - 파일 클래스, socket을 종료하기 위해 주로 사용됨

<br>

> #### 5. 예외 전가
- 호출한 곳으로 예외를 떠넘기는 것
- 매서드 선언부 끝에 throws 키워드를 작성
```
void testMethod() `throws` NullpointerException, ArrayIndexOutOfBoundException{
  ...
}
```
- NullpointerException, ArrayIndexOutOfBoundException 가 발생했을 경우 testMethod를 호출한 곳으로 예외처리를 떠넘김
