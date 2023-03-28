# 제네릭(Generic)

정의
- TypeScript 함수 또는 클래스를 정의하는 시점에 매개변수나 반환값의 타입을 선언하지 않고 생성 시점에 타입을 명시하여 하나의 타입만이 아닌 다양한 타입을 사용할 수 있도록 하는 기법이다.
- 재사용 가능한 컴포넌트를 생성하는 도구상자의 주요 도구 중 하나
- 단일 타입이 아닌 다양한 타입에서 작동하는 컴포넌트를 작성 가능하게 해준다.
    - C# 또는 Java에서는 제네릭이라고 하며 C++에는 템플릿(Template)이 있다.

사용법
- `any`를 쓰는 것은 함수의 `arg`가 어떤 타입이든 받을 수 있다는 점에서 제네릭이지만, 실제로 함수가 반환할 때 어떤 타입인지에 대한 정보는 잃게 됩니다. 만약 `number` 타입을 넘긴다고 해도 `any` 타입이 반환된다는 정보만 얻을 뿐입니다.

```typescript
function identity(arg: any): any {
  return arg;
}
```

- 무엇이 반환되는지 표시하기 위해 인수의 타입을 캡처할 방법이 필요합니다. 여기서는 값이 아닌 타입에 적용되는 `타입 변수`를 사용할 것입니다.
- `any`와는 다르게 인자로 받은 타입과 함수에서 반환하는 타입이 동일하다는 것을 알 수 있다.
```typescript
function identity<Type>(arg: Type): Type {
  return arg;
}

/// 하나의 타입이 아닌 배열이 필요하다면 아래와 같은 방법을 사용할 수 있다.

function identity<Type>(arg: Type[]): Type[] {
  return arg;
}

/// or

function identity<Type>(arg: Array<Type>): Array<Type> {
  return arg;
}
```

### Reference
- [TypeSceipr - Generics](https://www.typescriptlang.org/ko/docs/handbook/2/generics.html)
- [타입스크립트 핸드북 - 제네릭](https://joshua1988.github.io/ts/guide/generics.html#%EC%A0%9C%EB%84%A4%EB%A6%AD-%ED%83%80%EC%9E%85)
- []