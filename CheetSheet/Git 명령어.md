# Git 명령어 정리

 ### add
 - working directroy에 있는 파일을 staging area로 등록하는 명령어

 ### commit
 - 이력을 남기는 작업. staging aread에 있는 파일을 커밋할 수 있다.
 - 커밋할 시에 -m 옵션을 통해 커밋 메시지를 입력해야 한다.

 ### log
 - 커밋 로그 조회
 - --oneline (한줄표현), --graph (분기점 표시), --all (모든 이력 표시)

 ### show 
 - 커밋 정보 확인 가능한 명령어
 - 커밋 해시값, 메시지, 수정된 파일 목록, 변경 내용 등을 확인 가능

 ### clone
 - 원격 저장소 가져오기
 - git clone [url] 또는 git remote add [url]

 ### push
 - 로컬 브랜치 커밋을 원격 저장소 브랜치로 전송 : git push [별칭][branch]

 ### pull
 - 추적 원격 분기에서 커밋을 가져오고 병합 (fetch와 merge가 동시에 이루어짐)

 ### fetch
 - git 원격에서 모든 분기를 가져오기

 ### merge
 - 원격 브랜치를 현재 브랜치에 병합
 - merge에는 2가지 방법이 존재 : fast-forward merge, 3-way merge

 ### branch
 - 독립적으로 작업을 진행하기 위한 개념
 - 필요의 의해 만들어지는 각각의 브랜치는 다른 브랜치의 영향을 받지 않음
 - 여러 작업을 동시에 진행할 수 있게 해줌
 - git branch --list : 현재 가지고 있는 branch 목록을 보여줌

 ### checkout
 - 브랜치를 생성해주는 명령어
 - git checkout -b : 브랜치 생성 및 이동


 ### switch
 - 브랜치를 생성해주는 명령어
 - git switch -c : 브랜치 생성 및 이동

 ### fast forward merge
 - 병합하려는 branch들 사이에 분기가 존재하지 않는 경우 사용
 - conflicts가 발생할 수 없는 구조


 ### 3-way merge
 - base에서 commut을 진행해하여 분기해 나간 상태일 때 사용하는 방식
 - conflicts가 발생한 경우 수동으로 병합해주어야 함.
 - 3-way merge를 사용할 경우 병합한 새로운 커밋이 발생

 ### rebase
 - 지정된 것보다 먼저 현재 분기의 모든 커밋을 적용
 - 커밋 히스토리를 깔끔하게 관리할 수 있지만, 공개되어 사용하는 커밋을 rebase하면 문제 발생
 - rebase 작업 중 충돌이 일어날 경우 충돌 해결하고나서 add한 후에 --continue 옵션 사용.
 - rebase 자체를 취소할 경우 --abort 옵션 사용

 ### reset
 - 커밋을 되돌리는 명령어
 - 깃허브와 같은 온라인 저장소에 올라가 다른 사람 간 코드 공유를 허가하지 않음


 ### revert
 - 커밋을 되돌리는 명령어
 - 깃허브와 같은 온라인 저장소에 올라가 다른 사람 간 코드 공유를 허가
 - --edit-no : 커밋 메시지 수정 안하는 옵션 (기존 커밋명 앞에 revert가 추가되는 형태로 자동 )

### stash
- 아직 마무리 하지 않은 작업을 스택에 잠시 저장
- 수정 및 단계적 변경 사항 저장 : git stash 또는 git stash save
- stash 작업 후 working directory는 clean상태
- git stash로 저장되는 파일: Modified면서 Track되는 파일, Staging Area에 있는 파일
- git stash pop : 적용과 동시에 스태쉬 제거
- git stash drop : 가장 최근의 스태쉬 제거
- git stash list : 스태쉬 리스트 목록 확인
- git stash apply : 가장 최근의 스태쉬를 가져와 적용 // 자동으로 staged 상태로 만들어 주지 않는다. 또한 스택에 여전히 남아있다.
- git stash apply [스택이름] : 스태쉬 이름의 해당하는 스태쉬를 가져옴
- git stash apply --index : staged 상태까지 복원
- git stash show -p | git apply -R : 실수로 잘못 스태쉬 적용한 것을 되돌리고 싶을 때 사용

 ### 포인터
 - 깃은 객체 포인터 개념을 사용
 - 대표적인 객체 포인터 : HEAD
 - HEAD : 작업 중인 브랜치의 마지막 커밋 ID를 가리키는 참조 포인터
 - ^를 사용하여 이전 포인터 활용 가능
