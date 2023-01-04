# Bitwise Operator

- JavaScript에서 **bitwise operator**을 사용할 셩우 피연산자는 32비트 정수로 변환된다.
- 32비트 이상인 숫자는 최상위 비트가 삭제된다.

```javascript
Before: 11100110111110100000000000000110000000000001;
After: 10100000000000000110000000000001;
```

Unsigned Right shift(>>>)는 있지만 Unsigned Left shift는 없다.
다른 언어들도 Unsigned Left shift는 없다.
어차피 0으로 수렴되기 때문에 Left Shift와 차이가 없기 때문이다.([참고](https://stackoverflow.com/questions/26151644/why-is-there-no-unsigned-left-shift-operator-in-java))

<details>
    <summary>AND Operator(&)</summary>

```javascript
const a = 5;        // 00000000000000000000000000000101
const b = 3;        // 00000000000000000000000000000011

console.log(a & b); // 00000000000000000000000000000001
// expected output: 1
```
</details>

<details>
    <summary>OR Operator(|)</summary>

```javascript
const a = 5;        // 00000000000000000000000000000101
const b = 3;        // 00000000000000000000000000000011

console.log(a | b); // 00000000000000000000000000000111
// expected output: 7
```
</details>

<details>
    <summary>NOT Operator(~)</summary>

```javascript
const a = 5;     // 00000000000000000000000000000101
const b = -3;    // 11111111111111111111111111111101

console.log(~a); // 11111111111111111111111111111010
// expected output: -6

console.log(~b); // 00000000000000000000000000000010
// expected output: 2
```
</details>

<details>
    <summary>XOR Operator(^)</summary>

```javascript
const a = 5;        // 00000000000000000000000000000101
const b = 3;        // 00000000000000000000000000000011

console.log(a ^ b); // 00000000000000000000000000000110
// expected output: 6
```
</details>

<details>
    <summary>Left shift(<<)</summary>

```javascript
const a = 5;         // 00000000000000000000000000000101
const b = 2;         // 00000000000000000000000000000010

console.log(a << b); // 00000000000000000000000000010100
// expected output: 20
```
</details>

<details>
    <summary>Right shift(>>)</summary>

```javascript
const a = 5;         // 00000000000000000000000000000101
const b = 2;         // 00000000000000000000000000000010

console.log(a >> b); // 00000000000000000000000000000001
// expected output: 1
```
</details>

<details>
    <summary>Unsigned Right shift(>>>)</summary>

```javascript
const a = 5;          //  00000000000000000000000000000101
const b = 2;          //  00000000000000000000000000000010
const c = -5;         //  11111111111111111111111111111011

console.log(a >>> b); //  00000000000000000000000000000001
// expected output: 1

console.log(c >>> b); //  00111111111111111111111111111110
// expected output: 1073741822
```
</details>