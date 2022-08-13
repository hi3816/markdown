톰캣 설치

# java 설치

#  open-jdk 1.8 설치
$ yum install -y java-1.8.0-openjdk
$ yum install -y java-1.8.0-openjdk-devel

# 설치된 실제경로 검색
$ readlink -f /usr/bin/java

# 환경변수 등록
$ vi /etc/profile
----------------------------------------------------------------------------------------
JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.302.b08-0.el7_9.x86_64
PATH=$PATH:$JAVA_HOME/bin
CLASSPATH=$JAVA_HOME/jre/lib:$JAVA_HOME/lib/tools.jar

export JAVA_HOME PATH CLASSPATH
----------------------------------------------------------------------------------------
[마지막 줄에 추가]


# 등록한 환경변수 반영
$ source /etc/profile


# 다운로드할 디렉토리로이동
$ cd /usr/local/download


# Tomcat 8.5 설치
$ wget http://archive.apache.org/dist/tomcat/tomcat-8/v8.5.27/bin/apache-tomcat-8.5.27.tar.gz


# 압축 해제
$ tar zxvf apache-tomcat-8.5.27.tar.gz


# 압축 해제한 톰캣을 /usr/local/tomcat8 경로로 이동
mv apache-tomcat-8.5.27 /usr/local/tomcat8




--------------------메모장---------
vi /etc/firewalld/zones/public.xml //뚫은 포트를 알 수 있다

firewall-cmd --permanent --zone=public -add-port=8080/tcp

--------------수업내용------------------------
########
#openssl#
########
yum install wget -y
yum install perl gcc -y

cd /usr/local/src
wget https://www.openssl.org/source/openssl-1.1.1l.tar.gz --no-check-certificate
tar -xvzf openssl-1.1.1l.tar.gz
cd openssl-1.1.1l
./config --prefix=/usr/local/ssl --openssldir=/usr/local/ssl shared
make && make install




vi /etc/ld.so.conf.d/openssl-1.1.1l.conf
```
/usr/local/ssl/lib
```
ldconfig -v

ln -s /usr/local/ssl/lib/libssl.so.1.1 /usr/lib64/libssl.so.1.1
ln -s /usr/local/ssl/lib/libcrypto.so.1.1 /usr/lib64/libcrypto.so.1.1



mv /usr/bin/openssl /usr/bin/openssl1.0.2
ln -s /usr/local/ssl/bin/openssl /usr/bin/openssl

openssl version



#######
#apache#
#######
yum install gcc-c++ -y
yum install expat-devel -y

// sudo yum install -y expat expat-devel expat-static


mkdir -p /usr/local/src/apache
cd /usr/local/src/apache
wget http://ftp.cs.stanford.edu/pub/exim/pcre/pcre-8.45.tar.gz --no-check-certificate
tar -xvzf pcre-8.45.tar.gz
cd pcre-8.45
./configure
make && make install

cd ../

wget https://dlcdn.apache.org/httpd/httpd-2.4.54.tar.gz --no-check-certificate
wget http://apache.mirror.cdnetworks.com/apr/apr-1.6.5.tar.gz
wget http://apache.mirror.cdnetworks.com/apr/apr-util-1.6.1.tar.gz


tar -xvzf httpd-2.4.54.tar.gz
tar -xvzf apr-1.6.5.tar.gz
tar -xvzf apr-util-1.6.1.tar.gz

mv apr-1.6.5 httpd-2.4.54/srclib/apr
mv apr-util-1.6.1 httpd-2.4.54/srclib/apr-util


cd httpd-2.4.54
./configure --prefix=/usr/local/src/apache --enable-so --enable-ssl=shared --with-ssl=/usr/local/ssl --enable-rewrite
make && make install


vi /usr/lib/systemd/system/httpd.service
```
[Unit]
Description=The Apache HTTP Server

 
[Service]
Type=forking
PIDFile=/usr/local/src/apache/logs/httpd.pid
ExecStart=/usr/local/src/apache/bin/apachectl start
ExecReload=/usr/local/src/apache/bin/apachectl graceful
ExecStop=/usr/local/src/apache/bin/apachectl stop
KillSignal=SIGCONT
PrivateTmp=true

[Install]
WantedBy=multi-user.target
```

systemctl start httpd

##############
###자바설치####
##############

yum install -y java-1.8.0-openjdk
yum install -y java-1.8.0-openjdk-devel

readlink -f /usr/bin/java

vi /etc/profile

JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.342.b07-1.el7_9.x86_64
PATH=$PATH:$JAVA_HOME/bin
CLASSPATH=$JAVA_HOME/jre/lib:$JAVA_HOME/lib/tools.jar

export JAVA_HOME PATH CLASSPATH


source /etc/profile




##############
###tomcat설치###
###############
mkdir /usr/local/download
cd /usr/local/download
wget http://archive.apache.org/dist/tomcat/tomcat-8/v8.5.27/bin/apache-tomcat-8.5.27.tar.gz
tar zxvf apache-tomcat-8.5.27.tar.gz
mv apache-tomcat-8.5.27 /usr/local/tomcat8

vi /usr/local/tomcat8/conf/server.xml
69번줄  URIEncoding="UTF-8" 추가


vi /etc/profile


JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.342.b07-1.el7_9.x86_64/jre/bin/java
CATALINA_HOME=/usr/local/tomcat8
CLASSPATH=$JAVA_HOME/jre/lib:$JAVA_HOME/lib/tools.jar:$CATALINA_HOME/lib-jsp-api.jar:$CATALINA_HOME/lib/servlet-api.jar
PATH=$PATH:$JAVA_HOME/bin:/bin:/sbin
export JAVA_HOME PATH CLASSPATH CATALINA_HOME

source /etc/profile

/usr/local/tomcat8/bin/startup.sh

ps -ef|grep tomcat8

yum install net-tools -y
netstat -tln
wget http://localhost:8080/


vi /etc/systemd/system/tomcat8.service


# Systemd unit file for tomcat
[Unit]
Description=Apache Tomcat Web Application Container
After=syslog.target network.target

[Service]
Type=forking

Environment="JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.342.b07-1.el7_9.x86_64/jre/bin/java"
Environment="CATALINA_HOME=/usr/local/tomcat8"
Environment="CATALINA_BASE=/usr/local/tomcat8"
Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"
Environment="JAVA_OPTS=-Djava.security.egd=file:///dev/urandom"

ExecStart=/usr/local/tomcat8/bin/startup.sh
ExecStop=/usr/local/tomcat8/bin/shutdown.sh

User=root
Group=root
UMask=0007
RestartSec=10
Restart=always

[Install]
WantedBy=multi-user.target


systemctl daemon-reload
systemctl enable tomcat8
systemctl start tomcat8


systemctl enable tomcat8.service
systemctl list-unit-files --type service |grep tomcat8


http://192.168.9.99:8080/


####################
###tomcat apache연동###
####################

wget http://mirror.apache-kr.org/tomcat/tomcat-connectors/jk/tomcat-connectors-1.2.48-src.tar.gz
tar xvf tomcat-connectors-1.2.48-src.tar.gz
cd tomcat-connectors-1.2.48-src/native
chmod +x buildconf.sh
./configure --with-apxs=/usr/local/src/apache/bin/apxs
 make && make install


ls -al /usr/local/src/apache/modules/mod_jk.so
vi /usr/local/src/apache/conf/httpd.conf

[맨아래추가]
=======================================================
LoadModule jk_module modules/mod_jk.so

<IfModule mod_jk.c>
JkWorkersFile conf/workers.properties
JkLogFile logs/mod_jk.log
JkLogLevel info
JkLogStampFormat "[%a %b %d %H:%M:%S %Y] "
JkOptions +ForwardKeySize +ForwardURICompat -ForwardDirectories
JkRequestLogFormat "%w %R %V %T %U %q"
</IfModule>

<IfModule dir_module>
    DirectoryIndex index.html index.htm index.php index.php3 index.cgi index.jsp
</IfModule>
=======================================================

vi /usr/local/src/apache/conf/workers.properties
=======================================================
workers.tomcat_home=$CATALINA_HOME
workers.java_home=$JAVA_HOME
ps=/
worker.list=tomcat1
worker.tomcat1.port=8009
worker.tomcat1.host=192.168.9.99 // 여기 바꾸셔야댑니다
worker.tomcat1.type=ajp13
worker.tomcat1.lbfactor=1
=======================================================

vi /usr/local/src/apache/conf/httpd.conf
477줄 주석해제
Include conf/extra/httpd-vhosts.conf


vi /usr/local/src/apache/conf//extra/httpd-vhosts.conf

=======================================================
[마지막에 추가]
<VirtualHost *:80>
     ServerAdmin dslee
     DocumentRoot "/usr/local/src/apache/htdocs/"
     ServerName 192.168.9.99
     JkMount /*.jsp tomcat1
     JkMount /servlet/* tomcat1
</VirtualHost>
=======================================================
cd /usr/local/tomcat8/conf/
vi server.xml

####기존 설정은 삭제하고 변경#####
<Connector port="8080" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />

↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

<Connector port="8009" 
       maxThreads="2048" minSpareThreads="20" maxSpareThreads="100"
       connectionTimeout="20000"
       enableLookups="false"
       acceptorThreadCount="4"
       keepAliveTimeout="3"
       maxKeepAliveRequests="10000"
       protocol="AJP/1.3" redirectPort="8443" />
#####################

vi /usr/local/tomcat8/webapps/ROOT/index.jsp
<%-- test.jsp --%>
<%@ page language="java" %>
<%!
int a=100;
int b=50;
%>
<%
int c;
c=a+b;
%>
<html>
<head><title>JSP Test</title></head>
<body>
[JSP TEST OK]<br>
a=<%=a%><br>
b=<%=b%><br>
a+b=<%=c%>
</body>
</html>


systemctl restart httpd
systemctl restart tomcat8

