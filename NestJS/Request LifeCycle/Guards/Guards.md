# Guards

![Guards](../../../image/Guards.png)

Guard란 `CanActivate` interface가 실행되는 `@Injectable()` decorator가 달린 클래스입니다.

Guards는 **단일 책임**(single responsibility)을 갖습니다.

Guards는 request가 런타임에 존재라는 특정 조건(권한, 역할, ACL 등)에 따라 route hander에 의해 처리되는지 여부를 결정합니다. 이것을 주로 `authorization(권한 부여/승인)`라 합니다.

    Guards는 모든 middleware 후에 실행되며 interceptor나 pipe 전에 실행됩니다.


### Reference
[OVERVIEW Guards](https://docs.nestjs.com/guards)