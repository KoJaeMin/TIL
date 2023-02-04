# Data Type(데이터 타입)

![JS메모리 할당](/image/JSMemoryAllocation.png)

- JavaScript는 느슨한 타입(loosely typed)의 동적(dynamic) 언어이다. JavaScript의 변수는 어떤 특정 타입과 연결되지 않으며, 모든 타입의 값으로 할당 (및 재할당) 가능하다.
```javascript
let foo = 42 // foo가 숫자
foo = 'bar' // foo가 이제 문자열
foo = true // foo가 이제 불리언
```
- JavaScript에서 데이터 타입을 크게 원시 타입(primitive data type), 객체 타입(object/reference type)으로 나누어진다.

## 원시 타입(primitive data type)

객체를 제외한 모든 타입은 변경 **불가능한 값(immutable value)** 이며 **call-by-value(값에 의한 전달)** 이다.

- Boolean
- Null
- Undefined
- Number
    - **배정밀도 64비트 부동소수점 형(double-precision 64-bit floating-point format : -(253 -1) 와 253 -1 사이의 숫자값)** 을 따른다. 즉, 모든 수를 실수를 처리하며 정수만을 표현하기 위한 특별한 데이터 타입(integer type)은 없다.
    - 2진수, 8진수, 16진수 리터럴은 메모리에 동일한 배정밀도 64비트 부동소수점 형식의 2진수로 저장된다. 자바스크립트는 2진수, 8진수, 16진수 데이터 타입을 제공하지 않기 때문에 이들 값을 참조하면 모두 10진수로 해석된다.
- String
    - JavaScript는 정적타입(강타입) 언어들과는 다르게 String이 생성되고 변수가 그 String의 메모리 주소를 가르킨다. 이로 인해 새로운 String 값을 재할당하면 변수는 새로운 String의 메모리 주소를 가리키게 변경된다.
    - String은 배열처럼 인덱스를 통하여 접근가능하지만 **read only**이며 문자의 일부를 변경할 수 없다.
- Symbol (ES6에 추가됨)
- BigInt (ES11에 추가됨)
    - Number와 혼용해서 연산할 수 없다.

## 객체 타입(object/reference type)

객체는 데이터와 그 데이터에 관련한 동작(절차, 방법, 기능)을 모두 포함할 수 있는 개념적 존재이다. 달리 말해, 이름과 값을 가지는 데이터를 의미하는 **프로퍼티(property)** 와 동작을 의미하는 **메소드(method)** 를 포함할 수 있는 독립적 주체이다.

자바스크립트는 객체(object) 기반의 스크립트 언어로서 자바스크립트를 이루고 있는 거의 “모든 것”이 객체이다. 원시 타입(Primitives)을 제외한 나머지 값들(배열, 함수, 정규표현식 등)은 모두 객체이다. 또한 객체는 **call-by-reference(참조에 의한 전달)** 방식으로 전달된다.

- Object
    - JavaScript의 객체는 **키(key)** 과 **값(value)** 으로 구성된 **프로퍼티(Property)** 들의 집합이다.
    - 자바스크립트의 객체는 객체지향의 상속을 구현하기 위해 **프로토타입(prototype)** 이라고 불리는 객체의 프로퍼티와 메소드를 상속받을 수 있다. 이 프로토타입은 타 언어와 구별되는 중요한 개념이다.
    - 객체 생성 방법
        - 객체 리터럴
            가장 일반적인 자바스크립트의 객체 생성 방식으로 중괄호({})를 사용하여 객체를 생성하는데 {} 내에 1개 이상의 프로퍼티를 기술하면 해당 프로퍼티가 추가된 객체를 생성할 수 있다. {} 내에 아무것도 기술하지 않으면 빈 객체가 생성된다.
            ```javascript
            let emptyObject = {};
            let persion = {
                name: 'Gildong'
            }
            ```
        - Object 생성자 함수
            new 연산자와 Object 생성자 함수를 호출하여 빈 객체를 생성할 수 있다. 빈 객체 생성 이후 프로퍼티 또는 메소드를 추가하여 객체를 완성하는 방법이다.
            ```javascript
            // 빈 객체의 생성
            var person = new Object();
            // 프로퍼티 추가
            person.name = 'Lee';
            ```
        - 생성자 함수
        es6이전 버전은 Class가 없기에 생성자 함수를 사용한다. es6 버전부터는 Class라는 것을 이용한다. (여기서 Class는 사실 함수이다.)
        ```javascript
        // 생성자 함수
        function Person(name, gender) {
            this.name = name;
            this.gender = gender;
            this.sayHello = function(){
                console.log('Hi! My name is ' + this.name);
          };
        }
        // 인스턴스의 생성
        var person1 = new Person('Lee', 'male');
        ```


### Reference
- [데이터 타입과 변수](https://poiemaweb.com/js-data-type-variable)
- [객체](https://poiemaweb.com/js-object)
- [프로토타입의 이해](https://www.nextree.co.kr/p7323/)