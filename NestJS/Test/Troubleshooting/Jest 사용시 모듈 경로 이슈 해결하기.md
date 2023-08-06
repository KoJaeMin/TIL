# Jest 사용시 모듈 경로 이슈 해결하기

처음 Entity를 작성하고 `npm run test`을 이용하여 Unit Test를 한다면 아래와 같이 에러가 발생한다.

```bash
 FAIL  src/coursecategory/coursecategory.service.spec.ts
  ● Test suite failed to run

    Cannot find module 'src/entities/category.entity' from 'coursecategory/coursecategory.service.spec.ts'

      1 | import { Test, TestingModule } from '@nestjs/testing';
      2 | import { getRepositoryToken } from '@nestjs/typeorm';
    > 3 | import { Category } from 'src/entities/category.entity';
        | ^
      4 | import { Course } from 'src/entities/course.entity';
      5 | import { CourseCategory } from 'src/entities/coursecategory.entity';
      6 | import { CoursecategoryService } from './coursecategory.service';

      at Resolver._throwModNotFoundError (../node_modules/jest-resolve/build/resolver.js:491:11)
      at Object.<anonymous> (coursecategory/coursecategory.service.spec.ts:3:1)
```

이를 해결하기 위한 방법은 두 가지 정도 였다.

1. 상대 경로로 저장을 해준다. src 대신 ..와 같은 상대 경로를 지정하니 에러는 사라졌다.
하지만 만약 코드와 파일들이 많아진다면 매우 번거롭다.
```typescript
import { Category } from 'src/entities/category.entity';
/// 대신에
import { Category } from '../entities/category.entity';
```

2. jest의 디렉토리를 매핑해 준다. 먼저 아래와 같이 `package.json`에 jest설정이 기본적으로 되어 있다.
```json
/// package.json
"jest": {
    // ...
    // 생략
    // ...
    "coverageDirectory": "../coverage",
    "testEnvironment": "node"
}
```
하지만 마지막 부분에 이래를 추가해 준다면 src 디렉토리를 매핑할 수 있다.
```json
"moduleNameMapper": {
  "^src/(.*)$": "<rootDir>/$1"
}
```
결론적으로 아래와 같이 된다.
```json
/// package.json
"jest": {
     // ...
    // 생략
    // ...
    "coverageDirectory": "../coverage",
    "testEnvironment": "node",
    "moduleNameMapper": {
      "^src/(.*)$": "<rootDir>/$1"
    }
}
```
이 방법을 써서 unit test는 정상적으로 작동하나 e2e test에서는 작동을 하지 않는다.

이를 해결하기 위해서 아래와 같이 e2e test의 설정을 해주면 e2e test에도 적용된다.

```json
/// jest-e2e.json
{
  "moduleFileExtensions": ["js", "json", "ts"],
  "rootDir": ".",
  "testEnvironment": "node",
  "testRegex": ".e2e-spec.ts$",
  "transform": {
    "^.+\\.(t|j)s$": "ts-jest"
  },
  "moduleDirectories": ["<rootDir>/../", "node_modules"]
}
```