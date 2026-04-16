# sort, uniq

## sort, uniq 명령어 사용하기

(1) sort
```bash
sort [옵션] [파일명]
```
- 사용자가 지정한 파일의 내용을 정렬하거나, 정렬된 파일 내용을 병합할 때 사용

(2) sort 주요 옵션
```bash
sort -f data.txt
sort -r data.txt
sort -b data.txt
sort -u data.txt
```
- `-f` - 영어 정렬 시 대소문자 구분 안 함
- `-r` - 역순 정렬
- `-b` - 앞에 붙는 공백을 무시하고 정렬
- `-u` - 정렬 후 중복행 제거

(3) uniq 사용하기
```bash
uniq [옵션] [파일명]
```
- 중복된 내용의 연속된 행을 하나만 남기고 삭제한다.
- 중복된 내용일지라도 연속되지 않으면 중복을 찾아내지 못한다.
- sort 와 함께 사용하여, 중복된 내용끼리 정렬하고 uniq 처리하는 형태로 주로 사용한다.

(4) uniq 주요 옵션
```bassh
uniq -c data.txt
uniq -d data.txt
uniq -u data.txt
```
- `-c` - 연속하는 중복 라인이 몇 번 나오는지 보여준다.
- `-d` - 연속하는 중복 라인 중 한 라인만 보여준다.
- `-u` - 중복이 없는 라인만 보여준다.
- 만약 sort 되어있지 않은 상태라면 중복된 라인이라고 할지라도 `uniq -u` 처리했을 때 중복되지 않은 라인으로 보여진다.

(5) sort 와 uniq 함께 사용하기 예시
```bash
sort data.txt | uniq -u
# cat data.txt | sort | uniq -u 와 동일
```
- data.txt 를 오름차순으로 정렬하고 중복되지 않은 라인만 출력한다.