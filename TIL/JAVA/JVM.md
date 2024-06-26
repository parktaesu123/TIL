> JVM(Java Virtual Machine)
> 
- JVM은 자바를 실행시키기 위한 가상 기계(컴퓨터)이다.
- JAVA는 OS에 종속적이지 않는다는 특징이 있다.
    - OS에 종속받지 않고 실행되기 위해선 OS위에서 Java 를 실행시킬 무언가가 필요하다.
    - JVM이 OS에 종속받지 않고 CPU 가 Java를 인식, 실행할 수 있게 하는 가상 컴퓨터이다.
- Java 소스코드는 CPU가 인식을 하지 못하므로 기계어로 컴파일을 해줘야한다.
    - 하지만 Java는 이 JVM 이라는 가상머신을 거쳐서 OS에 도달하기 때문에 OS가 인식할 수 있는 기계어로 바로 컴파일 되는게 아니라
    JVM이 인식할 수 있는 Java bytecode로 변환된다.
    - 변환된 bytecode는 기계어가 아니기 때문에 OS에서 바로 실행되지 않는다.
    - 이 때, JVM이 OS가 bytecode를 이해할 수 있도록 해석해준다. 따라서 Byte Code는 JVM 위에서 OS 상관없이 실행될 수 있는 것이다.

<aside>
💡 따라서 OS에 종속적이지 않고, Java 파일 하나만 만들면 어느 디바이스든 JVM 위에서 실행할 수 있다.

</aside>
