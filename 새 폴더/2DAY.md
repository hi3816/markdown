##리눅스란?

##### 하드웨어란?
>컴퓨터나 컴퓨터에 붙어있는 주변 장치들
>```
>->컴퓨터 본체.cpu,하드디스크 마우스모니터 등
>
>```

##### 소프트웨어란?

>실체가 x,
>컴퓨터 프로그램
>```
>->마우스를 움직이게 하는 프로그램
>->모니터를 출력시켜주는 프로그램
>```

##### 운영체제란???

> 1. 컴퓨터 시스템의 자원
> 2. 사용자가 컴퓨터를 편리하고 효과적으로 제공하는 여러 프로그램의 모임<br>
>```
>운영체제는 컴퓨터 사용자와 컴퓨터 하드웨어간의 인터페이스로 동작하는 시스템 소프트웨어의 일종
>다른응용 프로그램이 유용한 작업을 할 수 있도록 환경을 제공한다.
>```
>![Alt text](/%EC%9D%B4%EB%AF%B8%EC%A7%80%ED%8C%8C%EC%9D%BC/%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C.jpg)

##### 운영체제의 종류?
>![Alt text](/%EC%9D%B4%EB%AF%B8%EC%A7%80%ED%8C%8C%EC%9D%BC/%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C%EC%A2%85%EB%A5%981.jpg)
>![Alt text](/%EC%9D%B4%EB%AF%B8%EC%A7%80%ED%8C%8C%EC%9D%BC/%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C%EC%A2%85%EB%A5%982.jpg)

##### 리눅스를 배우는 이유
>내가 만든 것들을
웹서버로 올려보자

##### 리눅스의 역사
>1969년 MIT, AT&T 벨 연구소의 켄 톰슨(Ken Thompson), 초기 형태의 UNIX 개발
핀란드 헬싱키 대학의 **리누스 토발즈(Linus Torvalds)** 가 
Minix의 커널 소스를 고쳐 GNU 시스템에 적합한 커널을 개발하였다.

##### 리눅스는 오픈소스 기반

> **오픈소스란?**<BR>
> 말 그대로 오픈된 소스 =
>누구나 공짜로 가져다 쓸 수 있을 뿐만 아니라 그 코드도 마음껏 들여다 볼 수 있고 원하는대로 조립, 재조립을 할 수 있습니다.

##### window나 MAC이 아닌 리눅스를 쓰는 이유

>1. 윈도우의 경우 **유료 스프트웨어** 라는 점 즉, 돈이 많이 든다<BR>
> 2. 일반적인 개발자로서는 개발해보기위한 진입장벽이 높다는 단점<BR>
>반면 리눅스는 무료이기 때문에 얼마든 서버에 깔아서 맘껏 사용이 가능.
>필요에 따라 개조해 쓰는것도 자유기 떄문에 이점이 많다.<BR>
> 3. 서버로 운영하는데에 있어선 끝판왕<BR>

##### 리눅스의 구조
>![Alt text](/%EC%9D%B4%EB%AF%B8%EC%A7%80%ED%8C%8C%EC%9D%BC/%EB%A6%AC%EB%88%85%EC%8A%A4%EA%B5%AC%EC%A1%B0.jpg)
> 하드웨어 커널 쉘 응용프로그램으로 구성 되어 있습니다.
> | Header One | Header Two |
> |:--------   | :--------- |
> | HW  | 컴퓨터의 전자 기계장치의 몸체자체   |
> | 커널   | 하드웨어와 소프트웨어의 연결다리   |
>| 쉘   | 사용자를 연결해주는 인터페이스, <BR>검은배경에 흰색글씨로 이루어진 창   |
> | 응용프로그램   | 리눅스 내부의 응용프로그램   |

##### 리눅스의 개요

>|||
>|:-|:-|
>|**/(최상위 디렉토리)**|-리눅스 상에 존재하는 모든 파일과 디렉토리의 시작.<BR>-최상위에 위치하는 디렉토리
>|**/BOOT**|-부팅과정에서 필요한 정보파일들의 경로 <BR> BOOT partition설정시에는 1GB 이상 용량을 설정|
>|**/bin(binary)**|-user/bin<br> -*exe(실행파일)<br>-기본적인 명령어 실행파일들의 경로|
>|**/sbin(system binary)**|-*.exe(실행파일)<br>-시스템 운영, 관리에 필요한 명령어 경로<br>-관리자 명령어|
>|**/root**|-관리자(root)의 home directory <br># home directory : 계정에 대한 정보를 저장하고 잇는 디렉토리|
>|**/home**|-일반 사용자들의 home directory가 저장되는 경로 <br>#윈도우는 관리자, 사용자가 같은곳에 위치<br>#리눅스는 관리자, 사용자가 서로다른곳에 위치|
>|**/dev(device)**|-각종 장치파일들이 저장되는 경로<br> #리눅스 시스템은 장치를 장치로서 인식하는것이 아니라 장치파일로 인식|
>|**/etc**|-서버 설정에 필요한 모든 정보파일들의 경로(시스템 관련)|
>|**/usr**|-리눅스 응용프로그램 기본 설치 경로<br>#윈도우의 프로그램 파일 폴더 유사<br>-대용량 데이터 보관 용도로도 사용|
>|**/var**|-로그(log)파일들의 경로|


##### 리눅스의 종류
>리눅스는 unix를 바탕으로 개발되었기 때문에 **슬렉웨어계열, 데비안 계열, 레드햇 계열** 등등 수많은 리눅스가 존재
>![Alt text](/%EC%9D%B4%EB%AF%B8%EC%A7%80%ED%8C%8C%EC%9D%BC/%EB%A6%AC%EB%88%85%EC%8A%A4%20%EC%A2%85%EB%A5%98.jpg)
>![Alt text](/%EC%9D%B4%EB%AF%B8%EC%A7%80%ED%8C%8C%EC%9D%BC/%EB%A6%AC%EB%88%85%EC%8A%A4%EC%A2%85%EB%A5%982.jpg)