# redirect

## 리다이렉트 (redirect)
- 리다이렉트는 HTTP 프로토콜로 정해진 규칙이다.
- 서버는 클라이언트의 요청에 대해 특정 URL로 이동을 요청할 수 있다. 이를 리다이렉트라고 한다.
- 서버는 클라이언트에게 HTTP 상태코드 302로 응답하는데 이때 헤더 내 Location 값에 이동할 URL을 추가한다. 클라이언트는 리다이렉션 응답을 받게 되면 헤더(Location)에 포함된 URL로 재요청을 보내게 된다. 이때 브라우저의 주소 창은 새 URL로 바뀌게 된다.
- 서블릿이나 JSP는 리다이렉트를 위해서 HttpServletResponse 클래스의 sendRedirect() 메소드를 사용한다.