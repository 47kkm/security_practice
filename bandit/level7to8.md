# grep

## grep 명령어 사용하기

(1) grep
```bash
grep [옵션][패턴][파일명]
```
- 특정 파일에서 지정한 문자열이나 정규표현식을 포함한 행을 출력해주는 명령어이다.

(2) grep 사용하기
- `grep "text" data.txt` - data.txt 파일에서 text 문자열 찾기
- `grep "text" data.txt data1.txt` data.txt, data1.txt 파일에서 text 문자열 찾기
- `grep "text" *` - 현재 디렉터리 내 모든 파일에서 text 문자열 찾기
- `grep "text" *.txt` - .txt 확장자를 가진 모든 파일에서 text 문자열 찾기 

(3) grep 자주 사용하는 옵션
```bash
grep -c "text" data.txt
grep -i "tEXt" data.txt
grep -n "text" data.txt
grep -r "text" data.txt 
```
- `-c`: 일치하는 행의 수 출력
- `-i`: 대소문자 구별하지 않음
- `-n`: 포함된 행의 번호를 함께 출력
- `-r`: 하위 디렉터리를 포함한 모든 파일에서 검색

(4) 헷갈리는 명령어
```bash
# 1)
find / -name data.txt | grep "text"

# 2)
grep "text" data.txt
```
- 1) 의 경우 find 의 결과가 나열된 행에서 "text" 문자열을 찾는 것이다. (파일 목록에서 text 찾기)
- 2) 의 경우 data.txt 파일 내에서 "text" 문자열을 찾는 것이다. (파일 내에서 text 찾기)