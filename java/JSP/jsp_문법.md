# JSP 문법

## 스크립트 요소의 이해
- JSP 페이지에서는 선언문(Declaration), 스크립트릿(Scriptlet), 표현식(Expression) 이라는 3가지의 스크립트 요소를 제공

## 선언문
- 선언문 : <%! %>
- 선언문은 JSP 페이지 내에서 필요한 맴버변수나 메소드가 필요할 때 선언해 사용하는 요소
- 선언문의 문법
- <%! 문장 %>
```html
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>

id : <%=getId() %>
</body>
</html>

<%!
    String id = "u001"; //멤버변수 선언
    public String getId( ) { //메소드 선언
        return id;
    }
%>
```

## 스크립트릿
- 스크립트릿 : <% %>
- 가장 일반적으로 많이 쓰이는 스크립트 요소
- 주로 프로그래밍의 로직을 기술할 때 사용
- 스크립트릿에서 선언된 변수는 지역변수
- 스크립트릿의 문법
- <% 문장 %>  
  
jsp
```html
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>

<%
  for(int i = 1; i <= 5; i++){
%>
<H<%=i %>> 아름다운 한글 </H<%=i %>>
<%
  }
%>
</body>
</html>
```
html
```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>


<H1> 아름다운 한글 </H1>

<H2> 아름다운 한글 </H2>

<H3> 아름다운 한글 </H3>

<H4> 아름다운 한글 </H4>

<H5> 아름다운 한글 </H5>

</body>
</html>
```
서블릿 코드 일부분
```java
for(int i = 1; i <= 5; i++){

      out.write('\n');
      out.write('<');
      out.write('H');
      out.print(i );
      out.write("> 아름다운 한글 </H");
      out.print(i );
      out.write('>');
      out.write('\n');

}
```

## 표현식
- 표현식 : <%= %>
- JSP 페이지에서 웹 브라우저에 출력할 부분을 표현 (즉, 화면에 출력하기 위한 것)
- 스크립트릿내에서 출력할 부분은 내장객체인 out 객체의 print() 또는 println() 메소드를 사용해서 출력
- 표현식의 문법
- <%= 문장 %>

## 주석(Comment)
- JSP 페이지에서 사용할 수 있는 주석
- HTML 주석, 자바 주석, JSP 주석

1. HTML 주석  
- HTML 주석은 <!-- <!-- --> -->
- HTML 주석은 HTML 주석을 사용한 페이지를 웹에서 서비스할 때 화면에 주석이 내용이 표시되지는 않으나, 소스 보기를 수행하면 HTML 주석의 내용이 화면에 표시.
2. JSP 주석  
- JSP 페이지에서만 사용되며 <%-- -->
- JSP 주석은 해당 페이지를, 웹 브라우저를 통해 출력 결과로서 표시하거나, 웹 브라우저 상에서 소스 보기를 해도 표시 되지 않음. 또한 JSP 주석 내에 실행코드를 넣어도 그 코드는 실행되지 않음.
3. 자바주석  
- 자바주석은 //, /**/
- //은 한 줄짜리 주석, /**/은 여러 줄 주석
- 스크립트릿이나 선언문에서 사용되는 주석으로, 자바와 주석 처리 방법이 같음

```html
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>
<%--jsp 주석문입니다.
여러줄을 입력할 수 있습니다. --%>
<!-- html 주석문입니다. -->
<%
/*
자바 여러줄 주석문입니다.
*/
  for(int i = 1; i <= 5; i++){ // java 한줄 주석문입니다.
%>
<H<%=i %>> 아름다운 한글 </H<%=i %>>
<%
  }
%>
</body>
</html>
```