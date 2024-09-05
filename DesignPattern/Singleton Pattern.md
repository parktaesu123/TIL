## 싱글톤 패턴

<aside>
🚀

싱글 톤 패턴이란??

</aside>

- 단 하나의 유일한 객체를 만들기 위한 코드 패턴
- 메모리 절약을 위해 똑같은 인스턴스를 새로 만들지 않고 기존의 인스턴스를 가져와 활용하는 기법
- 클래스에 인스턴스를 하나만 두고 이 인스턴스를 전역 변수처럼 활용하는 디자인 패턴

### 싱글톤 패턴 구현 원리

1. 생성자에서 인스턴스가 생성되는 것을 제한 → 생성자에 접근제한자 private
2. getInstance()라는 메서드에 생성자를 초기화
3. getInstance()메서드 실행해서 Instance 필드가 null값이면 초기화하고 아닐 경우에는 이미 생성된 객체 반환

### 문제점

- **모듈간 의존성이 높아진다.**
- **S.O.L.I.D 원칙에 위배되는 사례가 많다.**

### 참고자료

https://refactoring.guru/ko/design-patterns/singleton

https://inpa.tistory.com/entry/GOF-💠-싱글톤Singleton-패턴-꼼꼼하게-알아보자
