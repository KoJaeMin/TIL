## 웹

<details>
  <summary>REST API에 대하여 설명해 주세요.</summary>
  <br>

- “Representational State Transfer” 의 약자로 자원을 이름(자원의 표현)으로 구분하여 해당 자원의 상태(정보)를 주고 받는 모든 것을 의미합니다.

- 구성요소
    - 자원(Resource)
    - 행위(Verb)
    - 표현(Representations) 

- 제약조건
  - Client-Server
  - Stateless
  - Caching
  - Uniform Interface
    - identification of resources
    - manipulation of resources through representations
    - self-descriptive message
    - HATEOAS(hyermedia as thr engine of application state)
  - Layered System
  - Code on demand(Optional)

</details>


<details>
  <summary>MVC에 대하여 설명해 주세요.</summary>
  <br>

- MVC(Model-View-Controller) 패턴은 소프트웨어 개발에서 사용되는 아키텍처 패턴 중 하나로, 소프트웨어의 구성 요소를 Model, View, Controller 3개의 역할로 분리하여 각각의 역할을 담당하도록 설계하는 패턴입니다.
- 각각의 역할을 분리하여, 코드의 재사용성과 유지보수성을 향상시키고, 소프트웨어 개발 과정에서의 역할 분담과 협업을 용이하게 합니다.

### 역할
  - Model: 애플리케이션의 데이터와 데이터 처리 로직을 담당합니다. 데이터의 유효성 검사, 데이터베이스와의 상호작용, 데이터의 변경 등의 작업을 수행합니다.
  - View: 사용자 인터페이스(UI)를 담당합니다. 모델에서 처리한 데이터를 적절한 형식으로 사용자에게 보여주거나, 사용자의 입력을 수신하여 컨트롤러에 전달합니다.
  - Controller: 모델과 뷰 간의 상호작용을 조정합니다. 사용자의 입력에 따라 모델의 데이터를 업데이트하거나, 뷰의 표시를 갱신합니다.


</details>

<details>
  <summary>Cookie, 세션(Session)에 대하여 설명해 주세요.</summary>
  <br>

- Cookie
  - 웹 서버가 클라이언트(웹 브라우저)에게 전송하는 작은 데이터 조각입니다.
  - 쿠키는 클라이언트 측에서 저장되며, 클라이언트가 웹 서버에 요청을 보낼 때마다 해당 쿠키가 함께 전송됩니다.

- Cookie 특징
  - 이름, 값, 만료일(저장 기간 설정), 경로 정보로 구성되어 있습니다.
  - 클라이언트에 총 <b>300</b>개의 쿠키를 저장할 수 있습니다.
  - 하나의 도메인 당 <b>20</b>개의 쿠키를 가질 수 있습니다.
  - 하나의 쿠키는 <b>4KB(=4096byte)</b>까지 저장 가능합니다.

- 쿠키의 동작 순서
  1. 클라이언트가 페이지를 요청합니다. (사용자가 웹사이트 접근)
  2. 웹 서버는 쿠키를 생성합니다.
  3. 생성한 쿠키에 정보를 담아 HTTP 화면을 돌려줄 때, 같이 클라이언트에게 돌려줍니다.
  4. 넘겨 받은 쿠키는 클라이언트가 가지고 있다가(로컬 PC에 저장) 다시 서버에 요청할 때 요청과 함께 쿠키를 전송합니다.
  5. 동일 사이트 재방문시 클라이언트의 PC에 해당 쿠키가 있는 경우, 요청 페이지와 함께 쿠키를 전송합니다.

- 세션(Session)
  - 서버 측에서 클라이언트의 상태를 유지하기 위해 사용되는 개념입니다.
  - 클라이언트가 서버에 접속하면 서버는 클라이언트에게 고유한 세션 ID를 부여하고, 해당 세션 ID를 서버에 저장합니다. 클라이언트가 서버에 요청을 보낼 때마다 세션 ID를 함께 전송하고, 서버는 세션 ID를 사용하여 클라이언트의 상태를 유지합니다.
  - 방문자가 웹 서버에 접속해 있는 상태를 하나의 단위로 보고 그것을 세션이라 합니다.

- 세션 특징
  - 웹 서버에 웹 컨테이너의 상태를 유지하기 위한 정보를 저장합니다.
  - 웹 서버의 저장되는 쿠키(=세션 쿠키)
  - 브라우저를 닫거나, 서버에서 세션을 삭제했을때만 삭제가 되므로, 쿠키보다 비교적 보안이 좋습니다.
  - 저장 데이터에 제한이 없습니다.(서버 용량이 허용하는 한...)
  - 각 클라이언트 고유 Session ID를 부여합니다. Session ID로 클라이언트를 구분하여 각 클라이언트 요구에 맞는 서비스 제공합니다.

- 세션의 동작 순서
  1. 클라이언트가 페이지를 요청합니다. (사용자가 웹사이트 접근)
  2. 서버는 접근한 클라이언트의 Request-Header 필드인 Cookie를 확인하여, 클라이언트가 해당 session-id를 보냈는지 확인합니다.
  3. session-id가 존재하지 않는다면, 서버는 session-id를 생성해 클라이언트에게 돌려줍니다.
  4. 서버에서 클라이언트로 돌려준 session-id를 쿠키를 사용해 서버에 저장합니다. 쿠키 이름 : JSESSIONID
  5. 클라이언트는 재접속 시, 이 쿠키(JSESSIONID)를 이용하여 session-id 값을 서버에 전달합니다.

</details>

<!-- <details>
  <summary>JWT(JSON Web Token)에 대하여 설명해 주세요.</summary>
  <br>


</details> -->


### Reference
- [쿠키(Cookie), 세션(Session) 특징 및 차이](https://hahahoho5915.tistory.com/32)