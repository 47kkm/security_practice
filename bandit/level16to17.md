# nmap

## nmap 사용하기

(1) nmap
```bash
nmap [호스트]
```
- 포트 오픈 여부, 구동중인 서비스 등을 알 수 있는 도구
- `nmap [호스트]` 결과
  - 어떤 포트가 열려 있는지 (`open`) --> 연결 가능 (서비스 실행 중)
  - 닫혀 있는지 (`closed`) --> 포트는 있지만 닫힘
  - 막혀 있는지 (`filtered`) --> 방화벽 때문에 확인 불가


(2) nmap 주요 옵션
```bash
nmap -p [포트번호] [호스트]
nmap -sV [호스트]
nmap -O [호스트]
nmap -sS [호스트]
nmap -sU [호스트]
nmap --script [스크립트(NSE)] [호스트]
```
- `-p` - 포트 지정하여 스캔
  - `[포트번호]` - 단일 포트 스캔
  - `[포트번호, 포트번호, ...]` - 다중 포트 스캔
  - `[포트번호-포트번호]` - 범위 지정
- `-sV` - 포트 열림 + 어떤 서비스인지 확인 (HTTP, SSH, MySQL 등)
- `-O` - OS 스캔
- `-sS` - 스텔스 스캔 (root 권한 필요)
- `-sU` - UDP 스캔 (DNS, SNMP 같은 UDP 확인)
- `--script` - nmap 의 자체 스크립트인 NSE 실행. 카테고리(tag)가 붙어있다.
  - `default` - 기본적으로 안전하고 유용한 스크립트
  - `safe` - 서비스에 영향이 거의 없음
  - `auth` - 인증 관련
  - `vuln` - 취약점 검사
  - `discovery` - 정보 수집
  - `ssl` - SSL/TLS 관련
  - `brute` - 무차별 대입

cf) 어떤 스크립트가 있는지 찾기
- 리스트 보기
  ```bash
  ls /usr/share/nmap/scripts/
  ```
- 특정 키워드(태그) 검색
  ```bash
  ls /usr/share/nmap/scripts/ | grep ssl
  ls /usr/share/namp/scripts/ssl-*.nse
  ```



(3) 사용 예시
```bash
# 192.168.0.10 호스트의 5000-6000 범위 포트 중에서 SSL/TLS 통신을 하는 포트 검사
$ nmap -p 5000-6000 --script ssl-cert 192.168.0.10
```