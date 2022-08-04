```
복습 

cat

tac

ls -al

ll

>

>>

-n

ln -w -i -v

cd ../

mkdir

cal

who

history

CTL + L

rm
    -r
    -f

rmdir
    *

sudo su-

exit

su - [username]

sudo passwd

useradd[username]

userdel -r[username]

rm -rf 정보가 남아있는 유저 권한 읽는법 (rwx)

chmod [num] [파일명]
groupadd
gorupmod
    -n
    -g

groupdell
gpasswd
gpasswd -A // a옵션은 관리자를 지정할떄
groups
자바설치
chown
====================================

6일차

touch Test // 내용이 아무것도 TEST없는 파일 생성

find 
    -name 
    -user 
    -perm 
    -type 
    -size

wc -l /etc/rpm/macrosfjava // -l옵션은 line을 말하는것
wc -l /etc/yum/conf //
wc -l /etc/services
cp /etc/rpm/macros.fjava macros.fjava
ll
pwd
cp /etc/yum.conf yum.conf
cp /etc/services services

sudo find /etc/ -name "*.conf" | tail -n5

*******history*******

touch TEST
  499  ll
  500  cd ../../
  501  pwd
  502  find /home/ljh
  503  cd ~
  504  cd ../../
  505  find /home/ljh/ -name Test
  506  find /home/ljh/ -name TEST
  507  cd /home/ljh
  508  cd /home/ljh/
  509  mkdir TEST_D1
  510  mkdir TEST_D2
  511  mkdir TEST_D3
  512  ㅣㅣ
  513  ll
  514  wc -l
  515  wc -l /etc/
  516  wc -l /etc/yum.conf
  517  cp /etc/rpm/macros.fjava macros.fjava
  518  ll
  519  pwd
  520  cp /etc/yum.conf yum.comf
  521  cp /etc/services services
  522  ll
  523  wd help
  524  wd -help
  525  wc help
  526  wc -help
  527  wc --help
  528  cp services TEST_D
  529  ll
  530  cp services Test_D1/ service_COPY
  531  cp services Test_D1/service_COPY
  532  cp services TEST_D1/service_COPY
  533  cd TEST_D1
  534  ll
  535  chmod 555 service_COPY
  536  ll
  537  cd ../TEST_D2
  538  mkdir sample
  539  ls
  540  cd ~
  541  find -name sample
  542  cd TEST_D3 && touch sample
  543  ll
  544  cd ~
  545  find -name sample -type f
  546  find -name sample -type d
  547  find /home/ljh/ size +600k
  548  find /home/ljh/ -size +600k
  549  cd /home/ljh
  550  ll
  551  find /home/ljh/ -size +100c
  552  find /home/ljh/ --perm 555
  553  find /home/ljh -perm 555
  554  find home/ljh/ -perm 644
  555  ll
  556  find /home/ljh/ -user ljh
  557  sudo find /etc/ -name "*.conf" | tail -n5
  558  ll
  559  history



find
    -name
    -user
    -type
    -perm
    -size

grep
    -n
    -v
    -A
    -B
    -r

***문제***
문제1 
DB라는 유저를 추가하고 
비밀번호를 1234 로 변경하십시오.
useradd DB
passwd DB


문제2
DB라는 유저로 변경후 /home 으로
 이동후 경로를 출력하십시오
su -DB
cd /home
pwd
history

문제3
최상위 위치로 돌아간뒤 /home/DB 
sample라는 폴더를 만들고 속성(권한)값을
rw-rw-r-- 으로 변경하시오.

cd ~
cd /home/DB/
mkdir sample
chmod 664 smaple
ls -al



문제4
그룹 naver 를 만들고  유저 
developer1,developer2 를 추가하시오.
useradd developer1
useradd developer2
groupadd naver
gpasswd -a developer1 naver
gpasswd -a developer2 naver


문제5
developer1 유저로 속성(권한)값이 
r--rw-r-x 인 test 폴더를 만들고(최상위 위치에) 
그룹(test)를 naver로 변경하시오.

sudevelop1
mkdir test
chmod 465 test
sudo su -
cd /home/develop1
chown develop1 :naver test
또는
chgrp naver test

문제6. 
폴더를 지우고 싶은데 삭제가 안된다. 
그이유는? (사용한 명령어는 rmdir 이였다.)
1. 폴더가 비어있지않거나
2. 권한이없다

rm -rf

문제7.
pwd 명령어를 실행하니 현재 위치가 ~ 엿다 /home/DB/sample의 data 파일의 행번호를 붙여서 출력하는 명령어는?
cd /home/DB/sample
cat -n data
wc -l //행수만 출력


문제8
현재 디렉터리에 있는 파일명의 확장자가 java인 모든파일을 /tmp로 복사하시오.
touch hello5.java
cp *.java /tmp/



```
