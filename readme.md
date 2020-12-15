# gh-cli-tutorial
## 목적
- experience `github` by `gh cli`
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
만약 브랜치에 이슈번호를 넣어서 사용한다면 [자동화](precommitmsg.md)할 수 있다. 

### 7. Pull Request
- `pr`, pull request : 다른 branch나 fork로부터의 변경사항을 `pull` 할 것을 `request` 한다는 뜻. pull은 가져오기(fetch)와 병합(merge) 명령의 합이다. 개인적으로 비직관적인 작명이라 생각한다.


```
# pr create : 현재 checkout된 브랜치 기준으로 pr이 생성된다.
# pr을 생성하는 브랜치의 커밋이 1개 이상 있어야 한다. 
gh pr create
# pr 리스트
gh pr list
```
- `pr`은 커밋이 아니라 브랜치에서 생성된다.   
- 따라서 pr 생성 후, 커밋이 추가될 수도 있다.   
- pr 생성 후 커밋이 추가되는 시나리오는 다음과 같다.   
    1. merge 이전에 변경될 커밋 추가.
    2. code review 후 결과를 반영한 커밋 추가.
    3. conflict 가 발생해서 merge 커밋 추가.  
     (일반적인 merge : branch -> master, 본 항목에서 기술되는 merge : master -> branch )   
- 상기 시나리오 1번을 시도해보자.
```
# 파일 수정 후 
git commit -am "fixed minor bug for (#2)"
git push
gh pr view [num]
```
```
# pr 상세 보기
gh pr view 6
# pr 차이 보기 
gh pr diff 6
```

### 8. merge

gh pr merge





## 협업 환경 테스트


## References
- https://cli.github.com/manual