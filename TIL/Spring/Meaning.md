> ERD (Entity Relationship Diagram)
> 
- Entity(개체)와 Relationship(관계)을 중점적으로 표시하는 데이터베이스 구조를 한 눈에 알아보기 위해 그려 놓는 다이어그램

> 매핑(Mapping)
> 
- 해당 값이 다른 값을 가르키 도록 하는 것이다.
- ex) http~/backend.is.best라는 페이지를 만들었다고 가정할 때 이 url이 그대로 유출되면 보안상 취약하다
    
    그래서 backend.is.best = fact 로 설정하여 fact라는 url로 갔을 때 backend.is.best로 가게 한다.

> Lombok
> 
- 어노테이션을 제공하고 컴파일 과정에서 자동으로 개발자가 원하는 메소드를 생성/주입 방식으로 동작하는 라이브러리
- 롬복 라이브러리는 소스 코드를 작성할 때 자바 클래스에 어노테이션을 사용하여 쓰는 Getter메서드, Setter메서드, 생성자 등을 자동으로 만들어 주는 도구이다.
- 반복되는 코드 중복을 줄이고 가독성을 높인다.

> 자주 사용되는 Lombok
> 
- @NoArgsConstructor: 파라미터가 없는 기본 생성자를 만들어줌
- @AllArgsConstructor: 모든 필드 값을 파라미터로 받는 생성자를 만들어줌
- @RequiredArgsConstructor: final이나
- @Builder : 자동으로 해당 클래스에 빌더를 추가해줌

