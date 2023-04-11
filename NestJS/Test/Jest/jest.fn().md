# jest.fn()

Jest는 자체적으로 mock 기능을 지원힙니다.<br>
가장 기본적으로 `jest.fn()`을 사용하여 가짜 함수(mock function)을 생성할 수 있습니다.
```javascript
const mockCategoryRepository = () => ({
  find: jest.fn(),
  findOneBy: jest.fn(),
  create: jest.fn(),
  update: jest.fn(),
  insert: jest.fn()
});
```
이를 통하여 단위 테스트시 직접적으로 데이터베이스와 연결하는 것이 아닌 가짜의 함수를 만들어 사용합니다. 단위 테스트시 데이터 베이스에 연결한다면 테스트 시간이 오래걸리고 데이터베이스의 상태(전원이 꺼져있거나...)에 따라 테스트가 실패할 수도 있기 때문입니다. 최대한 코드가 아닌 외부적인 요인을 배제하려 사용합니다.
<br><br>
가짜함수는 기본적으로 호출 시 `undefined`를 반환합니다. 일반적인 함수라면 `mockReturnValue`를 사용하고 Promise를 반환하는 함수라면 `mockResolvedValue`나 `mockRejectedValue`와 같은 메서드를 사용하면 객체가 반환하는 값을 지정할 수 있습니다.<br>
만약 함수 실행을 원하면 `mockImplementation`를 사용하면 됩니다.

```javascript
const mockFn = jest.fn();
mockFn.mockImplementation((name) => `I am ${name}!`);
console.log(mockFn("Dale")); // I am Dale!
```