## Why Dynamic?

- 정적 프록시를 통한 구현은 프록시 패턴을 적용해야 하는 클래스마다 프록시 클래스를 직접 구현해야 하는 불편함이 있다.
- 프록시가 필요한 클래스 수만큼 계속 구현을 해줘야함 ⇒ 매우 비효율적임
- **이러한 문제점을 해결하기 위해 프록시 생성을 자동화해주는 Dynamic Proxy가 등장했다.**

## JDK Dynamic Proxy

- 런타임 시점에 인터페이스 기반 프록시 클래스를 자동으로 만들어준다.
- JAVA Reflection API인 Proxy.newProxyInstance() 사용하여 메모리 안에서 동적으로 프록시 인스턴스를 생성해서 반환한다.
- **메서드 호출을 InvocationHandler.invoke()가 가로채서 부가기능을 수행한 뒤 메서드를 대신 처리한다.**
- 프록시 클래스를 구현하지 않고 InvocationHandler를 통해 Proxy Pattern을 적용할 수 있다.

## newProxyInstance()

- 프록시 객체를 생성하는 메서드
- 이 메서드를 통해 프록시 클래스를 정의하지 않고 프록시 인스턴스를 생성 후 등록할 수 있다.

> `import java.lang.reflect.Proxy;`
> 

실제 소스 코드

```java
@CallerSensitive // 메서드 호출자에 따라 보안 정책이 달라짐 
    public static Object newProxyInstance(ClassLoader loader,
                                          Class<?>[] interfaces,
                                          InvocationHandler h) {
        Objects.requireNonNull(h); // InvocationHandler null 체크 후 에러 반환

				/*
					 자바 보안 정책에 의해 권한 확인
					 지금은 잘 안쓰임
			  */
        @SuppressWarnings("removal")
        final Class<?> caller = System.getSecurityManager() == null
                                    ? null
                                    : Reflection.getCallerClass();

        /*
          Look up or generate the designated proxy class and its constructor.
          (번역: 지정된 프록시 클래스와 해당 생성자를 찾거나 생성합니다.)
          프록시를 만들거나 이미 존재할 경우 캐시에서 가져옴	    
         */
        Constructor<?> cons = getProxyConstructor(caller, loader, interfaces);

        return newProxyInstance(caller, cons, h);
    }

    private static Object newProxyInstance(Class<?> caller, // null if no SecurityManager
                                           Constructor<?> cons,
                                           InvocationHandler h) {
        /*
          Invoke its constructor with the designated invocation handler.
          (번역: 지정된 호출 핸들러를 사용하여 생성자를 호출합니다.)
          프록시 클래스의 생성자를 호출하고 생성자에 InvocationHandler를 넣어서 반환
          => 프록시 객체의 메서드를 InvocationHandler에게 위임
         */
        try {
            if (caller != null) { // SecurityManager 보안 권한이 있는지 확인 
                checkNewProxyPermission(caller, cons.getDeclaringClass());
            }

            return cons.newInstance(new Object[]{h});
        } catch (IllegalAccessException | InstantiationException e) {
            throw new InternalError(e.toString(), e);
        } catch (InvocationTargetException e) {
            Throwable t = e.getCause();
            if (t instanceof RuntimeException) {
                throw (RuntimeException) t;
            } else {
                throw new InternalError(t.toString(), t);
            }
        }
    }
```

```java
ClassLoader loader, // Class Loader
Class<?>[] interfaces, // target object interface
InvocationHandler h // target object information handler
```

1. ClassLoader: 실제 프록시 클래스를 만들 클래스 로더
2. interfaces: 프록시가 구현하려고 하는 인터페이스 목록
    - **다중 인터페이스 구현, 다양한 타입으로 캐스팅을 이유로** 인터페이스 목록을 기반으로 **프록시 클래스 생성**
3. InvocationHandler: 프록시의 메서드가 실행되었을 때 호출을 가로채고 실행되는 핸들러

## **InvocationHandler**

- 프록시 객체의 발생하는 모든 메서드 호출을 가로채서 invoke() 메서드를 통해 부가기능을 수행한다.
- InvocationHandler가 메서드를 가로챔으로써 핵심 객체를 수정하지 않으면서 부가기능인 로깅, 트랜잭션, 권한 체크, 캐싱과 같은 작업들을 프록시 객체 마다 구현하지 않고 공통 인터페이스로 처리할 수 있다.
- 인터페이스의 형태로 invoke() 라는 공통 메서드를 제공함으로써 개발자가 부가기능을 처리하는 InvocationHandler 구현한 클래스를 사용하도록 유도한다.

```java
public interface InvocationHandler {
    public Object invoke(Object proxy, Method method, Object[] args)
        throws Throwable;
}
```

1. Proxy : 프록시 객체
2. Method : 호출한 메서드
3. Object[] args : 메서드에 전달된 매개변수
