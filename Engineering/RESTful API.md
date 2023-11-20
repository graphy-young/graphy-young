>Representational State Transfer Application Programming Interface

HTTP 요청으로 데이터에 CRUD(Create, Read, Update, Delete) 작업을 수행하기 위한 아키텍쳐 스타일
#### 주요 원칙
---
1. **Statelessness**: 각 요청에는 필요한 모든 정보가 포함되므로 Session 상태가 없음
2. **Client-Server Architecture**: Client와 Server는 일반적으로 HTTP를 통해 네트워크에서 통신하는 별개의 Entity
3. **일관된(Uniform) Interface**: RESTful API는 API를 구축하기 위한 표준 규칙 및 규약 세트를 가지고 있어 이해하고 사용하기 쉬움
4. **자원 기반(Resource-based)**: API는 Resource를 중심으로 설계되며, 이는 데이터 객체나 서비스일 수 있고 표준 HTTP 메소드를 사용하여 조작됨
#### HTTP Method
---
1. **GET**: 서버에서 데이터를 **검색** ([RFC 7231 - Section 4.3.1](https://tools.ietf.org/html/rfc7231#section-4.3.1))
2. **POST**: 새 데이터를 서버에 전송 ([RFC 7231 - Section 4.3.3](https://tools.ietf.org/html/rfc7231#section-4.3.3))
3. **PUT**: 서버의 기존 데이터를 업데이트 ([RFC 7231 - Section 4.3.4](https://tools.ietf.org/html/rfc7231#section-4.3.4))
4. **PATCH**: 리소스의 일부를 수정하거나 업데이트 ([RFC 5789](https://tools.ietf.org/html/rfc5789))
5. **DELETE**: 서버에서 데이터를 제거 ([RFC 7231 - Section 4.3.5](https://tools.ietf.org/html/rfc7231#section-4.3.5))
#### 장점
1. **확장성**: 상태가 없다는 것은 RESTful API를 쉽게 확장 가능하게 만듭니다.
2. **유연성**: 클라이언트와 서버는 서로에게 의존하지 않고 별도로 발전할 수 있습니다.
3. **상호 운용성**: 다양한 범위의 클라이언트가 API와 상호 작용할 수 있습니다.
4. **상태 없음**: 캐시 및 최적화가 더 쉽습니다.
#### 단점
1. **Overhead**: 각 요청과 함께 모든 필요한 데이터를 보내는 것은 오버헤드를 생성할 수 있습니다.
2. **복잡성**: 복잡한 작업의 경우, RESTful 스타일은 여러 요청이 필요할 수 있습니다.