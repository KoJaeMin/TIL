# 타입 선언/ 타입 추론 / 타입 단언
- TypeScript에서 변수에는 항상 타입이 설정해야 하며 여러 가지 방법이 있다.

## 타입 선언(Declaration)
- TypeScript에서 기본적으로 변수명 뒤에 타입을 명시하는 것으로 타입을 선언할 수 있다.
- 타입은 소문자, 대문자를 구별하므로 주의가 필요하다. TypeScript가 “기본 제공하는 타입”은 모두 소문자이다.
```typescript
let num : number = 100;
```

## 타입 추론(Inference)
- 개발자가 굳이 변수 선언할때 타입을 쓰지않아도 컴파일이 스스로 판단해서 타입을 넣어주는 것을 말한다.

```typescript
let num = 100; /// num의 타입이 number라는 추론이 일어남 
```

## 타입 단언(Assertions)
- 타입스크립트의 컴파일러가 타입 추론을 통해 판단한 것보다 개발자가 해당 변수의 타입을 더 잘 알고 있을 때, 변수에 원하는 타입을 강제로 부여하여 더 이상 추론하지 않도록 직접 지시하는 것이다.
- 강제 형변환은 실제로 데이터 자료를 변환시키지만, 타입 단언은 그냥 타입만 이것이라고 컴파일러에게 주장할 뿐이라 실제 데이터가 바뀌거나 그러지 않는다.
- 타입 단언을 하는 방법은 크게 2가지가 있다.
    - **앵글 브라켓(angle-bracket, <>)** 문법을 사용
    ```typescript
    let a : any = 'hello';
    let a_length : number = (<string>a).length;
    ```
    - **as** 문법을 사용
    ```typescript
    let a; /// a는 any라는 타입 추론이 일어남
    a = 1000;
    a = 'dasd';
    let b = a as string;/// b가 string이라는 것을 단언해 줌
    ```
