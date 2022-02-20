## SpringApplication



##### spring boot banner - 파일설정

```
==============================
staek spring boot ${application.version}
==============================
```

- /resources/banner.txt

- 스프링부트 시작 시 `banner.txt` 내용이 표출된다.

- `${spring-boot.version}` 등의 변수를 사용할 수 있음.

  - `MENIFEST.MF`에 정의 되어야 사용이 가능함. (jar로 실행)

  





##### spring boot banner - 소스설정

~~~java
@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication application = new SpringApplication(Application.class);
        application.setBannerMode(Banner.Mode.OFF);
        application.run(args);
    }
}
~~~

- 배너 끄기





~~~java
@SpringBootApplication
public class Application {
    public static void main(String[] args) {
        SpringApplication application = new SpringApplication(Application.class);
        application.setBanner(new Banner() {
            @Override
            public void printBanner(Environment environment, Class<?> sourceClass, PrintStream out) {
                out.println("===============");
                out.println("code level staek spring boot");
                out.println("===============");

            }
        });
        application.run(args);
    }
}
~~~

- 배너클래스를 구현하고 `setBanner()` 로 설정 가능

 