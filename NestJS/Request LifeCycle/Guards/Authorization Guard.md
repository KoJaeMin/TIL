# Authorization Guard(인증 가드)

인증은 호출자(일반적으로 인증된 특정 사용자)에게 충분한 권한이 있는 경우에만 특정 경로를 사용할 수 있어야 하므로 Guards의 훌륭한 사용 사례입니다. 

빌드할 `AuthGuard`은 인증된 사용자를 가정합니다(따라서 요청 헤더에 토큰이 첨부됩니다).

토큰을 추출 및 검증하고 추출된 정보를 사용하여 요청을 진행할 수 있는지 여부를 결정합니다.

```typescript
import { Injectable, CanActivate, ExecutionContext } from '@nestjs/common';
import { Observable } from 'rxjs';

@Injectable()
export class AuthGuard implements CanActivate {
  canActivate(
    context: ExecutionContext,
  ): boolean | Promise<boolean> | Observable<boolean> {
    const request = context.switchToHttp().getRequest();
    return validateRequest(request);
  }
}
```

함수 내부의 logic인 `validateRequest()`은 필요에 따라 간단하거나 복잡할 수 있습니다.

모든 가드는 `canActivate()`기능을 구현해야 합니다. 이 함수는 현재 요청이 허용되는지 여부를 나타내는 부울을 반환해야 합니다.

Nest는 반환 값을 사용하여 다음 작업을 제어합니다.

- `true`를 반환하면 요청이 처리됩니다.
- `false`를 반환하면 요청을 거부합니다.

## Execution context(실행 컨텍스트)

`canActivate()` 함수는 `ExecutionContext` 인스턴스를 단일 인자로 갖습니다.

`ArgumentsHost` 에 의하여 상속되었습니다.

`ArgumentsHost`를 확장하면 `ExecutionContext` 또한 현재 실행 프로세스에 대한 추가 세부 정보를 제공하는 몇 가지 새로운 도우미 메서드도 추가합니다.

이러한 세부 정보는 광범위한 컨트롤러, 메서드 및 실행 컨텍스트 집합에서 작동할 수 있는 보다 일반적인 가드를 구축하는 데 도움이 될 수 있습니다. 