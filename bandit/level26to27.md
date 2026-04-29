# Level 26 --> 27

## 문제 개요
`level 26` 에서 획득한 `bandit26` 계정으로 로그인한 셸에서 다음 레벨의 비밀번호를 획득한다.

## 풀이 과정
1. `more`와 `vim`을 이용해 `bandit26`으로 ssh 서버 로그인
2. `ls -al`명령어를 이용해 파일 리스트 및 권한 확인
3. `bandit27-do` 파일에 `setuid`설정 확인
4. `bandit27-do` 실행을 통해 해당 파일 실행 방식 파악
5. `bandit27-do` 를 이용해 `/etc/bandit_pass/bandit27` 을 읽어 비밀번호 획득

## 핵심 개념
1. setuid
- [Level19to20](./level19to20.md) 참고

## 보안 관점 분석
- 제한된 환경과 setuid 파일이 조합되어 취약점 발생
- 셸 탈출 후 setuid 설정된 파일을 이용해 권한 상승 및 비밀번호 획득

## 위험 요소
- 제한된 환경이라고 해도 인터랙티브 프로그램 사용 가능할 때 setuid 파일이 있다면 `root`권한을 획득하는 등의 권한 상승이 발생할 수 있음

## 대응 방안
- setuid 최소화
- 인터랙티브 프로그램 제한
- no-pty 적용
- ForceCommand 사용