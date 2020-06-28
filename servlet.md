
servlet
==============

**동적**으로 요청에 대한 응답 결과를 만들어내는 java class 



tomcat
=============
```
$ whereis tomcat8
tomcat8: /etc/tomcat8 /usr/libexec/tomcat8 /usr/share/tomcat8
```

* /etc/tomcat8  
`/etc/nginx/nginx.conf`와 같이 **tomcat의 설정 관련 정보**  
```
Catalina             jaspic-providers.xml  server.xml
catalina.properties  logging.properties    tomcat-users.xml
context.xml          policy.d              web.xml
```

* /usr/libexec/tomcat8  
스크립트 파일 집합  
```
tomcat-locate-java.sh  tomcat-start.sh  tomcat-update-policy.sh
```

* /usr/share/tomcat8  
jsp-api.jar, servlet-api.jar 등 라이브러리 파일이 저장.   
```
annotations-api.jar       jasper-el.jar       tomcat-i18n-ja.jar
catalina-ant.jar          jasper.jar          tomcat-i18n-ru.jar
catalina-ha.jar           jaspic-api.jar      tomcat-jdbc.jar
catalina-jmx-remote.jar   jsp-api.jar         tomcat-jni.jar
catalina-storeconfig.jar  servlet-api.jar     tomcat-util-scan.jar
catalina-tribes.jar       tomcat-api.jar      tomcat-util.jar
catalina.jar              tomcat-coyote.jar   tomcat-websocket.jar
commons-dbcp.jar          tomcat-dbcp.jar     websocket-api.jar
commons-pool.jar          tomcat-i18n-es.jar
el-api.jar                tomcat-i18n-fr.jar
```
