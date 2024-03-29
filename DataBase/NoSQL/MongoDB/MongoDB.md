# MongoDB

- 
- 온라인 서비스에 필요한 블록 캐시와 보조 인덱스 그리고 동시성 처리를 위한 스킵리스트(Skip-List)나 핮자드 포인터(Hazard Pointer)와 같은 특성을 가지고 있다.
- WiredTiger 스토리지 엔진을 장착했다. (MySQL 서버는 InnoDB 스토리지)

## Version
- 첫 번째 숫자는 메이저 버전(Major Version), 두 번째 숫자는 마이너 버전(Minor Version), 세 번째 숫자는 패치 번호(Patch Version)을 의미한다.
- 마이너 버전 중 홀수 번호는 개발 버전, 짝수 버전은 릴리즈 버전을 의미한다.

## Version Upgrade
- MongoDB 서버의 버전 업그레이드는 일반적으로 서비스를 중지하지 않고, 레플리카 셋의 멤버들을 순차적으로 업그레이드하는 "롤링 업그레이드(Rolling-upgrade)" 방식을 사용한다.
- setFeatureCompatibilityVersion 옵션을 통하여 상위 버전에서만 되는 기능을 업데이트 후 상위 버전의 기능을 활성화 해 준다. 이 옵션은 3.2에서 3.4로 업그레이드 될 때 처음 보입 되었다.

## 특징
- NoSQL
- 스키마 프리(Schema-Free)
    - 테이브의 컬럼 수준에만 적용되며 사용할 컬럼을 미리 정의하지 않고 언제든지 필요한 시점에 데이터를 저장할 수 있다는 것을 의미
    - 다른 NoSQL 데이터베이스와는 달리 보조 인덱스를 생성할 수 있으며 보조 인덱스는 스키마 프리가 아니라 항상 먼저 인덱스를 구성하는 필드를 정의해야한다.
- 비 관계형 데이터베이스

### MongoDB vs RDBMS

| MongoDB 용어 | RDBMS 용어 |
|--------------|-------------|
| Database | Database |
| Collection | Table |
| Document | Record(or Row) |
| Field | Column |
| Index | Index |
| Shard | Partition |
| Aggregation | Join |
| 쿼리의 결과로 `Cursor`반환 | 쿼리의 결과로 `Record`반환 |