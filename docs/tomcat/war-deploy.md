
# war 배포하기  
#### [참고](https://13akstjq.github.io/aws/2019/05/29/how-to-deploy-spring-lagacy-project-ec2-aws.html)  

#### 1. eclipse에서 project 우클릭 - [export] - [WAR file]  
다음과 같은 추축될 war파일 GET!  
```
exam31.war
```

#### 2. /var/lib/tomcat/webapps/ 디렉토리로 옮김  
```
/var/lib/tomcat8/webapps $ ls
ROOT 
exam31.war
```

#### 3. 옮긴 war 파일에 대한 권한 설정  
war 파일을 **tomcat** 소유로 바꾼다.  
* 권한 변경  
```
chown tomcat8:tomcat8 exam31
```
* 변경된 권한 확인  
```
drwxr-x--- 4 tomcat8 tomcat8 4096  6월 29 01:02 exam31
```

#### 4. tomcat 재시작할 필요 없음.  
```
systemctl reload tomcat8
```

#### 5. 접근  
exam31은 root context  
```
http://127.0.0.1:8080/exam31/ten
```

### 6. log 확인  

#### 로그 파일 위치   
```
/var/log/tomcat8
```

#### access_log  
>txt형태와 gz형태 두 가지의 로그  
```
localhost_access_log.2020-06-29.txt.gz
localhost_access_log.2020-06-29.txt
```
