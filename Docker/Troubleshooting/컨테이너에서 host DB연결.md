# 컨테이너에서 host DB 연결

- [이슈] : docker 컨테이너로 띄우고, DB는 docker 컨테이너나 외부DB 가 아닌 HOST의 DB에 연결하려고 하였다. 그리하여 `.env`파일에 기존 HOST에서 사용하는 방식으로 아래와 같이 정의해서 사용해였다. 하지만 연결에 실패하였다.
```.env
DATABASE_HOST=localhost
```

- [이유] : docker 의 localhost 와 HOST의 localhost 는 다르다
    - docker 컨테이너 입장에서 localhost 는 자신 컨테이너를 가리키는 것이기 때문에 localhost 로는 HOST의 로컬DB 와 연결이 안 된다.

- [해결법] : `localhost` 대신 `host.docker.internal` 사용

- [참고 자료]
    - [[docker] docker 컨테이너에서 local 의 DB 에 접속하기](https://shawn-dev.oopy.io/463a30bf-bf32-44e4-88be-8b4722e5549a#9fb8c98b-d690-4f30-9e27-527e0d32525b)
    - [How to connect locally hosted MySQL database with the docker container](https://stackoverflow.com/questions/44543842/how-to-connect-locally-hosted-mysql-database-with-the-docker-container/61480668#61480668)