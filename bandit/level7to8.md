# Level 7 --> 8

## 문제 개요
`data.txt` 파일에서 "millionth" 라는 단어 옆에 있는 값을 찾아, 다음 레벨의 비밀번호를 획득한다.

## 풀이 과정
1. ssh 서버 접속
2. `data.txt` 파일 확인
3. `grep` 명령어를 사용하여 특정 문자열 검색
4. 해당 라인에서 비밀번호 추출

## 핵심 개념
1. grep
```bash
grep [옵션][패턴][파일명]
```
- 특정 파일에서 지정한 문자열이나 정규표현식을 포함한 행을 출력해주는 명령어이다.

2. grep 사용하기
- `grep "text" data.txt` - data.txt 파일에서 text 문자열 찾기
- `grep "text" data.txt data1.txt` data.txt, data1.txt 파일에서 text 문자열 찾기
- `grep "text" *` - 현재 디렉터리 내 모든 파일에서 text 문자열 찾기
- `grep "text" *.txt` - .txt 확장자를 가진 모든 파일에서 text 문자열 찾기 

3. grep 자주 사용하는 옵션
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

4. 헷갈리는 명령어
```bash
# (1)
find / -name data.txt | grep "text"

# (2)
grep "text" data.txt
```
- (1) 의 경우 find 의 결과가 나열된 행에서 "text" 문자열을 찾는 것이다. (파일 목록에서 text 찾기)
- (2) 의 경우 data.txt 파일 내에서 "text" 문자열을 찾는 것이다. (파일 내에서 text 찾기)

## 보안 관점 분석
- 대량의 데이터에서 특정 정보를 빠르게 추출한다.

## 위험 요소
- 공격자는 로그, DB, 설정 파일 등 대량의 정보가 포함된 파일에서 원하는 특정 정보들만 뽑아볼 수 있다.
- 데이터를 필터링 하여 빠르게 뽑아낸다.
- 민감 정보가 로그/파일에 포함될 경우 `grep` 을 통해 빠르게 식별할 수 있다.

## 대응 방안
- 민감 정보가 로그에 포함되지 않도록 한다.
- 로그 등 중요파일 접근 권한 제한
- 로그 마스킹 처리