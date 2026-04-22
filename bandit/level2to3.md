# Level 2 --> 3

## 문제 개요
홈 디렉터리에 있는 `spaced in this filename`파일에서 다음 레벨의 비밀번호를 획득한다.

## 풀이 과정
1. ssh 서버 접속
2. `ls`를 이요해 파일 목록 확인
3. `spaces in this filename` 파일 확인
4. `cat`을 이용해 공백이 포함된 파일명을 가진 파일 읽기

## 핵심 개념
- shell 에서 공백은 명령어에서 인자(argument)를 구분하는 기준이 된다.
- `escape(\) + 공백` 으로 처리한다.
- '' 으로 처리한다.

1. touch (파일 생성)
```bash
touch space\ filename
touch spaces\ in\ filename
touch 'space filename'
```

2. cat (파일 읽기)
```bash
cat space\ filenmae
cat spaces\ in\ filename
cat < -spaces\ in\ filename
cat 'space filename'
```

3. cd (디렉터리 이동)
```bash
cd space\ directory
cd 'space directory'
```

## 보안 관점 분석
- shell 명령어 해석 방식에 의해 space(공백) 은 인자를 구분하는 기준이 된다.
- 따라서, 딥력값이 어떻게 해석되느냐에 따라 명령 실행 결과가 달라진다.

## 위험 요소
- 사용자 입력을 적절하게 처리하지 않으면 의도하지 않은 명령이 실행될 수 있다.

## 대응 방안
- 사용자 입력 검증
- shell command 사용 최소화
- quote 와 escape 의 적절한 사용