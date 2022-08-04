$ mv b1 ../cmd/      // b1을 cmd디렉토리로
$ ls                     // 리스트확인
$ cd ../cmd/             // cd를이용해서 cmd로

$ mv a1 a2 ../cmd2/  cmd2디렉토리로 a1,a2이동

cat > text   // text 파일작성 
$ cp text text-copy  // text파일을 text-copy파일로 복사
$cat text-copy       // 내용확인

$ mkdir dir           // dir 이라는 디렉토리생성
$ cp text dir/       // text파일을 dir디렉토리 밑으로 복사

$ ../                   // 상위 디렉토리로 이동
$ cp cmd/ cmd3/  // 디렉토리 복사
에러뜹니다.
$ cp –r cmd/ cmd3/  // 디렉토리 복사 (하위에 있는것도 다 복사해)
어제 디렉토리 삭제할때 $ rm –rf 디렉토리명 // 여기서 r 옵션쓰엿습니다.
Rmdir이라고 해도 삭제되요

$ cat > city        // city라는 파일 생성
                      내용작성
저장 CTL + D
$ cat city > city2   // city파일을 city2 로 저장
$ ls                   // 파일 리스트 확인
$ cat city >> city2  // city내용을 city2 끝 부분에 추가
$ cat city >> city2  // city내용을 city2 끝 부분에 추가

$ seq 100 100 1500    // sequncy를 만드는데 
                               100부터 시작해서 100증가로                 
                               1500 까지







wc -l x*  //앞에 x가 붙는것들이 몇줄인지 알려줌

rm -rf x* //앞에 x가 붙는것들을 몽땅 지운다

split K //K파일을 1000줄씩 쪼갬

cp /etc/services K // etc/services에 있는 경로의 파일을 K라는 이름으로 복사해 가져온다.

seq 100 100 1000 > A1 //1000까지 100부터 100씩 올라가는것을 


split
split K
split -C5000 --addtional-suffix=.java K backup_ //K파일을 backup_이름을 붙여서 5000용량까지 .java확장자로 쪼개버림

--------배운내용 정리---------

useradd
userdel
권한 777 / rwx
chmod

seq 100 100 1000 //시퀀스 100부터 100단위로 1000까지
pwd // 내가 어디있는지 보는 병령어
mv 옮기는 명령어
cp 복붙
split 쪼개기 
    -d //뒤에 숫자가 오도록
    -additional0suffix- //확장자명
    -C //라인기준 바이트자르기
    -B //바이트기준 자르기