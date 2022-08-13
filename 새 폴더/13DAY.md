# mysql설치

    yum list installed | grep mysql
    //설치된 mysql 확인

    yum remove -y mysql80-community-*
    //설치된 mysql 삭제 (이름확인하고 삭제할것)

    yum repolist enabled | grep "mysql"*
    //가능한 mysql확인

    yum respository
    // respository는 packa0ge를 모아놓은 저장소

    yum install -y https://dev.mysql.com/get/mysql80-community-release-el7-5.noarch.rpm
    //mysql설치

    yum repolist enabled | grep "mysql.*"
    //yum repolist(현재 확성화된 yum respository 목록을 확인한다)

    yum install -y mysql-server
    //mysql서버 설치

    mysqld -V
    //버전확인

    systemctl enable mysqld
    //

    systemctl start mysqld

    systemctl status mysqld


    grep "temporary password" /var/log/mysqld.log
    //임시 비밀번호 확인   ```,1<glqoTIg3y```

    mysql -u root -p
    //root계정접속 확인했던 비밀번호 입력

    ALTER USER 'root'@'localhost' IDENTIFIED BY "dlwlgP123!";
    //비밀번호 설정

    패스워드 정책은 구글링하면 나온다 정책을 바꾼 후 비밀번호를 설정해도 좋다 (검색어 : mysql비밀번호조합설정)


# 외부접속 허용
    use mysql;

    select host, user from user;

    create user 'root'@'192.168.56.1' identified by "dlwlgP123!";

    grant all privileges on *.*to 'root'@'192.168.56.1';
    
    flush privileges;

    구글로 공인아이피 검색 => 1.218.82.203

        create user 'root'@'1.218.82.203' identified by "dlwlgP123!";

        grant all privileges on *.*to 'root'@'1.218.82.203';
    
        flush privileges;

# mysql 기본캐릭터셋 설정

    vi /etc/my.cnf

    [client]
    default-character-set = utf8mb4

    [mysql]
    default-character-set = utf8mb4

    [mysqld]
    character-set-client-handshake = FALSE
    character-set-server = utf8mb4
    collation-server =utf8mb4_unicode_ci

    systemctl restart mysqld
    mysql -u root -p


    *****ppt mysql설치 참고********

# 배포하기

    *선생님이 주신 sample 의 C:\Users\이지혜\Downloads\sample\pangpany_erp\build\libs   에 있는 root.war을 복붙할거임

    터미널을 키고
    
    cd /usr/local/apache-tomcat-8.5.69/webapps
    //아파치 톰캣 이동

    rm -rf ROOT.war
    //기존 root.war을 삭제
    
    ((여기서 윈도우에 있는 root.war을 끌어서 넣어주고
    창이 뜨면 pwd로 조회한 현재 경로를 입력해 옮긴다))

    jar xvf ROOT.war
    //압축해제


# 이클립스에서 import하기

    이클립스 스프링을 킨후 프로젝트 목록에서 import중 gradle 폴더의 그레이들 프로젝트 클릭후 넥

    주절주절 넥

    프로젝트 루트 디렉토리에서 erp 넣은 후 넥

    파란글시 컨피규어클릭후 버전 6.6(다를수도) 후 어플리 넥 넥

    피니쉬

    *안됨

    
