# JSP란?

## JSP 등장 배경
- 마이크로소프트에서 ASP(Active Server Page)라는 쉽게 웹을 개발할 수 있는 스크립트(script) 엔진을 발표함 (1998년)
- 1997년에 발표된 서블릿은 ASP에 비하여 상대적으로 개발 방식이 불편함
- ASP에 대항하기 위하여 1999년 썬마이크로시스템즈에서 JSP를 발표
- JSP는 실제로 서블릿 기술을 사용

```html
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>sum10</title>
</head>
<body>

<% 
    int total = 0;
    for(int i = 1; i <= 10; i++){
        total = total + i;
    }
%>

1부터 10까지의 합 : <%=total %>

</body>
</html>
```