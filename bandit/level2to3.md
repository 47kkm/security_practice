# spaces in filename

## 파일 이름에 공백이 포함되어 있는 경우

- `escape(\) + 공백` 으로 처리한다.
- '' 으로 처리한다.

(1) touch (파일 생성)
```bash
touch space\ filename
touch spaces\ in\ filename
touch 'space filename'
```

(2) cat (파일 읽기)
```bash
cat space\ filenmae
cat spaces\ in\ filename
cat < -spaces\ in\ filename
cat 'space filename'
```

(3) cd (디렉터리 이동)
```bash
cd space\ directory
cd 'space directory'
```
