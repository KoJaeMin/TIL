# Iterator

- 자바스크립트에서 `반복자(Iterator)`는 시퀀스를 정의하고 종료시의 반환값을 잠재적으로 정의하는 객체입니다.
- 반복자는 `두 개의 속성(value, done)`을 반환하는 `next()` 메소드 사용하여 객체의 `Iterator protocol`을 구현합니다. 시퀀스의 마지막 값이 이미 산출되었다면 done 값은 true 가 됩니다. 만약 value값이 done 과 함께 존재한다면, 그것은 반복자의 반환값이 됩니다.
- 자바스크립트에서 가장 일반적인 반복자는 배열 반복자입니다. 배열은 완전히 할당되어야 하지만 `Iterator`는 무제한 시퀀스로 표현할 수 있습니다.

## Generator functions
- `Iterator`을 생성할 때는 주의해서 프로그래밍을 해야 하는데, `Iterator` 내부에 명시적으로 상태를 유지할 필요가 있기 때문입니다. `생성자(Generator)` 함수는 이에 대한 강력한 대안을 제공합니다: 실행이 연속적이지 않은 하나의 함수를 작성함으로서 개발자가 `iterative algorithm`을 정의할 수 있게 해줍니다. 생성자 함수는 `function*` 문법을 사용하여 작성됩니다.
- 생성자 함수가 최초로 호출될 때, 함수 내부의 어떠한 코드도 실행되지 않고, 대신 생성자라고 불리는 반복자 타입을 반환합니다. 생성자의 `next` 메소드를 호출함으로서 어떤 값이 소비되면, 생성자 함수는 `yield` 키워드를 만날 때까지 실행됩니다.

### function*
- function 뒤에 asterisk(\*)가 붙어 Generator function이 정의됩니다. 이때 Generator object를 반환합니다.
- Generator object는 **value**와 **done**이라는 프로퍼티를 갖는다.
### yield
- yield 키워드는 Generator function을 중지하거나 재개하는데 사용됩니다.
- Generator function은 `yield` 키워드 전까지 작업을 수행하다가 `next()`가 호출되면 `yield` 뒤에 나오는 표현식을 반환하며 다시 작업을 수행한다. 이 때, `next()`안에 값을 넣어주면 `yield` 표현식 뒤에 있는 변수에 값을 넣을 수 있다.

```javascript
function* generator(start = 0, end = Infinity, step = 1){
    let n = 0;
    for(let i = start; i < end; i++)
        n += yield n;
}

let gen = generator(0,5,1);
console.log(gen.next(10))// { value: 0, done: false }
console.log(gen.next(20))// { value: 20, done: false }
console.log(gen.next(4))// { value: 24, done: false }
console.log(gen.next(12))// { value: 36, done: false }
console.log(gen.next(421))// { value: 457, done: false }
console.log(gen.next())// { value: undefined, done: true }
```
![Generator function 작동방식](../../image/Generator%20function%20%EC%9E%91%EB%8F%99%EC%9B%90%EB%A6%AC.png)