# Git이란?
- 컴퓨터 파일의 변경사항을 추적하고 여러 명의 사용자들 간에 해당 파일들의 작업을 조율하기 위한 분산 버전 관리 시스템
- 소프트웨어 개발에서 소스 코드 관리에 주로 사용되지만 어떠한 집합의 파일의 변경사항을 지속적으로 추적하기 위해 사용 가능

# 버전 관리가 필요한 이유
- 전체 개발 소스를 공유하면서 개발 파트를 나누기 수월해진다
- 같은 모듈을 개발하더라도 소스를 서로 공유하며 개발할 수 있다
- 원할 때 예전 버전 내용 전체를 되돌려 볼 수 있으며 복잡한 코드를 개발할 때 이전 버전과 비교하기 수월해진다

# Git의 장점
- 빠른 협업환경 조성
- 누가 언제 무엇을 어떻게 수정했는지 코드 리뷰 가능
- 이슈 트래커 지원
- Github을 이용하여 깃을 쉽게 공유 가능
- 대부분의 IDE에서 git 연동을 제공

# Git의 주요 개념들
- merge : 한 branch에서 완성한 작업을 다른 branch에 병합
- tag : 특정 이력을 가지는 commit에 대한 참조
- pull request : 완료한 작업을 다른 사람이 리뷰하고 병합하도록 요청
- issue : 기능에 대한 논의, 버그 추적
- wiki : 링크들을 연결해 웹페이지 만들기
- push : 내 컴퓨터 로컬에 저장되어 있던 버전 정보를 서버(git 저장소)에 올리기
- pull : Git 저장소 서버로부터 내 컴퓨터 로컬로 버전 정보 전체를 가져오기

# Git 명령어

### Git 계정 정보 설정
- git config --global user.name "user_name"
- git config --global user.email "email@email.com"

### Git 설정
- Git에서는 윈도우와 맥 사이 (CRLF 개행문자 차이)의 줄넘김 차이를 방지하기 위한 설정을 제공
- git config --global core.autocrlf [true / false]
- git config --global user.safecrlf [true / false]
- Window 환경에서는 autocrlf를 true, safecrlf는 false로 설정

### Git 저장소 만들기
- 로컬 컴퓨터에서 git 저장소 생성 : git init
- 원격 저장소 가져오기 : git clone [url] 또는 git remote add [url]
- git remote add url은 local 저장소의 내용을 빈 원격 저장소에 등록하고 싶을 때 사용

### Git 브랜치 이름 설정
- 기본 브랜치 명은 master
- 기본 브랜치 명을 설정 시 master가 아닌 mainm으로 설정 권고
- git config --global init.defaultBranch "브랜치이름"

### Git 프로세스
![image](https://user-images.githubusercontent.com/101855945/203780014-90067c3b-2ce2-4c9f-9048-dff4786ded26.png)
- Working Directory : 내가 작업하려는 PC 내의 디렉터리
- Staging Area : git commit하기전에 저장되는 git의 공간 (커밋 예정인 파일, 디렉터리들이 모여있는 곳)
- Local Repository : 내 PC에 파일이 저장되는 개인용 저장소
- Remote Repository : 원격 저장소 (Github)

### 커밋과 변경사항
- 커밋은 이력을 남기는 작업
- 커밋을 위해서는 파일을 add 명령어를 통해 Staging Area로 옮겨주어야 함
- git add "파일명" 또는 git add . ('git add .'은 현재 staged area에 없는 모든 파일을 staged area로 옮겨주는 명령어)
- Staging 취소 : git reset [파일명]
- 현재 파일의 상태를 확인 : git status (커밋 완료 된 후에는 변경사항이 표시되지 않는다.)
- 파일이 Staging Area에 있다면 커밋 가능
- 커밋 : git commit -m "커밋 메시지"
- 커밋 전과 후 변동점 비교 : git diff
- staged area와 repository Head에 대해 비교 : git diff --staged
- 커밋 로그 조회 : git log
- log 옵션 : --oneline (한줄 표현), --graph (분기점 표시), --all (모든 이력 표시)

### 커밋 되돌리기
- git reset과 git revert를 통해 커밋을 되돌리기 가능
- reset은 되돌린 후 커밋 이력 제거, revert는 현재까지의 커밋 이력에 되돌리기 커밋 추가
- 'git reset'과 'git revert'는 'github' 같은 온라인 저장소에 올라가 다른 사람 간 코드 공유의 유(revert)무(reset)에 따라 달라짐
- git reset --option '돌아갈 커밋'
- git revert [commit hash]

### 포인터
- Git은 객체 포인터 개념을 사용
- 대표적인 객체 포인터는 HEAD
- HEAD : 작업 중인 브랜치의 마지막 커밋 ID를 가리키는 참조 포인터
- ^를 사용하여 이전 포인터 활용 가능
EX) 'HEAD^'는 마지막에서 2번째, 'HEAD^^'는 마지막에서 3번째

### 커밋 정보 탐색
- git show를 사용하여 커밋 정보를 확인 가능
- 커밋 해시값, 커밋 메시지, 수정된 파일 목록, 변경 내용 등을 확인 가능
- git show : 현재 브랜치의 가장 최근 커밋 정보를 확인
- git show 커밋해시값 : 특정 커밋 정보를 확인
- git show HEAD : HEAD 포인터가 가리키는 커밋 정보를 확인
- git show 커밋해시값 또는 HEAD^ : 이전

### 브랜치 및 병합
- 브랜치 목록 조회 : git branch --list
- 브랜치 생성 : git branch [브랜치명]
- 브랜치 생성 및 이동 : git checkout -b [브랜치명] 또는 git switch -c [브랜치명]
- 브랜치 삭제 : git branch -d 또는 git branch -D (-D는 강제 삭제 옵션)
- 브랜치 간 작업물 병합 : git merge [브랜치명]
- 지정된 것보다 먼저 현재 분기의 모든 커밋을 적용 : git rebase [branch] (이력 재기록)
- rebase는 커밋 히스토리를 깔끔하게 관리할 수 있지만 공개되어 사용하는 커밋을 rebase하면 문제 발생
- push 전 커밋 지우기 : git reset --hard [commit id]
- conflicts : 병합하는 과정에서 브랜치 별로 동일한 파일에서 다른 내용이 중첩된다면 발생하는 것
- conflicts가 발생했다면 수동으로 해결해야 한다.

### 병합 방식
- merge는 2가지 방법이 존재 (fast-forward merge, 3-way merge)
- fast-forward merge : 병합하려는 branch들 사이에 분기가 존재하지 않는 경우 사용

![image](https://user-images.githubusercontent.com/101855945/203785454-34790a70-a94e-4bec-81e5-8a9c0236f952.png)

- fast-forward merge는 구조 상 conflicts가 발생하지 않는다.
- 3-way merge : base에서 commit을 진행하여 분기해 나간 상태일 때 사용하는 방식

![image](https://user-images.githubusercontent.com/101855945/203786339-47fe2e70-9c0d-40a0-bad9-a48a36f427c0.png)

- 다음과 같이 분기가 발생하여 3-way merge를 사용할 경우 병합한 새로운 커밋이 발생

### 경로 변경 추적
- 커밋 관련 파일 삭제 : git rm [파일명]
- Stage 관련된 파일 옮기기 : git mv [existing-path][new-path]
- 커밋 이력 + 관련 파일 및 이동 이력까지 한번에 조회 : git log --stat -M

### 공유 및 업데이트
- git url을 별칭으로 추가 : git remote add [alias][url]
- Git 원격에서 모든 분기를 가져오기 : git fetch [alias]
- 원격 브랜치를 현재 브랜치에 병합 : git merge [alias][branch]
- 로컬 브랜치 커밋을 원격 저장소 브랜치로 전송 : git push [alias][branch]
- 추적 원격 분기에서 커밋을 가져오고 병합 (fetch와 merge가 동시에 이루어짐) : git pull

### 임시 커밋
- 수정 및 단계적 변경 사항 저장 : git stash
- 아직 마무리 하지 않은 작업을 스택에 잠시 저장
- git stash로 저장되는 파일: Modified면서 Track되는 파일, Staging Area에 있는 파일
- stash 스택의 맨 위에서 작업 쓰기 : git stash pop
- stash 스택의 맨 위에서 변경 사항 삭제 : git stash drop








