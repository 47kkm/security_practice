# tr

## tr 명령어 사용하기

(1) tr
```bash
tr [옵션] [SET1] [SET2]
```
- 특정 문자를 다른 문자로 변환(치환) 하거나 삭제한다.
- 일반적으로 길이가 동일한 두 문자 SET를 허용하며, 첫 번째 세트의 문자를 두 번째 세트의 문자로 대체한다.

(2) tr 주요 옵션
- `-d` - 지정한 문자를 삭제한다.
  ```bash
  $ echo 'hello 123 world' | tr -d '0-9'
  hello world
  ```
- `-s` - 같은 문자가 여러 번 반복될 때, 이를 하나로 압축한다.  
  ```bash
  $ echo 'hellooo   world' | tr -s 'o' ' '
  hello world
  ```
- `-c` - 문자열 내 포함되지 않은 문자들을 변환
  ```bash
  # 숫자를 제외한 모든 문자를 x로 변환
  $ echo 'hello123' | tr -c '0-9' 'x'
  xxxxx123
  ```
- 아무 옵션이 없는 경우 set1을 set2 로 변환
  ```bash
  $ echo 'hello world' | tr 'a-z' 'A-Z'
  HELLO WORLD
  ```

(3) 카이사르 암호
- 간단한 치환 암호
- 암호화하고자 하는 내용을 알파벳 별로 일정한 거리만큼 밀어서 다른 알파벳으로 치환하는 방식이다.

(4) ROT13
- 카이사르 암호의 일종으로 알파벳을 13글자씩 밀어서 만든다. (키 값이 13이 된다.)
- 암복호화가 같은 카이사르 암호인데, 알파벳이 26글자이기 때문에 2번 적용할 경우 원래대로 돌아온다. (1회 적용 --> 암호화, 2회 적용 --> 복호화)
```bash
$ echo 'hello world' | tr 'A-Za-z' 'N-ZA-Mn-za-m'
uryyb jbeyq
$ echo 'uryyb jbeyq' | tr 'A-Za-z' 'N-ZA-Mn-za-m'
hello world
```
- `A`에서 13번째는 `N`에 대응, `Z`에서 13번째는 `M`에 대응.
- `Z`가 끝난 이후는 다시 `A`로 돌아간다. 이를 나타내기 위해 `N-ZA-M`이 된다. 즉 (1) `N` 부터 `Z` 까지 (2) 이후 다시 `A` 부터 `M` 까지