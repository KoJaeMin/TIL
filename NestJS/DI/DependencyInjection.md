# DI(Dependency Injection)

## DI란
- Dependency Injection의 약자로 의존성 주입 또는 의존관계 주입이라 부른다.

## 의존성이란?
- 쉽게 말하면 A와 B가 존재할 경우 A가 변하는 것에 의해 B도 변한다면 **B가 A에 대한 의존성을 갖는다** 라고 말 할 수 있다.
- 흔히 아래와 같이 Class 내부에 Instace를 직접 생성하면 의존성이 생긴다고 본다.

```typescript
class A{
    public num : number = 1;
}

class B{
    private a : A;
    constructor(){
        this.a = new A();
    }
}

let instanceB = new B();
console.log(instanceB['a'].num);
/// 1
```

## 주입이란?
- Class 내부가 아닌 외부에서 객체를 생성해서 넣어주는 것이다.
```typescript
class A{
    public num : number = 1;
}

class B{
    private a : A;
    constructor(a : A){
        this.a = a;
    }
}

let instanceA = new A();
let instanceB = new B(instanceA);
console.log(instanceB['a'].num);
/// 1
```


### Reference
- [견고한 node.js 프로젝트 설계하기](https://velog.io/@hopsprings2/%EA%B2%AC%EA%B3%A0%ED%95%9C-node.js-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%95%84%ED%82%A4%ED%85%8D%EC%B3%90-%EC%84%A4%EA%B3%84%ED%95%98%EA%B8%B0#%EC%9D%98%EC%A1%B4%EC%84%B1-%EC%A3%BC%EC%9E%85-)
- [Dependency Injection(의존성 주입) in Typescript](https://darrengwon.tistory.com/1363)
- [[DI] Dependency Injection 이란?](https://medium.com/@jang.wangsu/di-dependency-injection-%EC%9D%B4%EB%9E%80-1b12fdefec4f)
- [[10분 테코톡] 오찌, 야호의 DI와 IoC](https://www.youtube.com/watch?v=8lp_nHicYd4)