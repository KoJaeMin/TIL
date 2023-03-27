# Controllers

## Scopes
Node.js는 매 요청마다 새로운 스레드를 이용하여 처리되는 **request/response Multi-Threaded Stateless Model**을 따르지 않는다. 그러므로 singleton instance를 사용하는 것은 매우 안전하다.
그러나, GraphQL 애플리케이션의 요청별 캐싱, request tracking 또는 multi-tenancy와 같이 컨트롤러의 요청 기반 수명이 원하는 동작일 수 있는 **edge-cases**가 있습니다.

  - edge-cases : 알고리즘이 처리하는 데이터의 값이 알고리즘의 특성에 따른 일정한 범위를 넘을 경우에 발생하는 문제를 가리킨다.

## Asynchronicity
- NestJS async 함수를 지원하며 잘 작동한다. 추가적으로 Nest의 route handler는 **RxJS observable streams**을 반환할 수 있어 더욱 강력하다.
- Nest는 자동적으로 아래의 소스를 구독하고 마지막으로 방출된 값을 가져옵니다.(한번 stream이 완료되면)

```typescript
/// async 버전
@Get()
async findAll(): Promise<any[]> {
  return [];
}
/// RxJS observable streams 버전
@Get()
findAll(): Observable<any[]> {
  return of([]);
}
```