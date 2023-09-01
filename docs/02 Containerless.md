# Containerless
- Containerless는 컨테이너를 사용하지않고 개발하자는 개념이 아니라 오히려 `Serverless` 개념에 가까움
- 서버의 설치 및 관를 신경쓰지않고 서버 애플리케이션 코드를 작성하는 것에 초점을 맞춰 운영과 배포에 투자를 더 할수있도록 만든구조

## Container
- 기존의 스프링은 IoC 컨테이너이다.

## Web
- 서비스를 개발할때 `Web Component` 하나(ex.회원가입과 같은 하나의 Feature)를 개발한다고 생각해야한다.
- 이 Web Component는 항상 `Web Client`와 동행되는 개념으로 보통 Client가 Request를 Component에 전달하면 작업을 거쳐 Response를 전달
- Web Componet는 항상 독립적으로 운영되는 것이 아닌, `Web Container`안에서 동작한다.

### Web Component의 목적
- **Dyanmic Content**를 만들어내는 것
- 정적인 응답값이 아닌 Reqeust에 의한 새로운 결과를 반영하여 다시 Client에게 Response 해주는 것

## Web Container
- Life Cycle의 관리
- 여러 Web Component를 관리
- Client의 요청이 어느 Component에서 처리되어야할지 관리
  - Request를 분석하는 **일련의 과정**을 통해 Componet에 전달

> 💡일련의 과정이란 무엇일까?
> 
> 위에서 설명된 일련의 과정은 URL 패턴을 기반으로 분리되는데 이는 DispatcherServlet이라는 컴포넌트에서 수행된다.
> URL 패턴으로 분리된 요청 URL을 해당 컨트롤러에게 전달하는 과정을 의미한다.

## 자바에서의 용어
- Web Contatiner : Servlet Container에 상응하는 개념
- Web Component : Servlet에 상응하는 개념

Servlet Container의 대표적인 예시가 바로 `Tomcat`

<img width="801" alt="스크린샷 2023-09-01 오후 7 40 23" src="https://github.com/DY-WhatSong/BE-What_Song/assets/39437170/767f913a-2233-4e36-8d55-d7432cf8eb95">

해당 구조가 스프링프레임워크 이전부터 사용되던 구조로 이에 대한 불만을 가지고 탄생된게 스프링 프레임워크

그렇다고 Servlet Container나 해당 개념이 뒤바뀐 것이아닌 추가적인 개념으로 사용됨

<img width="1147" alt="스크린샷 2023-09-01 오후 7 42 53" src="https://github.com/DY-WhatSong/BE-What_Song/assets/39437170/85e8d763-5439-4195-b718-f2c8e6eb1d65">

Servlet Container 뒤에 단에서 동작하며 **Bean**과 **Spring Container**로 그 개념이 확장적용됨

## Spring Framework

여기서 한가지 의문점은 Spring Container는 Servlet Container를 대체할 수 없을까? 결론적으로는 **불가능**하다.
대체보다는 **보완**의 개념에 가깝고
`Spring Container`는 애플리케이션의 객체들을 생성하고 관리하며, 객체 간의 의존성을 주입하여 애플리케이션의 구성을 조립하는 것에 목표를 두는 컨테이너이고,
`Servlet Container`는 웹 애플리케이션의 배포와 실행을 관리하는 것에 목적을 둔다.

여기서 한가지더, 스프링을 구성하기 위해선 서블릿 컨테이너가 반드시 필요하고 이에 따른 설정들 간단하게는 port와 매핑설정부터 ClassLoader와 WAR구조 고민까지 신경쓰기엔 개발자의 부담이 너무 높았기에
`Containerless` 개념을 추진하게 되었다.

## Apply Containerless

<img width="1164" alt="스크린샷 2023-09-01 오후 8 09 17" src="https://github.com/DY-WhatSong/BE-What_Song/assets/39437170/da596482-708b-4d4a-9bc0-e7f04c7dee25">

Servlet Container가 **실제로 동작하지 않는것은 아니다**. 다만, **SpringBoot가 이를 Default로 설정하여 개발자에게 설정에 대한 고민을 최소화**시켜준다.

이를 어떻게 간단하게 바꾸었나?

**main()** 메서드를 실행하여 전체의 Application이 구동되는 즉, `Standalone Application` 구조를 통해 최대한의 간편화를 이루어냈다.