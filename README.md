# Controller

Controller는 요청을 처리하고 응답을 반환하는 역할을 한다

- 애플리케이션에 대한 요청을 수신한다
- `라우팅`으로 어떤 컨트롤러가 어떤 요청을 수신하는지 제어한다
- Controller를 만들기 위해 `클래스`와 `데코레이터`를 사용한다

## Routing

Controller를 정의하기 위해 `@Controller()` 데코레이터를 사용해야한다.

- 데코레이터를 사용해 경로를 설정해준다
- `@Get()`과 같은 HTTP 메서드 데코레이터를 설정해준다
- `GET /cats` 요청은 `findAll()`메서드에 대응한다

```js
import { Controller, Get } from '@nestjs/common';
@Controller('cats')
export class CatsController {
  @Get()
  findAll(): string {
    return 'This action returns all cats';
  }
}
```

## Request Object

클라이언트가 보낸 request의 정보를 사용해 응답을 해줄 필요가 있다. 이때 `@Req()` 데코레이터를 추가한 request를 사용한다

```js
import { Controller, Get, Req } from '@nestjs/common';
import { Request } from 'express';

@Controller('cats')
export class CatsController {
  @Get()
  findAll(@Req() request: Request): string {
    return 'This action returns all cats';
  }
}
```

## 응답 코드

응답코드가 `201`인 `POST` 요청을 제외하고는 기본 응답코드는 `200`이다
`@HttpCode()` 데코레이터를 사용해서 쉽게 응답코드를 바꿀 수 있다
