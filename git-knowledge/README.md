## 깃헙의 명령어와 다양한 상황


## Git 명령어

### 저장소 관리

- **git init**: Git 저장소 초기화
- **git clone <repository_url>**: 원격 저장소를 로컬에 복제
- **git remote add <remote_name> <remote_url>**: 새로운 원격 저장소 추가
- **git remote rm <remote_name>**: 원격 저장소 제거
- **git remote rename <old_name> <new_name>**: 원격 저장소 이름 변경
- **git fetch**: 원격 저장소의 최신 변경 사항 가져오기
- **git pull**: 원격 저장소에서 변경 사항을 가져오고 병합하기
- **git push**: 로컬 변경 사항을 원격 저장소로 푸시하기

### 브랜치 관리

- **git branch**: 브랜치 목록 보기
- **git checkout -b <new_branch>**: 새로운 브랜치 생성하고 전환하기
- **git branch -d <branch_name>**: 로컬 브랜치 삭제하기
- **git branch -m <new_branch_name>**: 현재 브랜치의 이름 변경하기
- **git branch -vv**: 로컬 브랜치와 연결된 원격 브랜치 정보 보기

### 커밋 관리

- **git add .**: 모든 변경 사항을 스테이지에 추가하기
- **git commit -m "Commit message"**: 스테이지에 추가된 변경 사항을 커밋하기
- **git commit --amend**: 최신 커밋을 수정하거나 메시지 변경하기
- **git reset HEAD~1**: 최근 커밋을 취소하고 해당 변경 사항을 작업 디렉토리로 되돌리기
- **git revert <commit_hash>**: 특정 커밋의 변경 사항을 되돌리는 새로운 커밋 생성하기
- **git cherry-pick <commit_hash>**: 다른 브랜치에서 지정된 커밋을 현재 브랜치로 가져오기

### 변경 사항 확인

- **git status**: 현재 작업 디렉토리의 Git 상태 확인하기
- **git diff**: 작업 디렉토리의 변경 사항 보기
- **git log**: 커밋 히스토리 확인하기
- **git show <commit_hash>**: 특정 커밋의 변경 사항 보기
- **git blame <file>**: 파일의 각 라인에 대한 마지막 수정자 및 커밋 정보 보기

### 기타 유틸리티

- **git stash**: 현재 변경 사항을 스태시에 임시로 저장하기
- **git tag**: 태그 관리하기
- **git clean**: 추적되지 않은 파일 및 디렉토리 삭제하기
- **git config**: Git 설정 관리하기
- **git grep**: 저장소에서 특정 패턴을 포함하는 문자열 검색하기
