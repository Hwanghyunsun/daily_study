# jdk 설치 및 설정
## 1. jdk 다운로드
1. jdk를 다운로드 하기 위해 위의 주소로 접속한다.
https://www.oracle.com/java/technologies/javase-downloads.html      


2. JAVA 8 버전의 JDK Download를 클릭한다. 
<img src="https://user-images.githubusercontent.com/53217674/76597691-70a0f680-6544-11ea-80f0-d6a42056736c.png"></img><br/>


3. 운영체제에 맞는 파일을 다운로드한다. 여기에서는 윈도우 64비트 파일을 다운로드하기로 한다.
<img src="https://user-images.githubusercontent.com/53217674/76597693-71398d00-6544-11ea-8cba-c27bb1f97a3f.png"></img><br/>


## 2. jdk 설치
1. 다운로드 받은 파일을 실행하여 next버튼을 누른다. 
<img src="https://user-images.githubusercontent.com/53217674/76597696-71d22380-6544-11ea-9d39-26932e20174e.png"></img><br/>

2. Development Tools를 설치하면 된다. 일반적으로 기본 폴더에 설치해도 상관없으나, 어떤 프로그램은 공란을 인식하지 못하는 프로그램(특히 리눅스 호환관련)이 있어서 가능하면 공란이 없고 설치 경로를 짧게 잡는 것이 유리하다. 그렇기 때문에 Program Files를 지우고 next를 누른다.

<img src="https://user-images.githubusercontent.com/53217674/76597697-71d22380-6544-11ea-8a0d-2a80365ce526.png"></img><br/>

3. jre은 특별히 문제가 없으므로 기본 설치 폴더에서 다음을 눌러 진행한다.
<img src="https://user-images.githubusercontent.com/53217674/76597698-726aba00-6544-11ea-86c0-86abc09d73f0.png"></img><br/>

4. Close를 눌러 설치를 완료한다.
<img src="https://user-images.githubusercontent.com/53217674/76597702-73035080-6544-11ea-979c-02ee8f4a4c1d.png"></img><br/>


## 3. 환경변수 설정
### 환경변수란?
환경변수는 프로세스가 컴퓨터에서 동작하는 방식에 영향을 미치는 동적인 값들을 말한다.            

환경변수에는 두 가지 종류가 있다.
```
사용자 변수 : OS 내의 사용자별로 다르게 설정가능한 환경변수

시스템 변수 : 시스템 전체에 모두 적용되는 환경변수
```

### Path란?
자주 쓰는 프로그램의 경로가 등록되어있는 곳으로 그 경로에 존재하는 프로그램을 어떠한 장소에서든 실행시킬 수 있도록 해주는 것이다.

### Path 설정
JAVA 컴파일러와 클래스 파일 로더 등을 아무 위치에서나 사용하고 싶다면 Path에 이 프로그램들이 있는 경로를 지정해줘야 한다.
JAVA의 프로그램들을 사용하기 위해 jdk 폴더 안에 있는 bin 폴더를 Path에 등록시켜줘야 한다.

1. 윈도우 버튼 옆의 돋보기를 클릭하여 환경 변수를 입력 후 **시스템 환경 변수 편집**을 누른다.
<img src="https://user-images.githubusercontent.com/53217674/76597703-739be700-6544-11ea-969b-ed184e14d630.png"></img><br/>

2. 시스템 변수에서 **새로 만들기** 버튼을 누른다.
<img src="https://user-images.githubusercontent.com/53217674/76597705-739be700-6544-11ea-9389-d6e6832cf8a8.png"></img><br/>

3. 새 시스템 변수 창이 뜨면 **변수 이름**에 JAVA_HOME을 입력하고 **변수 값**에 JAVA가 설치된 디렉토리를 입력 후 확인 버튼을 누른다. 이는 JAVA 프로그램의 홈 경로를 말한다.
<img src="https://user-images.githubusercontent.com/53217674/76597706-74347d80-6544-11ea-8aec-4c1ad785fe29.png"></img><br/>

4. 다음은 Path를 설정한다. 시스템 변수 안의 **Path**를 클릭하고 편집 버튼을 누른다.
<img src="https://user-images.githubusercontent.com/53217674/76597707-74347d80-6544-11ea-8043-95adcc21ecc6.png"></img><br/>

5. 환경 변수 편집 창이 열리면 **새로 만들기**를 누르고 JAVA 설치 경로 밑의 bin까지 입력 후 확인 버튼을 누른다.          
;%JAVA_HOME%bin;와 같이 입력 하는 것도 가능하다.(;는 구분 문자)
<img src="https://user-images.githubusercontent.com/53217674/76599332-215cc500-6548-11ea-9869-7576584f598a.png"></img><br/>

6. 마지막으로 CLASSPATH를 설정한다. 이는 컴파일하거나 실행 시 참조하는 클래스나 라이브러리 위치를 지정하는 것이다. 시스템 변수의 **새로 만들기** 버튼을 누른다.
<img src="https://user-images.githubusercontent.com/53217674/76597705-739be700-6544-11ea-9389-d6e6832cf8a8.png"></img><br/>

7. 새 시스템 변수 창이 뜨면 **변수 이름**에 CLASSPATH **변수 값**에.;%JAVA_HOME%\lib\tools.jar를 입력하고 확인 버튼을 누른다.

## 4. 확인 과정
### 버전 확인하기
1. cmd 창을 열고 java -version을 입력한다. 
<img src="https://user-images.githubusercontent.com/53217674/76597712-7565aa80-6544-11ea-852e-a570d30fb8aa.png"></img><br/>

2. 엔터를 치면 현재 설치된 버전이 출력된다.
<img src="https://user-images.githubusercontent.com/53217674/76597713-7565aa80-6544-11ea-9a52-0e27467e1e35.png"></img><br/>


### 컴파일 명령
1. cmd 창에서 javac를 입력한다.
<img src="https://user-images.githubusercontent.com/53217674/76597713-7565aa80-6544-11ea-9a52-0e27467e1e35.png"></img><br/>

2. 엔터를 치면 아래와 같이 출력된다. 여기서 오류가 나면 환경변수의 Path를 재확인한다.
<img src="https://user-images.githubusercontent.com/53217674/76597717-75fe4100-6544-11ea-8776-4a7f7acf9985.png"></img><br/>