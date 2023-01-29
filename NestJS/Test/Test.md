# Test

- 유닛테스트는 서비스에서 분리된 유닛을 테스트하는 것이고 end-to-end 테스트는 모든 시스템을 테스트하는 것이다.

## Jest
- 자바스크립트를 쉽게 테스트할 수 있게하는 npm 패키지이다.
- `.spec.ts`가 붙은 파일은 테스트를 포함한 파일이다.
- 기본적으로 **NestJS**에서는 **jest**가 `.spec.ts` 파일을 찾을 수 있도록 설정돠어있다.

## Unit test
- 모든 function을 따로 테스트하는 것을 의미한다.
- `.spec.ts` 파일을 이용하여 테스트 할 수 있다.

```bash
# jest가 실행된다.
npm run test
# or
# 커버리지 데이터를 수집해 볼 수 있다. 최상위 폴더에 coverage라는 디렉토리가 생성된다.
npm run test:cov
# or
# 관찰자 모드로 실행한다.
npm run test:watch
```

```typescript
import { Test, TestingModule } from '@nestjs/testing';
import { QuestionsService } from './questions.service';

/// describe는 테스트를 묘사한다는 뜻이다.
describe('QuestionsService', () => {
  let service: QuestionsService;

  /// beforeEach는 테스트 전에 실행된다.
  beforeEach(async () => {
    const module: TestingModule = await Test.createTestingModule({
      providers: [QuestionsService],
    }).compile();

    service = module.get<QuestionsService>(QuestionsService);
  });

  /// test를 하는 부분이다.
  it('should be defined', () => {
    expect(service).toBeDefined();
  });
});
```

## End-to-end Test
- 사용자가 취할만한 액션들을 처음부터 끝까지 테스트하는 것을 의미한다.

### Reference
- [NestJS Testing](https://velog.io/@1yongs_/NestJS-Testing-Jest)
- [Jest로 테스트 커버리지 수집하기](https://www.daleseo.com/jest-coverage/)