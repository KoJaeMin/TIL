# DTO and Validation

## DTO란
-   DTO란 Data Transfer Object의 약자로 네트워크 상에서 데이터를 어떻게 보낼지 정의 하는 객체이다. 한마디로 데이터 형태에 대한 약속이다.

```typescript
/// dto 파일
export class CreateQuestionDto{
    readonly typeId : number;
    readonly degree : number;
    readonly contents : string;
    readonly activate : boolean;
}
```


## Type Validation
- 기본적으로 DTO를 정의하더라도 다른 형태의 데이터를 수신할 수 있다. 이를 방지하기 위해 Validation 기능을 추가해 줘야한다.
- class-validator는 validation 기능을 수행하기 위해서 class-transformer는 데이터 타입을 변환시켜주기 위해 사용한다.
```console
npm install --save class-validator class-transformer
```

```typescript
/// main.ts
import { ValidationPipe } from '@nestjs/common';
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  /// 글로벌 pipe 부분에 ValidationPipe를 추가해준다.
  app.useGlobalPipes(new ValidationPipe({
    whitelist: true, // validation을 위한 decorator가 붙어있지 않은 속성들은 제거
    forbidNonWhitelisted: true, // whitelist 설정을 켜서 걸러질 속성이 있다면 아예 요청 자체를 막도록 (400 에러)
    transform: true, // 요청에서 넘어온 자료들의 형변환
  }));

  await app.listen(3000);
}
bootstrap();
```


- 변수명 뒤에 물음표가 있다면 값이 없어도 된다. (필수적인 요소가 아니라는 뜻이다./IsOptional 데코레이터를 사용해도 된다.)

```typescript
export class CreateQuestionDto{
    @IsNumber()
    readonly typeId : number;

    @IsNumber()
    readonly degree : number;

    @IsString()
    readonly contents : string;

    @IsOptional()
    @IsBoolean()
    readonly activate : boolean;
    // 아래의 코드는 위와 동일한 효과를 낸다.
    // @IsBoolean()
    // readonly activate? : boolean;
}
```

- 만약 Array로 하는 경우 each를 true로 변경시키면 Array안에 있는 각각의 원소들을 validation을 수행한다.
```typescript
    @IsString({each:true})
    readonly contents : string[];
```

- 추가적으로 CreateQuestion DTO가 아닌 UpdateQuestion DTO의 경우 모든 값을 필수적으로 바꾸지 않아도 된다. 이런 경우 @nestjs/mapped-types를 사용하면 간단하게 모든 property를 Optional로 바꿔줄수 있다.
```typescript
export class UpdateQuestionDto extends PartialType(CreateQuestionDto){}
```