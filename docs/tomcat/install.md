# tomcat 설치  

### 1. JRE 설치  
**JDK**가 아닌, **JRE**가 필요하다.  
```
java -version
```
java가 설치되어 있지 않는 경우 추천되는 명령어  
```
Output
Command 'java' not found, but can be installed with:

apt install default-jre
apt install openjdk-11-jre-headless
apt install openjdk-8-jre-headless
```

jre설치  
```
apt install default-jre
```

### 2. tomcat 설치  
```
apt-get install tomcat8
```

상태확인 
```
systemctl status tomcat8
```
