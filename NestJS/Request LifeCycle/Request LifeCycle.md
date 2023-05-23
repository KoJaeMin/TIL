# Request LifeCycle

Nest 어플리케이션은 `request lifecycle`이라 불리는 순서로 request를 처리하고 response를 생성합니다.

일반적으로 request는 middleware를 통해 guards, interceptors, pipes , 마지막으로 return path의 interceptors(response가 생성될 때)로 흐릅니다.

## Request LifeCycle 진행
1. Incoming request
2. Globally bound middleware
3. Module bound middleware
4. Global guards
5. Controller guards
6. Route guards
7. Global interceptors (pre-controller)
8. Controller interceptors (pre-controller)
9. Route interceptors (pre-controller)
10. Global pipes
11. Controller pipes
12. Route pipes
13. Route parameter pipes
14. Controller (method handler)
15. Service (if exists)
16. Route interceptor (post-request)
17. Controller interceptor (post-request)
18. Global interceptor (post-request)
19. Exception filters (route, then controller, then global)
20. Server response
![Request LifeCycle](../../image/request%20lifecycle.png)


### Reference
- [NestJS Docs - Request LifeCycle](https://docs.nestjs.com/faq/request-lifecycle)
- [NestJs Request LifeCycle](https://dkrnfls.tistory.com/83)
- [NestJS Request lifecycle](https://velog.io/@hshs0409/NestJS-Request-lifecycle)
- [NestJS Interceptor와 Lifecycle](https://blog-ko.superb-ai.com/nestjs-interceptor-and-lifecycle/)