# strings

## strings 명령어 사용하기

(1) strings
```bash
strings [옵션] [파일명]
```
- 사람이 읽을 수 없는 바이너리 파일에서 텍스트(ASCII)만 추출할 때 사용한다.

(2) strings 주요 옵션
```bash
strings -f data.txt
strings -n data.txt
```
- `-f` - 각 문자열 행 앞에 파일 이름을 같이 출력한다.
- `-n` - 문자열의 최소 길이를 정한다.