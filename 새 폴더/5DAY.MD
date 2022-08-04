vm 으로 리눅스르르 올렸을 경우

1..ipconfig
vitualBox 호스트 주소확인

2.vm에서 터미널킨다음에(리눅스 기동된 상태)
	ip addr // vm 리눅스 인터넷 정보확인
	enp0s3 // ip 주소확인(10.0.2.15)
	

	yum install net-tools -y
	yum install openssh-server -y
	yum install openssh-client -y
	
	cd /etc/sysconfig/network-scripts/
	ll
	vi ifctg-enp0s3
	밑에 내용에 ONBOOT = no로 되어있으면 YES

	VM 네트워크 설정변경하기
	설정 -> 네트워크 -> 다음에 연결됨-> NAT로 변경 -> 고급 -> 포트포워딩 -> 옆쪽에 + 클릭 -> ssh | TCP | 윈도우IP | 22 | 리눅스 IP | 22
	->확인 눌러서 저장

	TERA TERN에 
	윈도우 IP 입력
	ID, PASSWD 입력 나오면 리눅스 접속됨


root상태로

groupadd teamA 	//teamA라는 그룹명의 그룹추가
tail /etc/group	 //추가된거 확인
grou
groupmod -n team1 teamA 	// 그룹명 변경, 변경할 그룹명을 적고 기존 그룹명을 적는다
tail /etc/group 		//추가된거 확인g

gorupdel team1 		//team1이라는 그룹을 삭제
tail /etc/group 		//추가된거 확인

groupmod -g 3000 teamB 	//-g 옵션으로 3000번대 그룹으로 만드는게 가능
tail /etc/group 		//확인

adduser -g 

gpasswd -A
groups

/etc.passwd
/etc/gpasswdcat 

grep

자바설치
chown

=========================

