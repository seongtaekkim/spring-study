## JAR

##### spring boot에서 jar로 패키징 하여 프로그램을 실행.



##### jar 생성

~~~
mvn clean
mvn package
java -jar test.jar
~~~



##### jar 디렉토리 구조

```
example.jar
 |
 +-META-INF
 |  +-MANIFEST.MF
 +-org
 |  +-springframework
 |     +-boot
 |        +-loader
 |           +-<spring boot loader classes>
 +-BOOT-INF
    +-classes
    |  +-mycompany
    |     +-project
    |        +-YourClasses.class
    +-lib
       +-dependency1.jar
       +-dependency2.jar
```

- `classes` 디렉토리에 사용자가 개발한 파일
- `lib`디렉토리에 의존라이브러리 
- `loader` 디렉토리에 라이브러리 loader 파일
- 기본적으로 자바에는 내장 jar를 로딩하는 표준적이 방법이 없다.
- `org.springframework.boot.loader.jar.JarFile`을 사용해서 내장 JAR를 읽는다.
- `org.springframework.boot.loader.Launcher`를 사용해서 실행한다.
  - `MENIFEST.MF` 파일내부에 `Main-Class : org.springframework.boot.loader.JarLauncher` 에서 최초로 프로그램이 시작되고,`Start-Class` 에서 사용자가 정의한 시작부분이 실행된다.





참조 <https://docs.spring.io/spring-boot/docs/current/reference/html/executable-jar.html>