## 아파치설치 ##

usr/local/src 의 download apache tomcat8 다 지워주기
yum으로 아파치 설치가 가능하다

    yum -y install java-1.8.0-openjdk-devel.x86_64
    //yum으로 자바 설치


    javac -version
    //자바버전 확인

    ps -ax | grep httpd
    //현재 실행중인 프로세스의 목록을 보는 명렁어
    -a 터미널에서 실행한 프로세스의 정보를 출력
    -x 실행중인 모든 프로세스의 정보를 출력

    yum list installed | grep httpd
    //설치가능한 패키지를 조회하기위함

    yum -y install httpd
    //설치함

    firewall-cmd --permanent --zone=public --add-port=80/tcp
    //방화벽 80번포트뚫기

    firewall-cmd --reload
    //포트를 뚫어주면 reload단계가 필요하다

    systemctl start httpd
    //아파치 실행, 포트포워딩에 ip를 적지않은 상태라면 localhost로 확인이 가능하다

## 톰캣설치 ##

    yum install wget
    //wget 설치

    cd /usr/local
    //설치할 경로로 들어간다

    wget http://archive.apache.org/dist/tomcat/tomcat-8/v8.5.69/bin/apache-tomcat-8.5.69.tar.gz
    //톰캣을 설치해준다


    tar -zxf apache-tomcat-8.5.69.tar.gz
    /압축해제

    firewall-cmd --permanent --add-port=8080/tcp
    firewall-cmd --permanent --add-port=22/tcp
    firewall-cmd --permanent --add-port=8443/tcp
    firewall-cmd --permanent --add-port=8009/tcp
    firewall-cmd --reload
    //포트뚫고 리로드해주기

    cd /usr/local/apache-tomcat-8.5.69/bin
    //압축푼곳의 bin으로 들어감
    
    ll
    //startup.sh파일 확인
    
    ./startup.sh
    //실행

# 아파치 톰캣 연동

    # yum -y install gcc gcc-c++ httpd-devel
    // gcc, gcc-c++ httpd-devel 설치

    # cd /usr/local
    //커넥터 위치 잡기
    
    # wget http://mirror.navercorp.com/apache/tomcat/tomcat-connectors/jk/tomcat-connectors-1.2.48-src.tar.gz
    //jk 커넥터 다운

    # tar -zxf tomcat-connectors-1.2.48-src.tar.gz
    //커넥터 압축해제
    
    # cd tomcat-connectors-1.2.48-src/native/
    //커넥터의 native로 접속

    # ./configure --with-apxs=/usr/bin/apxs
    //configure는 소스파일에 대한 환경설정을 해주는 명령어다.(configure뒤에 옵션을 넣음) 서버환경에 맞쳐 makefile을 생성해주는 과정이다.
    출처: https://itdexter.tistory.com/325 [IT_Dexter:티스토리]

    # make | make install
    //make해주기
    ```
    make는 소스를 컴파일 하는 것이다. 컴파일이란 것은 소스파일을 사용자가 실행 가능한 파일로 만들어 주는 과정을 말한다. make 과정이 끝나고 나면 설치파일(Setup 파일 같은 것)이 생성된 상태라고 볼 수 있다.여기서 중요한 것은 make에게 어떤 프로그램을 컴파일하고 링크해야 하는지 그 방법을 설명한 것이 makefile이다.

    make install은 make를 통해 만들어진 설치파일(setup)을 설치를 하는 과정이다. 한마디로 build된 프로그램을 실행 할 수 있게 파일들을 알맞은 위치에다가 복사를 한다. make dep 이란 것은 의존성 검사라고 하는 것인데 커널 컴파일을 하기 전에 이것들의 소스들에 문제가 있는지 검사하는 것이다. ( 설치에 필요한 것들이 제대로 있나 확인하는 것)
    출처: https://itdexter.tistory.com/325 [IT_Dexter:티스토리]
    ```

    # vi /etc/httpd/conf/httpd.conf
    ```
    LoadModule jk_module modules/mod_jk.so      //모듈위치
    <VirtualHost *:80>
        ServerName localhost
        JkMount /* tomcat
        //모든 url요청에서 서블릿 관련 처리가 필요하다면 workers.properties파일에 명시된 tomcat으로 넘기겠다는 의미
    </VirtualHost>

    <IfModule mod_jk.c>
        JkWorkersFile conf/workers.properties   //worker.properties파일위치
        JkShmFile run/mod_jk.shm                
        JkLogFile logs/mod_jk.log               //로그파일위치
        JkLogLevel info                         //로그레벨
        JkLogStampFormat "[%y %m %d %H:%M:%S]"
    </IfModule>
    ```
    //conf에서 맨아래에 위 내용을 적어준다

    # vi /etc/httpd/conf/workers.properties
    ```
    worker.list=tomcat
    worker.tomcat.port=8009
    worker.tomcat.host=localhost
    worker.tomcat.type=ajp13
    worker.tomcat.lbfactor=1
    ```
    (l이랑 i가 오타가많이난다 주의)

    # vi /usr/local/apache-tomcat-8.5.69/conf/server.xml
    116번째줄 부분 주석해제
    ```
    <Connector protocol="AJP/1.3"
                address="0.0.0.0"
                secretRequired="false"
                port="8009"
                redirectPort="8443" />
    ```
    
    # cd /usr/local/apache-tomcat-8.5.69/bin/
    # ./shutdown.sh
    # ./startup.sh
    //톰캣 경로 이동후 셧다운했다 다시 실행시켜준다

    # systemctl restart httpd
    //아파치도 다시 실행시켜주기
    
    //localhost를 입력해서 톰캣이 뜨는지 확인해준다 나온다면 성공 

    *******아파치 톰캣연동 관련 링크 (윈도우기준이지만 설치방법은 크게 다르지않음)********
    https://joont.tistory.com/55


     # vi /etc/httpd/conf/httpd.conf
    ```
    LoadModule jk_module modules/mod_jk.so      //모듈위치
    <VirtualHost *:80>
        DocumentRoot "/usr/local/src/apache/htdocs/"
        ServerName 192.168.56.1
        JkMount /*.jsp tomcat
        JkMount /servlet/* tomcat1
        //모든 url요청에서 서블릿 관련 처리가 필요하다면 workers.properties파일에 명시된 tomcat으로 넘기겠다는 의미
    </VirtualHost>