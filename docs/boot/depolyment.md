# Spring boot application 배포  

Tomcat이 내장된 spring boot 프로젝트는 jar로 바로 배포가능하다.
>그렇기에 jar파일 형태로 바로 배포가 가능하다. jar파일로 배포가 가능하다는 것은 java -jar command로 바로 실행가능한 것이다.  

* Spring boot의 강점은 내장 서버가 있어서 **실행 가능한 jar**파일로 만들어 배포하기가 쉽다.  
* 많은 의존성 라이브러리를 하나의 jar파일로 **패키징**하는 것이다.  

<br/>

war형태로 배포하는 경우는 기존의 tomcat에 올릴 때 사용한다.  
>즉, 내장 tomcat을 사용하지 않고 배포할 때 사용하는 것.  

<br/>

## 1. jar파일로 패키징 및 빌드하기  
build.gradle 파일에서 gradle에 대한 **plugin**을 추가한다.   
```
plugins {
    id 'org.springframework.boot' version '2.3.1.RELEASE'
    id 'io.spring.dependency-management' version '1.0.9.RELEASE'
    id 'java'
}

group = 'io.horoyoiis'
version = '0.0.1-SNAPSHOT'
sourceCompatibility = '11'

apply plugin: 'io.spring.dependency-management'   << 추가하기
...
```

## 2. gradle 실행하기  

* 빌드하기  
```
$ gradle bootjar
```

* 프로젝트의 `build` - `libs` 디렉토리 아래에 실행가능한 jar파일이 생성된다.  
```
/Desktop/webservice
build 
├── libs
│   └── webs-0.0.1-SNAPSHOT.jar

```

## 3. 실행 확인하기  
* 아래의 command로 프로젝트를 실행할 수 있다.  
```
$ java -jar webs-0.0.1-SNAPSHOT.jar
```

<br/>

## 4. 배포 스크립트 작성  

1. git clone, git pull을 통해 새 버전의 프로젝트를 배포 서버에 다운.  
2. gradle/maven을 통해 프로젝트의 test 및 build  
3. 배포 서버에서 해당 프로젝트를 실행  

#### 4.1. git clone  
```
$ mkdir ~/app/git
$ git clone https://github.com/horoyoii/blog.git
```

#### 4.2. 배포 스크립트 내용  
* 배포 서버에 배포 스크립트를 작성한다.  
```
$ vim ~/app/git/deploy.sh

$ chmod 755 deploy.sh
```
* 배포 서버에 `gradle`이 설치되어 있지 않더라도, **gradlew**를 사용하여 테스트 및 빌드 가능  
* java -jar 형태로 실행한다.  

```sh
#! /bin/bash

REPOSITORY=/root/app/git

PROJECT=blog

cd $REPOSITORY/$PROJECT

echo ">git pull"

git pull

echo "> start build"

./gradlew build

echo "> copy the jar file"

cp ./build/libs/*.jar $REPOSITORY/

CURRENT_PID=$(pgrep -f webs)

echo $CURRENT_PID

if [ -z CURRENT_PID ]; then
        echo "> 실행 중인 어플리케이션 없음"
else 
        echo ">kill -2 $CURRENT_PID"
        kill -9 $CURRENT_PID
        sleep 5
fi

echo "> 새 버전 배포"

JAR_NAME=$(ls $REPOSITORY/ |grep 'webs' | tail -n 1)

echo "> JAR name : $JAR_NAME"

nohup java -jar $REPOSITORY/$JAR_NAME &

```









