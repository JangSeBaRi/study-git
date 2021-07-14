## git 생성 및 git 버전관리
# git init
## 새로 추가한 파일
# git add f1.txt
## git 수정한 사람 명시
# git config --global user.name
# git config --global user.email
## 버전관리
# git commit
## 버전로그
# git log
## stage area (git add 를 했을 때 올라가는 상태, stage area에 있는 것들만 commit이 된다.)
## 버전로그의 차이를 보여줌
# git log -p
## 버전로그 이하버전
# git log "commit id"
## 두 버전사이의 차이점
# git diff "commit id".."commit id"
## 현재작업과 직전 버전의 차이(add하기 전)
# git diff
## 해당하는 버전 이하로 돌아가기 (중요! : 공유된 버전 이후에는 절대로 reset 사용 금지)
# git reset "commit id" --hard
## 가장 최근 버전으로 완벽하기 돌아가기 (status 깔끔)
# git reset --hard HEAD 
## 커밋 관련 메뉴얼 확인
# git commit --help
## 수정된 모든 파일 add 없이 commit 시키기 (버전관리가 되지않은 파일은 따로 add 시켜야함)
# git commit -a
## editor를 키지않고 이름 추가, 수정된 모든 파일 commit 시키기
# git commit -am "11"
## branch 목록 확인
# git branch
## branch 생성
# git branch [branch name]
## branch 이동
# git checkout [branch name]
## branch 생성 + 이동
# git checkout -b [branch name]
## log에 branch 흐름 파악하기
# git log --branches --decorate --graph
# git log --branches --decorate --graph --oneline
## master branch에는 없고 exp branch에는 있는 log
# git log master..exp
## 두 branch 사이에 차이
# git log -p master..exp
## 두 branch 사이에 차이점을 보여줌
# git diff master..exp
## 머징작업 (master로 checkout 후 exp 를 머징함)
# git merge exp
## branch 제거 
# git branch -d [branch name]

## merge에는 fast forward라는 방식이 있음. 이 경우 새로운 커밋을 생성하지 않는다. master에서 branch를 땄고 그 후 branch가 수정되는 동안 master에서 수정사항이 없다면 merge했을 때 새로운 커밋을 생성하지 않고 branch = master라는 것만 명시해준다.

## 작업중이던 branch를 커밋, add 안시키면서 일시 중지하면서 저장해두기
# git stash (save)
## 숨겨논 stash 불러오기
# git stash apply
## 숨겨논 stash 목록 (명시적으로 삭제하지 않으면 계속 저장되어 있음)
# git stash list
## stash 명시적 삭제 (가장 최근 저장된 stash 삭제)
# git stash drop
## stash 불러오고 저장되어 있는 것 삭제
# git stash pop
## stash는 적어도 버전관리 되고있는것들만 저장이됨 (새로운 파일을 추가한 경우 add 하지 않으면 List에 저장되지않음)

## 저장소 생성 (작업할 수 있는 공간은 없고 .git 의 내용물만 있음)
# git init --bare
## 현재 저장소에 원격 저장소를 추가한다
# git remote add origin [주소]
## 현재 저장소에 있는 원격 저장소의 목록
# git remote -v 
## 저장소를 지우고 싶다면
# git remote remove origin
## 원격저장소에 파일 밀어넣기
# git push
## 깃의 push형태를 전역적으로 simple로 바꾼다
# git config --global push.default simple
## 원격 저장소의 master 브랜치에 push한다 (u를 적으면 로컬과 원격저장소의 branch를 연결)
# git push --set-upstream origin master
# git push -u origin master
## 이후 두개의 master가 연결되었으므로 
# git push

## 이미 만들어진 남의 저장소 사용하는 방법 => fork를 눌러서 복제 후 url을 따온다.
# git clone [주소] [폴더명]

## 최근에 만든 commit 이름 변경 또는 누락시킨 내용을 add 한 후 적용시키면 커밋수정됌
# git commit --amend

## 또 다른 로컬저장소에서 원격저장소 내용 땡겨오고 싶을 때
# git pull