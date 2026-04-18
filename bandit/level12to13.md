# 압축 파일

## hexdump, xxd

(1) hexdump
- 파일이나 데이터를 16진수 형태로 보여주는 도구
- 바이너리 데이터를 16진수로 바꿔서 읽기 편하게 함
- 디버깅 / 분석 / 리버스 엔지니어링에서 많이 사용
- 주로 사용하는 용도
  - 파일이 깨졌는지 확인할 때
  - 실행파일(바이너리) 내부 구조 볼 때
  - 네트워크 패킷을 분석할 때
  - 텍스트가 아닌 이상한 파일 내용을 확인할 때

(2) xxd 명령어
```bash
xxd [옵션] [변환할 파일]
```
- 파일/표준 입력으로부터 hexdump를 만들거나 복원해주는 명령어

(3) xxd 주요 옵션
- `옵션 없음` - 16진수와 ASCII 를 함께 보여줌
  ```bash
  $ xxd file.bin
  00000000: 4865 6c6c 6f20 776f 726c 640a  Hello world
  # 왼쪽: offset, 가운데: 16진수, 오른쪽: ASCII
  ```
- `-r` - hexdump 텍스트를 바이너리 데이터로 변환
  ```bash
  $ xxd -r file.hex > file.bin
  ```
- `-p` - 16진수만 출력
  ```bash
  $ xxd -p file.bin
  48656c6c6f20776f726c640a
  ```

## 압축

(1) 개요
- gzip / bzip2는 파일 하나씩 압축만 수행한다.
- tar는 여러 파일을 하나로 묶는 역할로 압축은 수행하지 않는다.
- 보통 gzip + tar / bzip2 + tar 형태로 같이 사용한다.
  ```bash
  tar + gzip --> .tar.gz
  tar + bzip2 --> .tar.bz2
  ```

(2) gzip
```bash
gzip [옵션] [파일명]
```
- 압축률은 보통이지만 속도가 빠르고 확장자로 .gz 를 사용한다.

(3) gzip 주요 옵션
- `옵션 없음` - 압축파일 생성
- `-d` - 압축 해제
- `-c` - 결과를 stdout으로 출력
  ```bash
  $ gzip -c file.txt > file.gz
  ```

(4) bzip2
```bash
bzip2 [옵션] [파일명]
```
- gzip 보다 느리지만 압출률이 높으며 확장자로 .bz2 를 사용한다.

(5) bzip2 주요 옵션
- `옵션 없음` - 압축파일 생성
- `-d` - 압축 해제
- `-c` - 결과를 stdout으로 출력
  ```bash
  $ bzip2 -c file.txt > file.bz2
  ```
- `-1 ~ -9` - 압축 강도 조절
  ```bash
  # 최고 압축 (느림)
  $ bzip2 -9 file.txt
  ```

(6) tar
- 여러 파일을 하나로 묶는다. (아카이브)
- 파일 자체를 압축하지는 않는다.

(7) tar 주요 옵션
- `기본 사용`
  ```bash
  # 묶기
  tar -cvf archive.tar file1 file2 dir/
  
  # 풀기
  tar -xvf archive.tar
  ```
- `-c` - 생성 (create)
- `-x` - 압축 해제 (extract)
- `-v` - 과정 출력 (verbose)
- `-f` - 파일 지정 (file)
- gzip 압축과 함께 사용
  ```bash
  # 묶기 (tar 아카이브 --> 압축)
  tar -czvf archive.tar.gz folder/
  # 풀기 (압축 해제 --> tar 아카이브 해제)
  tar -xzvf archive.tar.gz
  ```
- bzip2 압축과 함께 사용
  ```bash
  # 묶기 (tar 아카이브 --> 압축)
  tar -cjvf archive.tar.bz2 folder/
  # 풀기 (압축 해제 --> tar 아카이브 해제)
  tar -xjvf archive.tar.bz2
  ```
