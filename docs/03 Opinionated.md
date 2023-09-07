# Opinionated
- 스프링부트의 가장 핵심이 되는 자동화에 초점을 둔 이야기
- 이로 인해 소프트웨어의 도메인과 로직 개발에 집중할 수 있게

**자동화?**
- 이전 챕터에 설명되었던 여러 설정 파일들을 신경쓰지 않아도 되는점

## 스프링 프레임워크의 철학
- 정적이었던 이전 서블릿 구조와 달리 모든 것을 교체가능하게 유연하지만 애플리케이션 코드는 방해받지 않는 것을 목적으로 설계되었다.
- 하지만, 그 만큼이나 설정에 대한 고민이 개발자들에게 전달되게 됨
- Not Opinionated

## 스프링부트의 철학
- Opinionated : 가이드 즉, 디폴트를 따라야한다. 단, 설정에 대한 고민 부담이 적어지고 애플리케이션 코드에 집중할 수 있다.
- 개발속도 향상을 목표에 둠

### 스프링부트의 Default 기준
- 표준 자바 기술
- 오픈소스 기술의 종류와 의존관계 및 사용버전을 정의해준다.
- 각 기술을 스프링에 적용하는 방식(DI 구성)과 디폴트 설정값 제공

### 유연한 확장
- 스프링부트에 내장된 디폴트 구성을 커스터마이징하는데 있어 유연한 구조제공
- 모듈화 시키기에 최적화된 프레임워크