# dashed file name

## 파일 이름이 dash 로 시작하는 경우

- dash(-)는 보통 명령어의 옵션과 argument 로 사용되기 때문에 열기 위해서 다른 설정이 필요하다.

(1) touch (파일 생성)
```bash
touch -- -[나머지 파일명]
```

(2) cat (파일 읽기)
```bash
cat < -[나머지 파일명]
```

(3) cp (파일 복사)
```bash
cp -- -[나머지 파일명]
```
