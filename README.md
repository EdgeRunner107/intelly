![2024-05-06 00 28 37](https://github.com/EdgeRunner107/intelly/assets/140359171/9b8afc8e-e49e-48a3-a622-208e675953e5)

![2024-05-06 00 29 33](https://github.com/EdgeRunner107/intelly/assets/140359171/af1a1bc5-0791-4ced-b1be-bdaa9a0dd3c8)


HTTP 프로토콜이란?
HTTP(Hypertext Transfer Protocol)프로토콜이란 상호 간에 정의한 규칙을 의미하며 특정 기기 간에 데이터를 주고받기 위해 정의되었습니다.
통신 프로토콜을 쉽게 풀어보면 “나는 이렇게 줄 테니 넌 이렇게 받고 난 너가 준거 그렇게 받을께” 정도

웹에서는 브라우저와 서버 간에 데이터를 주고받기 위한 방식으로 HTTP 프로토콜을 사용하고 있음

HTTP 프로토콜 특징
HTTP 프로토콜은 상태가 없는(stateless) 프로토콜입니다. 
여기서 상태가 없다라는 말은 데이터를 주고 받기 위한 각각의 데이터 요청이 서로 독립적으로 관리
좀 더 쉽게 말해서 이전 데이터 요청과 다음 데이터 요청이 서로 관련이 없다.

이러한 특징 덕택에 서버는 세션과 같은 별도의 추가 정보를 관리하지 않아도 되고, 다수의 요청 처리 및 서버의 부하를 줄일 수 있는 성능 상의 이점이 생김

HTTP 프로토콜은 일반적으로 TCP/IP 통신 위에서 동작하며 기본 포트는 80번입니다

HTTP Request & HTTP Response
HTTP 프로토콜로 데이터를 주고받기 위해서는 아래와 같이 요청(Request)을 보내고 응답(Response)을 받아야 함
![request-response](https://github.com/EdgeRunner107/intelly/assets/140359171/07cc8f3b-ebb3-4d82-8f66-dced0e705b56)
클라이언트란 요청을 보내는 쪽을 의미하며 일반적으로 웹 관점에서는 브라우저를 의미 서버란 요청을 받는 쪽을 의미하며 일반적으로 데이터를 보내주는 원격지의 컴퓨터를 의미

URL 구조
![url-structure](https://github.com/EdgeRunner107/intelly/assets/140359171/4435bb95-9773-4a8f-af3b-95cea6b68dfd)

HTTP 요청 메서드
URL을 이용하면 서버에 특정 데이터를 요청할 수 있음 여기서 요청하는 데이터에 특정 동작을 수행하고 싶으면 어떻게 해야 할까
 HTTP 요청 메서드(Http Request Methods)를 이용합니다.

일반적으로 HTTP 요청 메서드는 HTTP Verbs라고도 불리우며 아래와 같이 주요 메서드를 갖고 있습니다.

GET : 존재하는 자원에 대한 요청

POST : 새로운 자원을 생성

PUT : 존재하는 자원에 대한 변경

DELETE : 존재하는 자원에 대한 삭제

이와 같이 데이터에 대한 조회, 생성, 변경, 삭제 동작을 HTTP 요청 메서드로 정의할 수 있습니다. 참고로 때에 따라서는 POST 메서드로 PUT, DELETE의 동작도 수행할 수 있습니다.


기타 요청 메서드는 다음과 같습니다.

HEAD : 서버 헤더 정보를 획득. GET과 비슷하나 Response Body를 반환하지 않음

OPTIONS : 서버 옵션들을 확인하기 위한 요청. CORS에서 사용


HTTP 상태 코드
앞에서 살펴본 URL과 요청 메서드가 클라이언트에서 설정해야 할 정보라면 HTTP 상태 코드(HTTP Status Code)는 서버에서 설정해주는 응답(Response) 정보입니다.

버에서 응답으로 오는 상태 코드가 크게 2개로 나뉩니다. 200(성공)과 404(실패)입니다. 따라서, 이 HTTP 상태 코드로 추가적인 로직을 구현할 수 있죠.

주요 상태 코드는 200번대부터 500번대까지 다양하게 있지만 주요한 상태 코드만 몇 개

2xx - 성공
200번대의 상태 코드는 대부분 성공을 의미합니다.

200 : GET 요청에 대한 성공

204 : No Content. 성공했으나 응답 본문에 데이터가 없음

205 : Reset Content. 성공했으나 클라이언트의 화면을 새로 고침하도록 권고

206 : Partial Conent. 성공했으나 일부 범위의 데이터만 반환

3xx - 리다이렉션

300번대의 상태 코드는 대부분 클라이언트가 이전 주소로 데이터를 요청하여 서버에서 새 URL로 리다이렉트를 유도하는 경우입니다.

301 : Moved Permanently, 요청한 자원이 새 URL에 존재

303 : See Other, 요청한 자원이 임시 주소에 존재

304 : Not Modified, 요청한 자원이 변경되지 않았으므로 클라이언트에서 캐싱된 자원을 사용하도록 권고. ETag와 같은 정보를 활용하여 변경 여부를 확인

4xx - 클라이언트 에러

400번대 상태 코드는 대부분 클라이언트의 코드가 잘못된 경우입니다. 유효하지 않은 자원을 요청했거나 요청이나 권한이 잘못된 경우 발생합니다. 가장 익숙한 상태 코드는 404 코드입니다. 요청한 자원이 서버에 없다는 의미죠.


400 : Bad Request, 잘못된 요청

401 : Unauthorized, 권한 없이 요청. Authorization 헤더가 잘못된 경우

403 : Forbidden, 서버에서 해당 자원에 대해 접근 금지

405 : Method Not Allowed, 허용되지 않은 요청 메서드

409 : Conflict, 최신 자원이 아닌데 업데이트하는 경우. ex) 파일 업로드 시 버전 충돌

5xx - 서버 에러

500번대 상태 코드는 서버 쪽에서 오류가 난 경우입니다.

501 : Not Implemented, 요청한 동작에 대해 서버가 수행할 수 없는 경우

503 : Service Unavailable, 서버가 과부하 또는 유지 보수로 내려간 경우

HTTP 요청과 응답 이자 프로토콜
앞에서 배운 URL, 요청 메서드, 상태 코드를 조합하면 아래와 같은 구조
![http-full-structure](https://github.com/EdgeRunner107/intelly/assets/140359171/6c8b39d7-0d7d-433a-818f-34969f5a6a5d)


스프링 - 테스트케이스
테스팅하는 방법으로 쉽게 생각해볼 때 main메서드나 컨트롤러의 url을 호출하는 방법이 있겠지만 
프로젝트 규모가 커지고 여러명이 개발하게 되면 이러한 방법만으로 테스팅하는 것은 쉽지않다.

 Java에서는 이러한 문제를 JUnit이라는 프레임워크를 제공해서
쉽게 만든 기능을 테스트할 수 있는 환경을 제공한다. 

@Test 어노테이션을 붙인 메서드가 테스트할 메서드로 등록이되어 main메서드처럼 실행할 수 있게 된다.
그리고 @AfterEach 어노테이션을 붙인 메서드는
각 테스트메서드들이 실행완료된 다음에 한번씩 호출이 된다.


Optional이란?
존재할수도 있지만 안할 수도 있는 객체, null이 될 수도 있는 객체를 감싸고 있는 일종의 래퍼 클래스
기존엔 객체를 직접 null인지 체크 했지만 optional에 담아서 쓰면 null을 다루기가 좋아짐
 

Optional의 효과
명시적으로 해당 변수가 null일 수도 있다는 가능성을 표현할 수 있음
NPE를 유발할 수 있는 null을 직접 다루지 않아도 됨
null체크를 직접 하지 않아도 됨
 
Optional 기본 사용법
Optional 선언
제네릭을 제공하기 때문에, 변수를 선언할 때 작성한 타입 파라미터에 따라서 감쌀 수 있는 객체의 타입이 결정됨
변수명은 maybe나 opt 같은 접두어를 붙여서 Optional타입이라는 것을 알리기도 함
Optional<Order> optOrder;
객체 생성
Optional.empty()
null을 담고 있는 Optional 객체를 얻어옴
비어있는 객체는 Optional 내부적으로 미리 생성해 놓은 싱글턴 인스턴스
Optional<User> optUser = Optional.empty()
Optional.of(value)
null이 아닌 객체를 담고 있는 Optional 객체를 생성
null이 넘어올 경우, NPE를 던지기 때문에 주의해서 사용
Optional<User> optUser = Optional.of(user);
 Optional.ofNullable(value)
null인지 아닌지 확신할 수 없는 객체를 담고 있는 Optional 객체 생성
Optional.empty()와 Optional.of(value)를 합쳐놓은 메소드
Optional.of(value)의 경우 null이 넘어오게 되면 NPE를 던지지만 이건 null이 넘어오면 비어있는 Optional 객체를 줌
해당 객체가 null인지 아닌지 자신없는 상황에서는 이 메소드를 사용
Optional<User> optUser = Optional.ofNullable(null);
 


Optional 객체 존재 여부 확인
옵셔널은 Null일 수도 아닐 수도 있기 때문에 객체가 존재하는지 아니면 비어있는지 확인을 해야 함
아래 메소드를 활용하여 존재 여부를 확인하여 이후 로직을 진행하도록 분기 처리를 할 수 있음
isPresent( )
boolean을 반환하는 메소드
Optional.isPresent() 의 경우 객체가 존재하면 true가 리턴되고, 비어있는 경우 false를 리턴 함
 
Optional<String> optStr = Optional.ofNullable("test"); if (optStr.isPresent()) { System.out.println(optStr.get()); }
ifPresent( )
Optional.ifPresent(Cosumer<? super String> consumer>)
옵셔널에 객체가 존재하면 ( ) 가로 안에 작업을 진행하라는 메소드
리턴되는 값 void
Optional<String>optStr=Optional.ofNullable("test");
optStr.ifPresent(str->System.out.println(str));
 

Optional이 담고 있는 객체 접근
Optional 클래스는 담고 있는 객체를 꺼내오기 위해서 다양한 인스턴스 메소드를 제공
아래 메소드 모두 Optional이 담고 있는 객체가 존재할 경우 동일하게 해당 값을 반환하고 비어 있는 경우 작동이 다르기 때문에 특징을 알아야 함
get( )
비어있는 Optional 객체에 대해서, NoSuchElementException을 던짐
비어있지 않은 Optional에 사용해야 함
orElse(T other)
옵셔널이 비어 있다면 파라미터로 입력한 인자를 리턴하게 됨
orElseGet(Supplier<? extends T> other)
비어있는 Optional 객체에 대해서, 넘어온 함수형 인자를 통해 생성된 객체를 반환
orElse(T other) 메소드와 동일하게 리턴 하지만 비어있는 경우만 함수를 호출해서 성능상 이점 기대 가능
orElseThrow(Supplier<? extends X> exceptionSupplier)
비어 있는 Optional객체에 대해, 넘어온 함수형 인자를 통해 생성된 예외를 던짐
 


 

실무에서 사용한 Optional 간단 예시
실무를 하면서 Optional을 가장 많이 사용하는 것이 DB에서 데이터를 조회하는 경우이다. 현재 진행중인 프로젝트에서 JPA를 사용하고 있고, 1건만 조회하는 경우 리턴 값을 optional로 받고 있다. 참고로 JPA는 단건 반환의 메소드의 경우 Optional로 준다.


 

옵셔널로 받는 이유는 조건에 따라 조회를 하면 무조건 리턴되는 데이터가 있는 것이 아니기 때문이다. 리턴된 데이터가 없으면 에러를 내려줘야 하는 경우도 있고, 리턴된 데이터가 없으면 임의의 데이터를 추가해 줘야 하기 때문에 Optional 메소드를 활용하여 사용하고 있다.

 

특징이나 상세 설명처럼 optional로 받으면 제공되는 메소드로 null을 확인하거나 예외처리 등을 할 수 있다. 참고로 제대로 옵셔널을 활용하는 사람중에는 Stream처럼 사용하는 경우들이 있다. 그럼 소스 코드를 더 간단하게 작성할 수 있다.

Optional.ofNullable(user)
        .map(User::getGroup)
        .map(Group::getName)
        .orElse("Team1");
 

 

프로젝트에서 JPA로 Optional을 사용한 간단한 예시 코드는 아래와 같다. 아마 예시를 보면 이런식으로 쓰는구나 라고 이해하기 좋을 것이다.

 

JPA repository 인터페이스에서 내가 조회하고자 하는 메소드를 추가하고, 해당 데이터를 조회해 오는 코드에서 사용한다. Optional로 받아도 되지만 해당 이름을 가진 유저가 무조건 나와야 하는 경우에는 아래와 같이 없는 경우 에러를 던지게 처리할 수 있다. 일반적으로 프론트에서 해당 사원을 데이터를 주고 그걸 조회하기 떄문에 데이터가 없는 경우 에러를 내리게 처리했다.

 

JPA repository code

@Repository
public interface UserRepository extends JpaRepository<UserEntity, Long> {
    Optional<UserEntity> findByName(String Name);
}
 

Service class code

String name = "sun";
UserEntity optUserEntity = userRepository.findByName(name)
          .orElseThrow(() -> new EmptyDataException("해당 이름을 가진 유저가 데이터가 없음"));

