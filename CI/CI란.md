# CI란

- 개발자를 위한 자동화 프로세스인 지속적인 통합(Continuous Integration)
- 개발자가 각각 개발한 소스코드를 모아서 한꺼번에 빌드하는 통합 빌드의 과정을 특정 시점이 아니라 매일이나 매주와 같이 아주 잦은 주기로 수행함으로써 통합에서 발생하는 오류와 시간을 줄이기 위한 기법
- TOOL로는 Github Actions, Jenkins 등이 있다.(본인은 현재 Github Actions를 이용합니다.)

## 특징
- 소스코드 일관성 유지
- 자동 빌드
    - 커밋에 따른 자동 빌드
    - 시간 간격에 의한 빌드
- 자동 테스팅
- 일일 체크아웃과 빌드

### Reference
- [Hudson을 이용한 빌드와 테스트의 자동화](http://bcho.tistory.com/entry/Hudson%EC%9D%84-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EB%B9%8C%EB%93%9C-%EB%B0%B0%ED%8F%AC-%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%9E%90%EB%8F%99%ED%99%94)
- [CI ( Continuous Integration ) 툴 기초. CI 는 무엇인가?](https://aroundck.tistory.com/2723)
- [CI/CD(Continuous Integration/Continuous Delivery)란?](https://www.redhat.com/ko/topics/devops/what-is-ci-cd)