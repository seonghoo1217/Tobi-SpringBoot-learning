# Dispatcher Servlet
기존 **Request**를 분석하여 ApplicationContext에 Bean을 등록시키던 방식에서 DispatcherServlet으로 변환하여 줄 경우 DispatcherServlet이 url 패턴기반으로 어떠한 컨트롤러로 연결시켜줘야하는지 매핑에 대한 처리를 자동으로 진행해준다.

하지만, 어노테이션을 통해 Http Method에 대한 타입을 지정하여 DispathcerServlet이 모든 Bean을 탐색할때 등록이 되도록 `@RequestMapping`이 필요하다.

이때 DispatcherServlet의 기본 Return 값은 ViewResolver라는 객체에게 값을 넘겨 해당 String(html파일이름)을 find하게된다.

그렇기에 JSON 혹은 단순 문자열을 Return할 경우에는 `@ResponseBody` 어노테이션을 이용

이를 명시적으로 사용하지 않을 땐 @RestController를 이용한다.
