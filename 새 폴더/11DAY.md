########
#방화벽#
########
yum install firewalld //yum으로 방화벽 관련 설치
systemctl start firewalld
systemctl enable firewalld
firewall-cmd --state //상태
firewall-cmd --zone=public --list-all //방화벽리스트

firewall-cmd --zone=public --add-port=20/tcp --permanent # FTP 
firewall-cmd --zone=public --add-port=21/tcp --permanent # FTP 
firewall-cmd --zone=public --add-port=80/tcp --permanent # HTTP
firewall-cmd --zone=public --add-port=443/tcp --permanent # HTTPS
firewall-cmd --zone=public --add-port=3306/tcp --permanent # MySQL
firewall-cmd --zone=public --add-port=8009/tcp --permanent # Tomcat
firewall-cmd --zone=public --add-port=8443/tcp --permanent # Tomcat redirect

firewall-cmd --reload
firewall-cmd --zone=public --list-all //방화벽리스트

selinux설정
selinux는 보안을 강화시켜주는 보안 커널이지만... 귀찮아진다

setenforce 0 //se보안 해제 재부팅시 다시 걸린다
sestatus// 