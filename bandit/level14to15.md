# netcat (nc)

## nc 사용하기

(1) nc
   
```
[보내는 쪽] --> TCP/UDP --> [받는 nc]   
```

```bash
nc [옵션] [호스트] [포트]
```
- TCP/UDP 로 메시지를 주고 받는 네트워크용 메시지 도구
- 기능
  - 포트 열고 대기하기
  - 다른 포트로 메시지 보내기
  - 파일 전송
  - 포트 열려있는지 테스트
  - 간단한 서버 만들기

(2) nc 주요 옵션
```bash
nc -l [포트번호]
nc -v [호스트] [포트번호]
nc -z [호스트] [포트번호]
nc -u [호스트] [포트번호]
nc -w [seconds] [호스트] [포트번호]
```
- `-l` - listen. 포트 열고 대기
- `-v` - verbose. 연결 과정을 자세히 출력
- `-z` - 포트 스캔 모드. 열려 있는 포트를 찾는다.
- `-u` - tcp 대신 udp 사용
- `-w` - timeout. seconds 초 후 자동 종료

(3) 사용 예시
```bash
# localhost 5000번 포트에 메시지 보내기
$ echo "hello" | nc localhost 5000
```
```bash
# 5000번 포트로 들어오는 데이터를 받아서 file.txt 로 저장하기
$ nc -l 5000 > file.txt
```
```bash
# file.txt 내용을 5000번 포트로 전송
$ nc localhost 5000 < file.txt
```
```bash
# 192.168.0.10 호스트의 20-80 포트 중 열려있는 포트 확인 
nc -zv 192.168.0.10 20-80
```