# 6. 브랜치

<h1>6-1. 새로운 작업</h1>
-	브랜치는 나뭇가지, 지사, 분점 등 줄기하나에서 뻗어온 갈림길을 의미<br>
-	깃에서는 저장공간 하나에서 가상의 또 다른 저장공간을 만드는 것을 의미<br>

<h3>6-1.1 브랜치 작업</h3>
-	새로운 기능을 추가하거나 많은 변경이 예상되면, 폴더를 통째로 복사하고 폴더 이름을 변경하며 작업해왔음<br>
-	커밋은 파일의 수정이력을 관리한다고 하면, 브랜치는 프로젝트를 독립적으로 관리하는데 사용함<br>
-	안정된 코드 상태를 유지하고, 개발중인 작업과 구분하여 처리해야 할 필요가 있음<br>

<h3>6-1.2 깃 브랜치 특징</h3>
-	가상 폴더 : 깃의 브랜치는 작업 폴더를 실제로 복사하지 않고, 가상 폴더로 생성함. 이는 물리적으로 복제된 구조보다 더 유연하게 처리할 수 있음<br>
-	독립적인 동작 : 원본 폴더와 분리하여 독립적인 개발 작업 수행이 가능함. 기존에는 소스코드의 작업 폴더를 별도로 생성하고 물리적으로 복사된 각자의 폴더에서 코드 작업 후 소스코드 2개를 합쳤으나, 브랜치를 활용하면 각 브랜치에서 소스코드를 수정하고, 원본코드에 병합하는 명령만 실행하면 됨<br>
-	빠른 동작 : 다른 VCS들은 브랜치 생성 시 내부파일 전체를 복사하지만, 깃은 다른 도구들에 비해 가볍고, 전환이 빠른 브랜치 기능을 보유하고 있다. 이는 Blob개념을 도입해서 내부를 구조화 했기 때문인데, Blob은 포인트와 유사한 객체이다. 깃은 브랜치 변경 시 포인터를 활용하여 빠른 전환성능을 보여준다.<br>
-	브랜치를 명령을 사용하면 내부적으로 커밋 하나를 생성하여 브랜치에 할당한다. 다른 버전 관리 시스템은 파일 전체 복사를 하지만, 깃은 41바이트를 가지는 해시파일 하나만 만들면됨.<br>


<h1>6-2. 실습 준비</h1>
-	깃은 master 브랜치를 하나 가지고 있고 브랜치는 HEAD 포인터를 가지고 있다.<br>

<h3>6-2.1 저장소 생성 및 초기화</h3>
<img src =https://user-images.githubusercontent.com/101856066/194851906-186b405f-6b3d-4638-a5b3-63ac6189fc7a.png>

<h3>6-2.2 기본 브랜치</h3>
-	깃은 최소 브랜치가 1개 이상 필요함.<br>
-	저장소를 처음 초기화하면 master 브랜치가 자동으로 생성됨<br>
-	모든 커밋 이력은 브랜치에 기록됨.<br>
-	깃에서는 항상 현재 작업하는 브랜치 위치를 확인하는 것이 중요<br>
-	또한 branch 명령어로 현재 브랜치를 확인할 수 있음<br>

<h1>6-3. 브랜치 생성</h1>
-	브랜치는 공통 커밋을 가리키는 지점임.<br>
-	커밋처럼 SHA1 해시키를 가리킨다. 하지만 이는 기억하기 번거로우므로, 특정 커밋을 가리키는 별칭을 만듬.<br>
-	새 브랜치를 생성하면 포인터만 있는 브랜치가 생성됨.<br>
-	브랜치는 마지막 커밋 위치를 가리키는 역할만 할 뿐, 실제 브랜치가 아님. 실제 브랜치는 실제 커밋이 추가될 때 만들어짐<br>

<h3>6-3.1 브랜치 생성</h3>
-	기본적으로 제공되는 master 브랜치 이외에 사용자가 직접 정의한 사용자 정의 브랜치를 생성하는 것을 의미함<br>
-	브랜치는 또 하나의 개발 분기점을 의미함.<br>
-	브랜치를 생성하려면 아래와 같은 명령어를 사용한다.<br>
-	git branch [Branch name] [Commit ID]<br>
-	브랜치 이름만 입력하면, 현재 HEAD포인터 기준으로 새로운 브랜치 생성, 직접 지정하면 지정한 커밋 ID 기준으로 생성<br>
<img src ="https://user-images.githubusercontent.com/101856066/194851908-79197048-e5ee-4c12-9c57-7cc5be97285e.png">

<h3>6-3.2 브랜치 이름</h3>
-	브랜치 이름은 /를 사용하여 계층적 구조로 만들어 사용이 가능. 규칙은 아래와 같음<br>
-	기호(-)로 시작할 수 없음<br>
-	마침표(.)로 시작할 수 없음<br>
-	연속적인 마침표(..)를 포함할 수 없음<br>
-	빈칸, 공백 문자, 물결(~), 캐럿(^), 물음표(?), 별표(*), 대괄호([]) 등은 포함할 수 없음<br>
-	아스키 제어 문자는 포함할 수 없음<br>
-	주의할 점은 브랜치 이름은 중복해서 사용하지 않아야함.<br>
<img src="https://user-images.githubusercontent.com/101856066/194851909-82509ef4-51f2-4d38-803d-74be89ef2ef1.png">

<h3>6-3.3 소스트리 브랜치</h3>
-	새탭에서 Add 클릭<br>
-	탐색을 눌러 만든 폴더를 찾아 선택 후 추가<br>
-	왼쪽에서 브랜치 탭 확인<br>
-	Master 브랜치 선택<br>
-	마우스 오른쪽 버튼을 눌러 브랜치… 메뉴 선택<br>
-	위쪽 브랜치 생성 버튼 클릭<br>
-	커밋을 선택하여 브랜치 생성하는 것은 지정한 커밋을 기준으로 브랜치를 생성한다는 것<br>
-	커밋 목록에서 브랜치 생성하면 명시된 커밋에 브랜치가 체크되어 있는 것을 확인<br>
-	최종커밋 기준으로 작업사본 부모항목 선택<br>
<img src="https://user-images.githubusercontent.com/101856066/194851912-4ee2567a-8fad-4495-b269-90f80e2b685f.png">
<img src="https://user-images.githubusercontent.com/101856066/194851806-d54e393b-de01-488d-bd3d-a2e991cf38ce.png">

<h1>6-4. 브랜치 확인</h1>
<h3>6-4.1 간단 브랜치 목록</h3>
-	깃 배시에서 브랜치 목록을 확인하려면 git branch 만 단독으로 사용하면 됨<br>
-	별표는 현재 선택된 브랜치를 의미<br>
-	소스트리 목록에서 O 마크 이동 확인<br>
-	깃 배시에서는 *로 표시함.<br>
<img src="https://user-images.githubusercontent.com/101856066/194851811-870aa219-303b-445d-a91c-a37a2ae3e104.png">

<h3>6-4.2 브랜치 해시</h3>
-	특정한 커밋의 해시 값을 가리킴 저수준 명령인 rev-parse를 사용하여 현재 브랜치가 어떤 커밋 해시 값을 가리키는지 확인할 수는 있음<br>
-	브랜치의 해시값과 브랜치를 생성한 기준 커밋의 해시 값이 동일함.<br>
<img src="https://user-images.githubusercontent.com/101856066/194851813-40e3d4f9-5884-4f62-9fb2-f20c8b52a2ec.png">

<h3>6-4.3 브랜치 세부 사항 확인</h3>
-	Branch 명령어 뒤에 -v 또는 –verbose 옵션을 함께 사용하여 이름, 커밋ID, 커밋 메시지 등을 볼 수 있음.<br>
<img src="https://user-images.githubusercontent.com/101856066/194851816-acd2ad5e-9761-42de-b987-dcbd9446b7d9.png">

<h1>6-5. 브랜치 이동</h1>
<h3>6-5.1 체크아웃</h3>
-	호텔에서 퇴실할 때 체크아웃 한다는 말에서 유래함.<br>
-	현재 브랜치를 떠나, 새로운 브랜치로 들어간다는 의미<br>
-	git checkout [브랜치이름]<br>
-	주의점은 깃은 하나의 워킹 디렉터리만 가지고 있고 다른 브랜치에서 작업하려면 브랜치를 변경하여 워킹 디렉터리를 재설정해야 함<br>
-	또한 커밋하지 않은 내용이 없으면, 브랜치를 변경할 수 없음. 이는 6-5.5에서 조금 더 자세히 언급됨<br>
<img src="https://user-images.githubusercontent.com/101856066/194851819-821a74db-3d0e-45e4-ad10-f3a6f1ee452d.png">

<h3>6-5.2 브랜치 동작 원리</h3>
-	HEAD 정보는 항상 변경된 브랜치의 마지막 커밋을 가리킴. 브랜치가 이동하면 HEAD 포인터도 같이 이동함<br>
-	변경된 브랜치로 새로 작업할 수 있도록 워킹 디렉터리를 변경함. 기존 브랜치의 워킹 디렉터리를 정리해야 함<br>

<h3>6-5.3 소스트리 실습</h3>
-	브랜치 선택 상태에서 마우스 우클릭 후 체크아웃master…를 선택<br>
-	O 마크가 이동함<br>

<h3>6-5.4 이전 브랜치</h3>
-	리눅스에서 대시(-) 기호는 이전 디렉터리를 의미<br>
-	이 대시를 활용하여 쉽게 이전 브랜치로 이동할 수 있음.<br>
-	git checkout -를 활용하면 됨.<br>
<img  src="https://user-images.githubusercontent.com/101856066/194851822-461181f5-ac1b-4bc1-9151-589ca191961b.png">

<h3>6-5.5 워킹 디렉터리 정리</h3>
-	현재 작업하고 있는 워킹 디렉터리를 정리 하고 넘어가야 함<br>
-	워킹 디렉터리 안에서 작성하는 내용이 존재하고, 커밋하지 않았으면 체크아웃 시 경고가 발생함<br>
-	깃은 향후 충돌을 방지하기 위해서 이러한 제약을 걸어 놓았음<br>
<img src="https://user-images.githubusercontent.com/101856066/194851827-a7640d4d-50ce-49ba-8335-4c3a9150ed27.png">

<h1>6-6. 브랜치 공간</h1>
<h3>6-6.1 브랜치 로그</h3>
-	현재까지 작업한 로그 기록을 확인할 때 git log를 쓰지만, 브랜치 흐름도를 쓰려면 --graph를 같이 사용함.  --graph --all 옵션을 사용하여 모든 로그를 출력함<br>
-	브랜치 경로와 작업들이 텍스트 그래프로 출력됨<br>
<img src = https://user-images.githubusercontent.com/101856066/194851829-47009ce7-98ac-484d-be4d-1c5000d952b3.png>

<h3>6-6.2 브랜치 소스 확인</h3>
<img src = https://user-images.githubusercontent.com/101856066/194851830-5cba61b1-4fa5-434c-8fc9-c5366b985da1.png>

<h1>6-7. HEAD 포인터</h1>
<h3>6-7.1 마지막 커밋</h3>
-	깃은 마지막 커밋 정보가 매우 중요함. <br>
-	마지막 커밋 정보를 기반으로 새로운 커밋을 생성하기 때문임 마지막 커밋은 새로운 커밋의 부모 커밋임.<br>
-	마지막 커밋을 가리키는 HEAD 포인터를 부모 커밋으로 대체하여 사용함. 이를 활용하여 빠르게 스냅샷을 생성할 수 있음<br>

<h3>6-7.2 브랜치 HEAD</h3>
-	브랜치를 이동하면 HEAD 포인터도 이동함.<br>
<img src = https://user-images.githubusercontent.com/101856066/194851834-4c8f473a-4fb3-472d-8542-509751001621.png>

<h3>6-7.3 소스트리 HEAD</h3>
-	소스트리 에서도 HEAD 포인트 상태를 쉽게 확인할 수 있음<br>
-	각 브랜치의 마지막 위치를 브랜치 아이콘으로 표시<br>
<img src =https://user-images.githubusercontent.com/101856066/194851839-16771e03-3d81-4c33-9d3f-cc563f0008ef.png>

<h3>6-7.4 상대적 위치</h3>
-	깃의 HEAD 포인터는 내부적으로 커밋을 생성하고 브랜치를 관리하는데 매우 유용<br>
-	다양한 명령어를 입력할 때도 기준점으로 두고 사용함<br>
-	캐럿(^)과 물결(~) 기호를 같이 사용함.<br>
-	이전 n개의 위치를 지정하려면 ^나 ~를 여러 개 사용하는 것 보다는 HEAD^n 또는 HEAD~n 과 같이 숫자를 붙이는 것이 좋음<br>

<h3>6-7.5 AHEAD, BHEAD</h3>
-	원격 저장소와 연동하여 깃을 관리하면 브랜치마다 HEAD가 2개가 있음.<br>
-	AHEAD와 BHEAD는 서로 다른 저장소 간 HEAD 포인터의 위치 차이를 의미함.<br>
-	AHEAD : 서버로 전송되지 않은 로컬 커밋이 있는 것을 의미함.<br>
-	BHEAD : 로컬 저장소로 내려받지 않은 커밋이 있는 것을 의미함.<br>

<h1>6-8. 생성과 이동</h1>
<h3>6-8.1 자동 이동 옵션</h3>
-	Branch 생성과 이동을 한번에 처리하는 명령이 존재한다.<br>
-	Git checkout -b를 이용하면 된다.<br>
-	Git checkout -b [브랜치 이름]과 같이 사용한다.<br>
<img src = https://user-images.githubusercontent.com/101856066/194851839-16771e03-3d81-4c33-9d3f-cc563f0008ef.png>

<h3>6-8.2 커밋 이동</h3>
-	브랜치 이름은 커밋 해시 키와 동일함.<br>
-	브랜치 이름 대신 커밋 해시키를 사용하여 체크아웃 할 수도 있음<br>
<img src = https://user-images.githubusercontent.com/101856066/194851841-41466eb7-17d4-4532-a30f-d6966b61b1ef.png>

<h3>6-8.3 HEAD를 활용한 이동</h3>
-	HEAD 포인터를 사용하여 체크아웃 할 수도 있음<br>
-	Git checkout HEAD-1과 같이 사용<br>
<img src = https://user-images.githubusercontent.com/101856066/194851844-7b0d7f74-fb1f-432e-8f9e-770214b1fe30.png>

<h3>6-8.4 돌아오기</h3>
-	커밋 해시키 또는 HEAD를 사용하여 과거의 커밋으로 체크아웃했으면 다시 현재 시점으로 돌아와야 한다. 간단하게 대시(-)를 활용하면 됨<br>
-	Git checkout -를 사용한다.<br>
<img src = https://user-images.githubusercontent.com/101856066/194851850-31bf88a3-079f-4493-b8b1-c59b0c6421c2.png>

<h1>6-9. 원격 브랜치</h1>
-	로컬 저장소, 원격 저장소는 일종의 저장소임. 분산형 저장소의 특징으로써 다수의 저장소를 만들어 연결할 수 있음.<br>
<h3>6-9.1 리모트 브랜치</h3>
-	원격 저장소에 생성한 브랜치를 리모트 브랜치라 부름<br>
-	별도 명령을 실행해서 저장소를 동기화해야 함.<br>
-	보통 별칭/브랜치 이름 형태를 가지고 있음<br>

<h3>6-9.2 실습 준비</h3>
<img src = https://user-images.githubusercontent.com/101856066/194851853-6b53d1b5-2502-4303-88dc-36b8768c60d5.png>
<img src = https://user-images.githubusercontent.com/101856066/194851855-bd57cb53-16c1-4295-9b5f-5604bc7b3ae8.png>

<h3>6-9.3 브랜치 추적</h3>
-	로컬 저장소에서 원격 저장소의 브랜치를 가리키는 것을 브랜치 추적이라고 부름<br>
-	추적 브랜치를 트래킹 브랜치라고 부름.<br>
-	로컬 저장소가 원격 저장소와 연결될 때 원격 브랜치의 트래킹 정보는 자동으로 갱신됨<br>

<h3>6-9.4 브랜치 업로드</h3>
-	자동으로 등록되지 않고, git remote show 명령어로 등록된 원격 브랜치를 확인할 수 있음<br>
-	리모트 브랜치는 서버 간 통신을 하고 나서 생성됨.<br>
-	동기화 하려면 git push [원격 저장소 별칭] [브랜치 이름] 작업을 해줘야 함<br>
<img src = https://user-images.githubusercontent.com/101856066/194851858-3e784cc8-95c6-4de8-9a29-57392ae666d5.png>
<img src = https://user-images.githubusercontent.com/101856066/194851861-36769f3d-44ec-4095-b6a9-800f79aad74e.png>
<img src = https://user-images.githubusercontent.com/101856066/194851863-51b7de3b-1d32-4a16-88c0-29848482af11.png>
<img src = https://user-images.githubusercontent.com/101856066/194851864-95016535-7a4b-4b49-866c-dce407e8af2c.png>

<h3>6-9.5 이름이 다른 브랜치</h3>
-	반드시 원격 브랜치와 로컬 브랜치는 이름이 동일할 필요가 없음.<br>
-	브랜치를 직접 수동으로 지정하여 연결하려면 콜론으로 구분한다.<br>
-	Git push origin 브랜치이름:새로운브랜치 와 같이 사용한다.<br>
<img src = https://user-images.githubusercontent.com/101856066/194851866-b2ef0831-4f35-43a3-a474-ea51f93f4010.png>
<img src = https://user-images.githubusercontent.com/101856066/194851869-8574e93d-9776-46ae-a7eb-e64de5d048c7.png>                                                                                                               
<h3>6-9.6 업스트림 트래킹</h3>
-	업스트림은 브랜치 추적을 다르게 표현한 것<br>
-	로컬 저장소의 브랜치와 원격 저장소의 브랜치는 업로드 할 수 있도록 매칭되어 있음<br>
-	이러한 매칭을 업스트림 트래킹이라고 함<br>
-	이는 원격 브랜치와 로컬 브랜치를 연결해주는 중간 다리 역할을 함<br>
-	Git branch -r 옵션을 사용하면 원격 저장소의 리모트 브랜치 목록을 확인할 수 있음<br>
-	모든 브랜치 정보를 확인하고 싶다면 -a 옵션을 사용<br>
-	트래킹 브랜치는 -vv 옵션을 사용하여 확인함<br>
<img src = https://user-images.githubusercontent.com/101856066/194851871-66b6f5ce-62ac-4892-9a05-d7a09589173e.png>
<img src = https://user-images.githubusercontent.com/101856066/194851874-34887d85-c47e-4783-979f-6bd1970d6be3.png>
<img src = https://user-images.githubusercontent.com/101856066/194851878-ba813ee6-342b-4745-b6c6-f44ab5fa66d4.png>

<h3>6-9.7 원격 브랜치 복사</h3>
-	원격 저장소의 리모트 브랜치를 이용해서 로컬 저장소에서도 새로운 브랜치를 생성하여 동기화 가능<br>
-	Git checkout -b 새이름 origin/브랜치이름 과 같이 사용함.<br>
<img src = https://user-images.githubusercontent.com/101856066/194851879-ce00d7b7-4dfc-477a-aad6-320014b4e3a6.png>
<img src = https://user-images.githubusercontent.com/101856066/194851882-2dd4b3db-1762-45b0-b95c-54f2ef5ef5f2.png>
<img src = https://user-images.githubusercontent.com/101856066/194851885-8234dc14-f20f-4589-9b96-d3576b600272.png>
<img src = https://user-images.githubusercontent.com/101856066/194851886-171c12ee-f515-4478-989f-795bd8eca0ba.png>
<img src = https://user-images.githubusercontent.com/101856066/194851887-1396b23a-e58b-46be-b59e-50d59a54ef76.png>

<h3>6-9.8 업스트림 연결</h3>
-	기존에 있는 브랜치를 업스트림으로 직접 설정할 수 있음<br>
-	Git branch -u origin/브랜치이름 과 같이 사용하면 됨<br>
-	-u 옵션은 –set-upstream-to를 의미하고, 기존 브랜치를 특정 원격 브랜치로 추적함.<br>
<img src = https://user-images.githubusercontent.com/101856066/194851889-fbbf876f-54ca-4a5e-b863-5f143b9740a1.png>

<h1>6-10. 브랜치 전송</h1>
<h3>6-10.1 브랜치 푸시</h3>
-	깃의 푸시 작업은 로컬 저장소의 파일들을 원격 저장소로 전송함. 또한 브랜치 정보와 커밋 까지 모두 전송함.<br>
-	원격 저장소 연결만으로 업스트림이 자동으로 설정되지는 않음<br>
-	--set-upstream을 이용해 직접 설정해주어야 함<br>

<h3>6-10.2 브랜치 페치</h3>
-	리모트 브랜치가 페치되면 깃은 단수히 원격저장소별칭/브랜치 포인터만 생성하고 자동으로 병합하지는 않음.<br>
-	병합은 merge로 별도로 해야함.<br>
-	병합하지 않고 테스트만 하고 싶으면 원격 브랜치의 포인터를 사용하여 임시 브랜치 생성 및 직접 체크아웃을 하면 됨<br>

<h1>6-11. 브랜치 삭제</h1>
-	브랜치를 삭제하는 것은 간단함. 하지만 브랜치 내용 및 커밋을 모두 삭제하기에 주의해야 함.<br>
-	현재 자신이 있는 브랜치는 삭제할 수 없음<br>
<img src = https://user-images.githubusercontent.com/101856066/194851894-826cc955-30f3-44ed-aab6-fbb7f68d6223.png>

<h3>6-11.1 일반적인 삭제 방법</h3>
-	-d 옵션을 사용함.<br>
-	Git branch -d [브랜치이름]<br>
-	스테이지 상태가 깨끗할 때만 삭제 허용<br>
<img src = https://user-images.githubusercontent.com/101856066/194851896-c0c61b17-2f03-48df-9d60-ce0cef5d8dd8.png>

<h3>6-11.2 강제 삭제 방법</h3>
-	-D 옵션을 사용해야 함.<br>
-	Git branch -D [브랜치이름]<br>
<img src = https://user-images.githubusercontent.com/101856066/194851898-13cd1077-90a3-4de0-9213-5cf35e66d70e.png>

<h3>6-11.3 소스트리에서 삭제</h3>
-	브랜치 선택 후 우클릭, featuer 삭제를 선택<br>

<h3>6-11.4 리모트 브랜치 삭제</h3>
-	삭제 명령을 푸시해야 하며 git push origin --delete [리모트브랜치이름] 과 같이 사용해야 함.<br>
<img src = https://user-images.githubusercontent.com/101856066/194851899-01caa529-d22a-4c83-b260-d2f03cefa60a.png>
<img src = https://user-images.githubusercontent.com/101856066/194851902-d457e2ed-0827-4bcc-ab7c-e53f201c17e4.png>
<img src = https://user-images.githubusercontent.com/101856066/194851904-8b64a282-4bbe-408b-9e97-6dd2eeb08fe1.png>

