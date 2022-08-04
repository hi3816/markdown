----배울 것-----
```
d압출 해제
묶기. 풀기

vi 편집기

패캐지관리 (rpm, yum)
***************history****************

    touch file1.txt
    touch file2.txt
    touch file3.txt
    ll
    cp /etc/services services
    cd services
    ll
    gzip
    gzip file1.txt
    ll
    gzip services
    ll
    gzip -d services.gz
    gzip file2txt
    gzip file3.txt
    gzip -d file2txt.gz file3.txt.gz    //한번에 푸는것도 가능

    705  sudo yum install zip -y
    706  sudo yum install unzip -y
    707  zip file.zip file1.txt
    708  ll
    709  unzip file.zip
    710  ll
    711  rm file1.txt
    712  unzip file.zip
    713  ll
    714  bzip -k file1.txt
    715  bzip2 -k file1.txt
    716  ll
    717  bzip2 -d file1.txt.bz2
    718  ll
    719  rm file1.txt
    720  ll
    721  bzip2 -d file1.txt.bz2
    722  ll
    723  unzip file.zip
    724  ll
    725  rm file1-copy
    726  rm file1_copy

    -----------------

    sudo yum install -y wget  //
    wget http://ftp.exim.org/pub/pcre/pcre-8.20.tar.gz//웹에 있는 파일을 다운
    gzip -d pcre-8.20.tar.gz


    --------





************정리************


---압축풀기, 묶기---

    tar -cvf [묶여서 생성될 이름][대상파일들]  //묶어서 압축
    tar -xvf [묶인 파일 이름]      //묶어서 압축한거 풀기
        
    압축을 하면서 묶을 수 있다

    tar -cvfj   //
    tar -cvfz

    -명령어를 만드는 명령어
    alias ll2 =ls -Alh'




---vi모드---

    -많이쓰는 명령어

    dd      //한줄 잘라내기
    3dd     //세줄 잘라내기
    p       //붙여넣기
    x       //한글자삭제
    dw      //단어삭제
    u       //실행취소
    y       //복사

    -마지막행모드
    :q!
    :w!
    :wq!
    :set nu
    :set nonu


---yum rpm---
    
    wget
    https://www.oracle.com/java/technologies/downloads/#java18

    -c //이어서 다운하기
    
    
    yum
        -install
        -remove
        -check-update
        -update

        -yum list

        

