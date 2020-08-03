---
title:  "JSP project 생성"
excerpt: "2020웹서비스 개발 캠프"
toc: true
toc_sticky: true

categories:
  - gitBlog
tags:
  - GitHub
  - Blog

last_modified_at: 2020-08-03
---




## 1. JSP 개발환경 설치하기.



JDK 8, Tomcat 8.5, Spring Tool Suite 4, Maven3 을 먼저 설치해보자.







1. JDK

[JDK](https://www.w3schools.com/js/js_validation.asp)


여기 들어가서 linux/macOS/Windows 중 자신에게 맞는걸 선택한 후 다운로드 받는다.

설치 후 windows 검색창에서 `cmd 명령 프롬포트`를 찾아 설치 확인을 하는데,

`java -version`   라고 입력했을 때, 이런 화면이 나와야 한다.


![poco](/assets/images/jsp_proj/jdk설치.GIF)





2. Tomcat

JDK 8이상 [Tomcat](https://tomcat.apache.org/download-80.cgi)


![poco](/assets/images/jsp_proj/톰캣.GIF)


화살표 표시되어있는 부분 중 하나를 선택해서 다운받으면 된다.


그런뒤 압축을 풀어 해당 폴더를 자신이 편한 위치에 옮기면 된다.


여기선 따로 설치할 필요가 없다. 압축폴더를 풀기만 하면 된다.







3. Spring Tool Suite

[STS](https://spring.io/tools)

여기에서 파일을 다운받으면 된다.


다운로드가 완료되면, 본인이 설치할 위치를 선택해 압축파일을 푼 뒤 설치프로그램을 통해 설치하면 된다.





4. Maven3

[Maven](http://maven.apache.org/download.cgi)

여기서 **Binary zip archive - Link** 부분을 눌러서 다운받으면 된다.

그리고 나서 본인이 설정한 위치에서 압축폴더를 풀어야 한다.


> C:project/apache-maven-3.6.3

나는 여기 위치로 옮겼다.


그리고 여기서 중요한 것이, **환경변수 (PATH)** 설정.


원래 환경변수설정을 하는 방법이 보통 있는데, 나는 아무리 해도 어딘가에 실수가 있었던지? 되지 않았다.


그래서 결국 한 방법은,


`cmd 명령 프롬포트` 여기서 직접 환경변수를 설정해주면 된다.


**Unix-based** operating systems (Linux, Solaris and Mac OS X)
      > export PATH=/usr/local/apache-maven-3.x.y/bin:$PATH

**Windows**
      > set PATH="c:\program files\apache-maven-3.x.y\bin";%PATH%

![poco](/assets/images/jsp_proj/톰캣설치2.GIF)


> mvn -version

을 입력했을 때, 자신의 컴퓨터에 설치된 파일의 정보가 나와야 정상이다.



제일 위는, 환경변수 설정이 제대로 되지 않았을 때 나오는 결과.

중간은 직접 환경변수를 설정한 것.

마지막은 성공적으로 설치되었을 때 나오는 결과.








## 새로운 프로젝트 만들기

프로그램 준비가 다 되었다면, 이젠 새로운 프로젝트를 만들어보아야 한다.


아까 설치했던 **spring tool suite** 에 들어간다.



1. **file/new/[Web] - [Dynamic Web Project]**  으로 새로운 프로젝트를 만들어 준다.


2. 아까 설치한 maven 프로젝트로 변환해주기 위해, 프로젝트에서 우측클릭 후, **configure / convert to maven project** 를 클릭한다.


3. 새로운 프로젝트 폴더 속 webContent 폴더에 **index.jsp** 파일을 만든다.


4. Tomcat 라이브러리 추가를 해야 한다.

![poco](/assets/images/jsp_proj/톰캣서버설치.GIF)

화면 하단부쪽에서 server 글씨를 찾아, 아래 공백 칸에서 **우측클릭-server-new**





![poco](/assets/images/jsp_proj/톰캣서버설치2.GIF)

이렇게 Server name을 설정 후, Next를 누른다.



그리고 왼쪽 **Available** 의 서버이름을 **configure** 으로 add 해준다.그리고 Finish.





![poco](/assets/images/jsp_proj/톰캣서버설치3.GIF)

아래 Server 에서 방금 자신이 만든 server 이름을 더블클릭하면 이런 화면이 뜬다.

**Modules-path 선택-edit** 에서 기존 Path의 내용을 지운 뒤 Ok-저장.



5. 아까 만든 index.jsp 파일에 내용 입력 후, 아랫쪽 칸에서 톰캣을 구동시킨다. (서버명 더블클릭-start)


그리고 크롬에서

>http://localhost:8080

을 입력하면, 본인이 입력한 내용이 뜨게 된다.







## github와 연동


1. 기존 github 아이디로 로그인 해, new repository 생성.


**프로젝트명-Team-Share Project**



체크박스 클릭 후, create repository로 로컬저장소를 만든다.






2. 새로 만든 repository의 주소를 복사한뒤, 'git repository' 검색 후 방금 만든 저장소 이름을 더블클릭.

![poco](/assets/images/jsp_proj/깃연동.GIF)

3. create remote


4. configure-push


5. Source Git Repository 에서 주소 붙여넣기후 Save


6. 그런 뒤, git push commit을 통해 올리면 완성!



![poco](/assets/images/jsp_proj/깃연동-2.GIF)
