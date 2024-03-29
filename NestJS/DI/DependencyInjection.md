# DI(Dependency Injection)

## DI란
- Dependency Injection의 약자로 의존성 주입 또는 의존관계 주입이라 부른다.
- 의존성을 분리시켜 사용하며 결합도를 낮추는 작업이다.

- 장점
    - 의존성이 줄어든다.
    - 재사용성이 높은 코드가 된다.
    - 테스트하기 좋은 코드가 된다.
    - 가독성이 높아진다.

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

let instanceB = new B(new A());
console.log(instanceB['a'].num);
/// 1
```

## 의존성 분리
- 의존관계 역전의 원칙으로 의존관계를 분리시킨다.

```typescript
/// 인터페이스를 이용하여 의존성을 분리시킬 수 있다.
/// number를 변수로 갖는 class면 어떤 class여도 B class에 주입할 수 있다.
interface DIinterface{
    num : number
}

class A implements DIinterface{
    public num : number = 1;
}

class C implements DIinterface{
    public num : number = 2;
}

class B{
    private a : DIinterface;
    constructor(a : DIinterface){
        this.a = a;
    }
}

let instanceB0 = new B(new A());
let instanceB1 = new B(new C());
console.log(instanceB0['a'].num);// 1
console.log(instanceB1['a'].num);// 2
```
```typescript
/// interface가 제어의 주체가 된다.
interface DIinterface{
    // num : number
}

class A implements DIinterface{
    public num : number = 1;
}

class C implements DIinterface{
    public num : number = 2;
}

class B{
    private a : DIinterface;
    constructor(a : DIinterface){
        this.a = a;
    }
}

let instanceB0 = new B(new A());
let instanceB1 = new B(new C());
console.log(instanceB0['a'].num);// error
console.log(instanceB1['a'].num);// error
```

## IoC(Inversion of Control, 제어의 역전)
- IoC는 메소드나 객체의 호출작업을 개발자가 결정하는 것이 아니라, 외부에서 결정되는 것을 의미한다.
- NestJS에서 Provider 간의 관계를 관리하는 ("IoC") 컨테이너가 있다.


### Reference
- [견고한 node.js 프로젝트 설계하기](https://velog.io/@hopsprings2/%EA%B2%AC%EA%B3%A0%ED%95%9C-node.js-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%95%84%ED%82%A4%ED%85%8D%EC%B3%90-%EC%84%A4%EA%B3%84%ED%95%98%EA%B8%B0#%EC%9D%98%EC%A1%B4%EC%84%B1-%EC%A3%BC%EC%9E%85-)
- [Dependency Injection(의존성 주입) in Typescript](https://darrengwon.tistory.com/1363)
- [[DI] Dependency Injection 이란?](https://medium.com/@jang.wangsu/di-dependency-injection-%EC%9D%B4%EB%9E%80-1b12fdefec4f)
- [[10분 테코톡] 오찌, 야호의 DI와 IoC](https://www.youtube.com/watch?v=8lp_nHicYd4)
- [DI는 IoC를 사용하지 않아도 된다](https://jwchung.github.io/DI%EB%8A%94-IoC%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80-%EC%95%8A%EC%95%84%EB%8F%84-%EB%90%9C%EB%8B%A4)
- [NestJS provider](https://docs.nestjs.com/providers#custom-providers)