# gh-cli-tutorial
## github cli 테스트   
### 1. 설치
- 하기 명령으로 설치한다.
```
choco install gh
```
그외 설치 방법 : [여기](https://github.com/cli/cli#installation) 참조.  
### 2. 설치 확인
설치가 완료 되었으면 `refreshenv` 혹은 껐다킨 후 `gh --version` 를 통해 설치 유무를 확인.

### 3. login
```
gh auth login
```
으로 웹페이지를 통해서 인증받았고 ssh 방식을 선택.

### 4. 저장소 생성
`gh repo create [repo name]` 를 통해서 저장소를 cli로 만든다. 
```
gh repo create gh-cli-tutorial
```
로 본 저장소를 생성. 

### 5. 이슈 생성

이슈를 친근하게 다루기위해 alias를 설정하였다.
```
gh alias set i  "issue"
gh alias set ic "issue create"
gh alias set il "issue list"
gh alias set iv "issue view"
```

이슈를 먼저 생성하는 것은 계획과 실행에 큰 도움이 된다.
```
gh ic -a kursnim -t "Initial commit" -b "Blabla"
//    -a [id]         해당 id로 담당자 선정
//    -t [txt]        이슈 제목
//    -b [txt]        이슈 내용
```
```gh il```로 이슈 리스트를 확인 후 해당 번호에 해당하는 이슈를 상세보기
```
gh iv 1
// 1번 이슈 보기

gh iv 1 --web
// 1번 이슈 웹으로 보기
```

### 6. 코드 / 문서 변경
readme.md를 생성 및 변경 후, 커밋한다.   
추적성 관리를 위해  커밋 메시지에 #1로 이슈 번호를 넣는 것이 중요하다.
```
git add readme.md
# 변경된 파일 add
git commit -m "initial commit (#1)"
# 커밋
```


## 협업 환경 테스트


## References
- https://cli.github.com/manual