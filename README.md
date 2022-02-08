nestjs + postgresql + TypeORM + graphQL + jwt + kakaoOauth

# DB

1. typeorm 설치

```sh
yarn add typeorm @nestjs/typeorm --save
```

2. ormconfig.json 파일 추가

```js
{
  "type": "postgres",
  "host": "localhost",
  "port": 5432,
  "username": "username",
  "password": "password",
  "database": "DB이름",
  "entities": ["dist/**/**.entity{.ts,.js}"],
  "synchronize": true //
}
```

- `type` : 사용하게 될 DBMS
- `host` : 연결 주소 (localhost or DB서버 주소)
- `port` : 연결 포트(기본5432)
- `username`
- `password`
- `database`
- `entities` : dist 아래의 폴더. 이 설정의 경로에 있는 파일을 참고하여 DB에서 스키마를 설정하게 됨
- `synchronize` : true 로 하시면 실행시 DB 스키마가 자동으로 생성되게 됩니다. production일 때와 development일때 다르게 해야됨

### app.module.ts에서 TypeOrm 설정

```js
// app.module.ts
import { TypeOrmModule } from '@nestjs/typeorm';
@Module({
  imports: [TypeOrmModule.forRoot()],
})
```

- `ormconfig.json`을 생성해주었기 때문에 forRoot()메서드 안에 아무것도 안적어줘도 됨
