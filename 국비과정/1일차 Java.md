# 개발환경구축 

## 자바언어로 개발 할수있는 도구설치
* 자바언어 version
```
JAVA 8 : JDK1.8 
JDK : Java Developmentment Kit (자바개발도구)
```
* 라이센스
  * oracle JDK
  * open   JDK

JDK - 자바명령어 집합체, 개발목적으로 지원하는 S/W <br>
JRE - 자바프로그램을 실행시켜주는 환경적인 도구

## JAVA Version 체크 
명렁프롬프트 실행 -> cmd -> " java -version , javac -version "
```
ex) java version "1.8.0_271"
    javac 1.8.0_271
```
<br>

## 환경변수 등록
* path : 특정폴더의 명령어를 위치에 상관없이 사용이 가능하게 하도록 해당 명령어를 가지고 폴더를 등록
```
시스템 변수 - 새로만들기 ex)
JAVA_HOME C:\dev\programFiles\Java\jdk1.8.0_271
path 선택 -> 편집 -> 새로만들기 : %JAVA_HOME%\bin
시스템변수 - path - 편집 - jdk  
```
<br>

## 통합개발환경도구(IDE) : 개발툴(편집기)
* 표준 : elipse (무료)
```
이클립스 실행이 안될 경우 여러 원인 중에 대부분은 JDK 환경변수 등록에 문제가 많다.
```
* 상업 : inteliJ (유료)
  
## Eclipse 환경설정
* 메모리 상태
    * Window - preferences - 좌측 General에서 오른쪽 3번째 Show heap Status 체크하면 확인가능
* 인코딩 설정
    * Window - preference - enc검색 - General - workspace - Other:UTF-8 (Apply:적용) 
    * Window - preference - General - web - CSS&HTML&JSP flies - Encoding : ISO 10646/Unicode(UTF-8) - Apply(설정)
```
인코딩은 생성된 똑같은 방식으로 저장 불러오기해야한다.
툴로 소스를 열면 한글데이터가 깨져보이는 경우 인코딩방식 설정이 다른방식이기 때문
ex) ANSI 숫자-영어 : 1Byte , 한글 : 2Byte
     UTF 숫자-영어 : 1Byte , 한글 : 3Byte 
```
 
