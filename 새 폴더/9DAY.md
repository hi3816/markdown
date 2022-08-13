
#아파치 설치

pwd                             //내위치 확인

cd /usr/local/src/apache        //설치할 경로

https://dlcdn.apache.org/httpd/     //여기로 들어가서
	https://dlcdn.apache.org/httpd/httpd-2.4.54.tar.gz      /이걸 다운

https://apache.mirror.cdnetworkds.com/apr/      //여기로 들어가서
	http://apache.mirror.cdnetworks.com/apr/apr-util-1.6.1.tar.gz                           //이걸다운
	http://apache.mirror.cdnetworks.com/apr/apr-1.6.5.tar.gz                            //이걸다운

tar -xvzf apr-1.6.5.tar.gz      //압축해제
tar -xvzf apr-util-1.6.1.tar.gz //압축해제
ll                              
tar -xvzf httpd-2.4.54.tar.gz   //압축해제

--------------------------


mv apr-1.6.5 httpd-2.4.54/srclib/apr
                                //압축해제했던 apr을 httpd-2.4.5~
mv apr-util-1.6.1 httpd-2.4.54/srclib/apr-util
                                //압축해제했던 apr-util을 ~
pwd

./configure --prefix=/usr/local/src/apache --enable-so --enable-ssl=shared --with-ssl=/usr/local/ssl --enable-rewrite


ppt대로 하다가 방화벽때문에 막히는경우가 있다.
    firewall-cmd --add-port=80/tcp --zone=public --permanent
    를 입력해서 80포트로 뚫어주자


내 아이피 확인
ip addr         //inet







------------------
mskim centos미니 새로 깔기

cd /etc/sysconfig/network-srcripts
vi ifcfg-enp0s3

재부팅

yum update -y

yum install net-tools -y
yum install openssh-server -y
yum install openssh-client -y

