
# JSP  

### 1. JSP의 위치는 WebContents/  

```
.
├── WebContent
│   ├── META-INF
│   │   └── MANIFEST.MF
│   └── WEB-INF
│       └── lib
├── build
│   └── classes
│       └── exam
│           └── TenServlet.class
└── src
    └── exam
        └── TenServlet.java
```

### 2. jsp 형식  

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>

</body>
</html>
```

### 3. 기호(지시자)  

jsp는 몇가지 약속된 기호를 가진다.
>이 기호를 통하여 jsp가 servlet으로 바뀔 때, 어떻게 바뀔지 결정. 

모든 JSP는 servlet으로 바뀌어서 동작한다.  

#### 3.1. page 지시자  
```
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
```

#### 3.2. <% : 스크립트 릿   
자바 코드를 넣을 수 있는 지시자  
<br/>

#### 3.3. <%= : 표현식  
response의 응답 결과에 보여줄 값은 <%= > 으로 표현된다.  
```jsp
<body>

<% 
    int total = 0;
    for(int i = 1; i <= 10; i++){
        total = total + i;
    }
%>

1부터 10까지의 합 : <%=total %>

</body>
```
<%= 값 %> 이 안에 표현된 값은 out.print()의 값에 들어간다.  

#### 3.4. 실행  
```
http://localhost:8080/exam31/greeting.jsp
```
* 위와 같이 요청 시 다음의 jsp가 servlet으로 변환되어 서빙된다.  
```jsp
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

