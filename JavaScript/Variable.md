# Variable(변수)
- 변수(Variable)는 프로그램에서 사용되는 데이터를 일정 기간 동안 기억하여 필요한 때에 다시 사용하기 위해 데이터에 고유의 이름인 식별자(identifier)를 명시한 것이다.
- 변수에 명시한 고유한 식별자를 변수명이라 하고 변수로 참조할 수 있는 데이터를 변수값이라 한다.
- 변수는 `var`, `let`, `const` 키워드를 사용하여 **선언**하고 할당 연산자를 사용해 값을 **할당**한다. 그리고 식별자인 변수명을 사용해 변수에 저장된 값을 참조한다.
- 자바스크립트의 변수는 **블록 레벨 스코프(block-level scope)** 를 가지지 않고 **함수 레벨 스코프(function-level scope)** 를 갖는다. 단, ECMAScript 6에서 도입된 `let`, `const` 키워드를 사용하면 블록 레벨 스코프를 사용할 수 있다. 

```javascript
var score;  // 변수의 선언
score = 80; // 값의 할당
score = 90; // 값의 재할당
score;      // 변수의 참조

// 변수의 선언과 할당
var average = (50 + 100) / 2;
```

## 동적 타이핑
- 자바스크립트는 동적 타입(dynamic/weak type) 언어이다. 이것은 변수의 타입 지정(Type annotation)없이 값이 할당되는 과정에서 값의 타입에 의해 자동으로 타입이 결정(Type Inference)될 것이라는 뜻이다. 따라서 같은 변수에 여러 타입의 값을 할당할 수 있다. 이를 동적 타이핑(Dynamic Typing)이라 한다.

```javascript
var foo;

console.log(typeof foo);  // undefined

foo = null;
console.log(typeof foo);  // object

foo = {};
console.log(typeof foo);  // object

foo = 3;
console.log(typeof foo);  // number

foo = 3.14;
console.log(typeof foo);  // number

foo = 'Hi';
console.log(typeof foo);  // string

foo = true;
console.log(typeof foo);  // boolean
```

## 호이스팅
- 호이스팅이란 `var` 선언문이나 `function` 선언문 등 모든 선언문이 해당 **Scope**의 선두로 옮겨진 것처럼 동작하는 특성을 말한다.
- 자바스크립트는 모든 선언문(`var`, `let`, `const`, `function`, `function*`, `class`)이 선언되기 이전에 참조 가능하다.
```javascript
/// 스코프 처음에 foo가 호이스팅이 되어 foo라는 변수가 선언되며 undefined로 초기화 된다.
/// var foo;
console.log(foo); // ① undefined
/// 실질적으로 변수가 할당이 되는 부분이다.
var foo = 123;
console.log(foo); // ② 123
/// var 선언은 함수레벨 스코프로 전역변수이다. 이에 
{
  var foo = 456;
}
console.log(foo); // ③ 456
```