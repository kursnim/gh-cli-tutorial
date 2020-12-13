# gh-cli-tutorial
## 목적
- `gh cli` 를 통해 github를 경험한다.
## 시작
### 1. 설치
- 하기 명령으로 설치한다. 
```
choco install gh
```
- choco (windows) 설치 방법 : [여기](https://chocolatey.org/install)
- 그외 설치 방법 : [여기](https://github.com/cli/cli#installation)  
### 2. 설치 확인
설치가 완료 되었으면 `refreshenv` 혹은 껐다킨 후 `gh --version` 를 통해 설치 유무를 확인.

### 3. login
하기 명령으로 로그인하며, 선택지는 기호에 잘 고른다.
```
gh auth login
...
✔ Logged in as kursnim
```
로그인이 완료
```
gh auth status
```

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
우선, 협업에 유리한 습관을 들이기 위해 다음을 숙지한다.   
- branch에 모든 변경을 커밋한다.
- master는 pull request를 통한 merge commit만 한다.

`git checkout -b [branch name]` 으로 브랜치를 생성과 동시에 checkout 해준다.   
`[branch name]`은 이슈관리를 한다면 간단한기능설명, 이슈번호, assignee 가 들어가야한다. 여기서는 `test-2-kursnim` 이다.
```
git checkout -b test-2-kursnim
```

readme.md를 생성 및 변경 후, 커밋한다.   
추적성 관리를 위해  커밋 메시지에 #2로 이슈 번호를 넣는 것이 중요하다.
```
git add readme.md
# 변경된 파일 add
git commit -m "6. 코드/문서 변경 (#2)"
# 커밋
git push
# Push 
```

### 7. Pull Request
- pull request
- 
gh pr create
gh pr list

gh pr view 6
gh pr diff 6

merge commit 이 일반적이지만 개인 프로젝트이니 rebase로 해본다.





## 협업 환경 테스트


## References
- https://cli.github.com/manual