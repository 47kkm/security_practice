# ncat

## ncat 사용하기

(1) ncat
```bash
ncat [옵션] [호스트] [포트번호]
```
- 네트워크 연결, 데이터 송수신, SSL/TLS 를 지원하는 도구
- nc(netcat) 보다 보안, 기능이 강화
- 기능
  - 서버 열기
  - 클라이언트 접속
  - TLS 암호화
  - 파일 전송

(2) ncat 주요 옵션
```bash
ncat -l [포트번호]
ncat --ssl [호스트] [포트번호]
ncat -v [호스트] [포트번호]
ncat -u [호스트] [포트번호]
ncat -w [seconds] [호스트] [포트번호]
```
- `-l` - listen. 포트 열고 대기
- `--ssl` - SSL/TLS 암호화 연결
- `-v` - 상세 출력
- `-u` - udp 사용
- `-w` - timeout. seconds 초 후 자동 종료

(3) 사용 예시
```bash
# localhost 5000번 포트에 TLS 통신으로 메시지 보내기
$ echo "hello" | ncat --ssl localhost 5000
```
```bash
# 5000번 포트로 들어오는 데이터를 받아서 file.txt 로 저장하기
$ ncat -l 5000 > file.txt
```
```bash
# file.txt 내용을 5000번 포트로 전송
$ ncat localhost 5000 < file.txt 
```
```bash
# 192.168.0.10 호스트의 80번 포트 열려있는지 확인
ncat -zv 192.168.0.10 80
```