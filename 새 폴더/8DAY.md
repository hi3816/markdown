rpm 
    -ivh
    -e
의존성이 중요하다
=================================
OpenSSL 설치방법

1. 설치 전 필수 설치
yum install perl gcc -y

2. openssl다운로드 사이트 접속
https://www.openssl.org/source/

아래로내리다보면 링크주소 복사
ex ) openssl-1.1-tar.gz

#설치에 앞서 yum업데이트
yum -y update
tar -xvzf openssl-1.1.1q.tar.gz //압축푹기
cd openssl-1.1.1q/ //이동

#묶음 해제
tar -xvzf openssl-1.1.1ㅣ.tar.gz

#openssl 디렉토리 이동
cd opennssl-1.1.1l (이 파일이름이 아닐 수 있음 tab으로 확인해보길)

#configure를 통해소스파일에 환경설정 적용
./config --prefix=/usr/local/ssl --openssldir=/usr/local/ssl shared

#make 파일로 소스를 컴파일하고 make install로 설치 진행
make && make install

#openssl-1.1.1.conf 설정등록
vi /etc/ld.so.conf.d/oepnssl-1.1.1l.conf (1.1.1~뒤에는 바뀌었을수도있음..)
-----------------------
/usr/local/ssl/lib
-----------------------

#설정등록 확인
ldconfig -v

# 접근성을 위해 등록
$ ln -s /usr/local/ssl/lib/libssl.so.1.1 /usr/lib64/libssl.so.1.1
$ ln -s /usr/local/ssl/lib/libcrypto.so.1.1 /usr/lib64/libcrypto.so.1.1


# 설치한 버전을 주로 사용되게 등록
$ mv /usr/bin/openssl /usr/bin/openssl1.0.2
$ ln -s /usr/local/ssl/bin/openssl /usr/bin/openssl


# 설치 및 등록한 openssl 버전 확인
$ openssl version

# wget 설치
$ yum install wget -y


# 컴파일러 모음 설치
$ yum install gcc-c++ -y


# expat-devel 설치 (expat을 가지고 XML 응용 프로그램을 개발하는데 필요한 라이브러리)
$ yum install expat-devel -y

우선은 apache설치에 앞서, pcre를 설치합니다.

# 설치할 디렉토리 생성
$ mkdir -p /usr/local/src/apache


# 설치할 디렉토리로 이동
$ cd /usr/local/src/apache


# wget 으로 pcre 다운로드
$ wget https://ftp.pcre.org/pub/pcre/pcre-8.43.tar.gz --no-check-certificate


# 묶음 해제
$ tar -xvzf pcre-8.43.tar.gz


# pcre디렉토리로 이동
$ cd pcre-8.43

# configure를 통해 소스파일에 환경설정을 적용
$ ./configure


# make 파일로 소스를 컴파일하고 make install로 설치진행
$ make && make install

=================================
make && make install
