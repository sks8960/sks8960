# 1. 되돌리기
- 깃을 이용하여 버전을 관리하는 목적은 만일의 사태를 대비하기 위해서임
- 개발자는 코드를 단계별로 발전 시키면서 실수를 최소화하고자 노력해야함
- 아무리 주의해서 프로그래밍해도 오류가 생길수 있음
- 억지로 문제를 해결하는 것 보다는 작업을 포기하고 다시 시작하는 것이 더 빠를 수 있음
- 깃으로는 원하는 시점으로 언제든지 전체 코드를 되돌릴 수 있음

### 1-1. 다시 시작
- 몇 줄만 암기하여 코드를 다시 변경하면 되지만, 몇 시간 혹은 며칠동안 작업한 코드라면 이야기가 다름
- 모든 수정내역을 일일히 기억하여 과거로 돌아가는 것은 불가능에 가까움
- 깃을 사용하면 기록된 커밋을 이전 상태로 되돌릴 수 있음
- 코드를 되돌리는 방법에는 reset, revert가 있음  
<img width="361" alt="image" src="https://user-images.githubusercontent.com/101856066/203326274-1fb0f88d-df2c-428f-aecb-a50d3d038b57.png">
<img width="308" alt="image" src="https://user-images.githubusercontent.com/101856066/203326310-46b95ada-7dda-4f77-9414-9a481637e469.png">
<img width="310" alt="image" src="https://user-images.githubusercontent.com/101856066/203326347-09a803d8-686a-410d-8810-3c198e8d75bc.png">
<img width="334" alt="image" src="https://user-images.githubusercontent.com/101856066/203326495-d1b5b2d6-5b22-4a77-a7c1-789c69fb0e37.png">
<img width="326" alt="image" src="https://user-images.githubusercontent.com/101856066/203326545-f91042e1-d4a5-4b72-8fa4-4b2afd1779ed.png">
<img width="319" alt="image" src="https://user-images.githubusercontent.com/101856066/203326592-ac558803-4fe2-4296-9d95-34c093d16950.png">
<img width="324" alt="image" src="https://user-images.githubusercontent.com/101856066/203326621-ceaf37b8-b648-40ec-a560-9b02094d3c30.png">
<img width="220" alt="image" src="https://user-images.githubusercontent.com/101856066/203326980-9ab575fc-5b8c-4c9e-9341-fa65a9a4d3bc.png">


# 2. 리셋
- 리셋은 커밋을 기준으로 이전 코드로 되돌리는 방법으로, 기록된 커밋을 취소함
- 커밋을 취소하는 만큼 리셋 시 신중해야함

### 2-1. 복귀 시점
- 이전 코드로 복귀하려면 복귀 시점을 알려줘야 함
- log 명령어로 커밋 해시값을 확인 후 복귀하고자 하는 커밋의 해시값을 넣어 주면 됨  
<img width="311" alt="image" src="https://user-images.githubusercontent.com/101856066/203327079-7359a35e-42dc-4655-93d8-b7e1dc7d2848.png">

- HEAD 포인터를 사용하여 되돌아갈 수도 있음
- 예시는 git reset --hard HEAD~3 처럼 사용

### 2-2. reset 명령어
- 지정된 커밋 코드로 되돌아감
- 형식은 git reset [옵션] [커밋ID]이다.
- 옵션에는 아래 세 가지가 존재함.
- soft : 스테이지 영역을 포함한 상태로 복원
- mixed : 기본은 mixed임.
- hard : 실제 파일이 삭제된 이전 상태로 복원

### 2-3. soft 옵션
- 가장 낮은 단계의 리셋 동작  
<img width="329" alt="image" src="https://user-images.githubusercontent.com/101856066/203327531-453ada29-a6b4-44fc-a022-f7af890d69ee.png">
<img width="194" alt="image" src="https://user-images.githubusercontent.com/101856066/203327572-aab1bb8f-43ee-4e2b-8b15-32b9b531aa2c.png">
<img width="316" alt="image" src="https://user-images.githubusercontent.com/101856066/203327635-53d86802-bf01-4842-b2f9-eac922f9b441.png">
<img width="307" alt="image" src="https://user-images.githubusercontent.com/101856066/203327695-d59f022f-3ecd-4b57-ba89-b6784f086283.png">

- soft옵션은 파일을 수정하고 add 명령어로 스테이지 영역에 올려 커밋을 실행하기 직전의 단계로 되돌림
- 단순히 HEAD 위치를 이동하는 역할만 함
- checkout 명령어와 HEAD를 이동한다는 점은 동일하나, soft옵션은 브랜치를 이동하진 않음
<img width="308" alt="image" src="https://user-images.githubusercontent.com/101856066/203327788-fa94b459-7388-416c-9ba5-c5996caa141d.png">

- 소스코드의 내용이 변경되지 않더라도 새로 커밋하면 변경된 시간값을 적용하여 해시 값을 생성함.
<img width="323" alt="image" src="https://user-images.githubusercontent.com/101856066/203327892-9c9320b0-57bc-468d-a57e-d5e12f9d1ac8.png">

### 2-4. mixed 옵션
- reset 명령어의 기본값은 mixed 옵션이나 옵션을 생략해서 사용해도됨  
<img width="331" alt="image" src="https://user-images.githubusercontent.com/101856066/203328622-c246c155-053c-434d-9ad3-9357fc3e42e4.png">
<img width="418" alt="image" src="https://user-images.githubusercontent.com/101856066/203328689-c1d8ffd5-ab72-40f3-884b-8917fd856b13.png">
<img width="310" alt="image" src="https://user-images.githubusercontent.com/101856066/203328731-04755536-a1a3-4c8a-8a33-474c5353afc9.png">
<img width="407" alt="image" src="https://user-images.githubusercontent.com/101856066/203328913-e9fa7a7e-32e5-4ca6-8a6e-781276681700.png">

### 2-5. hard 옵션
- 가장 강력한 옵션이고, 모든 작업 내용이 실제로 삭제됨
- 그렇기 때문에 hard옵션은 주의해서 사용해야 함  
<img width="308" alt="image" src="https://user-images.githubusercontent.com/101856066/203329186-f10169e0-a2f8-4c32-a9d4-13dd2fdbc85b.png">
<img width="184" alt="image" src="https://user-images.githubusercontent.com/101856066/203329226-a1f87b63-820e-4f8c-afa4-8c5e175f83c8.png">
<img width="313" alt="image" src="https://user-images.githubusercontent.com/101856066/203329279-83d88be9-2bfd-4f80-bffb-3bf54bcbe62d.png">

### 2-6. 소스트리
- 매번 로그를 검색하여 리셋하는 것은 불편
- 소스트리 커밋 그래프에서 복귀할 커밋 선택 후 우클릭하여 이 커밋까지 현재 브랜치 초기화 메뉴 선택  
<img width="230" alt="image" src="https://user-images.githubusercontent.com/101856066/203329851-88cf61a6-3317-4649-aca1-7bd364611720.png">

- 팝업창에서 soft, mixed, hard 옵션 중 선택  
<img width="298" alt="image" src="https://user-images.githubusercontent.com/101856066/203329961-a42d34c5-4449-4042-a4c1-6dd9b5919aa1.png">

- 정말 되돌릴거면 예 클릭  
<img width="329" alt="image" src="https://user-images.githubusercontent.com/101856066/203330228-0a3fd803-8ff1-4b72-8fc6-ebc9b317469f.png">

### 2-7. 커밋 합치기
- rebase에서 -i 옵션으로 커밋을 하나로 합치는 동작 수행할 수 있었음
- 단일 커밋은 --amend 옵션으로 수정할 수 있음.
- 동작 원리를 이해하면 커밋도 수정 가능  
<img width="304" alt="image" src="https://user-images.githubusercontent.com/101856066/203330550-b1c9d475-0b19-48e5-8ac1-5fb257e35291.png">
<img width="317" alt="image" src="https://user-images.githubusercontent.com/101856066/203330590-fdb63d71-a7ec-42f5-9649-5531209e354f.png">
<img width="182" alt="image" src="https://user-images.githubusercontent.com/101856066/203330661-86141fa9-7549-4a84-8fac-17ab88cd5cc6.png">
<img width="310" alt="image" src="https://user-images.githubusercontent.com/101856066/203330773-08b6453a-846b-4cec-ae07-e391de498a03.png">
<img width="182" alt="image" src="https://user-images.githubusercontent.com/101856066/203330836-9fb94e38-b89f-4526-8fe3-1ebe51cfa7bd.png">

### 2-8. 스테이지 리셋
- 스테이지에 등록할 때에는 add를 사용해왔음
- 등록 된 파일을 다시 unstage 상태로 만들 때는 reset명령어 사용
- 기본 형태에는 --mixed 옵션이랑 HEAD가 축약되어 있음
- HEAD대신 커밋 ID를 사용해도 괜찮음

### 2-9. 작업 취소
- 수정 중 오류가 생겨 모두 취소하고 싶을 때가 있음
- 워킹 디렉터리에서 코드 수정하고 스테이지에 다시 등록함
- 수정을 완전히 취소하려면 워킹 디렉터리와 스테이지 상태를 모두 제거하여 마지막 커밋 상태로 되돌려 놓아야 함
- reset --hard를 이용하여 모두 삭제 처리해야 함

### 2-10. 병합 취소
- 병합된 브랜치도 취소할 수 있음.  
<img width="319" alt="image" src="https://user-images.githubusercontent.com/101856066/203332494-fd87acd9-22d1-43ce-8eaa-7238150d0397.png">
<img width="313" alt="image" src="https://user-images.githubusercontent.com/101856066/203331738-f014cd79-2dd3-45ed-b3a2-42247bb47ba7.png">
<img width="193" alt="image" src="https://user-images.githubusercontent.com/101856066/203332164-d1ea2c52-38d9-48b3-a69a-58e853afc4df.png">
<img width="317" alt="image" src="https://user-images.githubusercontent.com/101856066/203332288-683e533c-eb0d-4e2c-bd64-7aea0e16c06f.png">
<img width="224" alt="image" src="https://user-images.githubusercontent.com/101856066/203332040-a2755532-f494-42d8-a677-720afdec7103.png">
<img width="306" alt="image" src="https://user-images.githubusercontent.com/101856066/203332224-8e635298-3d0a-4ce6-bfb6-6513a61ef95f.png">
<img width="193" alt="image" src="https://user-images.githubusercontent.com/101856066/203332176-603755e7-7b70-4e5b-901b-3c1a0e33c6cf.png">

### 2-11. 주의할 점
- 저장소를 외부에 공개했거나 공유하고 있다면 주의해야 함
- 함께 작업하는 개발자에게 혼란을 줄 수 있음
- 일반적으론 공개 커밋에 대해 리셋 작업을 하지 않음

# 3. 리버트
- 공개 커밋을 되돌리기 위해서 하는 작업
- 커밋 정보 삭제 여부에 차이가 있음

### 3-1. 취소 커밋
- 리버트는 기존 커밋을 남겨 두고 취소에 대한 새로운 커밋을 생성함
- 취소 커밋 생성할 때에는 revert 명령어 사용
- 삭제를 위한 새로운 커밋을 생성함
<img width="335" alt="image" src="https://user-images.githubusercontent.com/101856066/203334335-32f18a86-45f5-4357-a4f4-0c8cfadffe4b.png">
<img width="328" alt="image" src="https://user-images.githubusercontent.com/101856066/203334389-5ab96ebf-89ba-4a2c-ad54-01d87dc6766a.png">
<img width="325" alt="image" src="https://user-images.githubusercontent.com/101856066/203334435-89d64b70-fffe-4900-9ee0-e44db004be46.png">
<img width="188" alt="image" src="https://user-images.githubusercontent.com/101856066/203334494-05ebb71a-5d6f-419c-b40b-df473e8970e8.png">
<img width="317" alt="image" src="https://user-images.githubusercontent.com/101856066/203334706-d3d70e05-bf8e-423e-a066-da86e7d2715a.png">
<img width="198" alt="image" src="https://user-images.githubusercontent.com/101856066/203334765-8602559c-036b-4f8e-89b2-c58012b30690.png">

### 3-2. 리버트 지정
- 리버트는 한 번에 커밋 하나만 취소 가능
- 범위 지정 연산자를 사용하여 여러 커밋을 revert 할 수 있음
- 사용 예시는 git revert CommitID .. CommitID와 같이 사용

### 3-3. 소스트리에서 리버트
- 해당 커밋을 선택한 후 마우스 오른쪽 버튼을 클릭하고 커밋 되돌리기 메뉴 선택
<img width="224" alt="image" src="https://user-images.githubusercontent.com/101856066/203335131-122457e3-8405-454d-afb9-8e70081bdef5.png">
<img width="327" alt="image" src="https://user-images.githubusercontent.com/101856066/203335171-5283a040-7040-41a1-8c45-3d1908258042.png">

### 3-4. 병합 취소
- 병합한 커밋을 revert를 이용하여 취소할 수 있음
- 리셋은 방금 실행한 병합만 삭제하나 리버트는 시간 지난 후 과거의 병합을 선택하여 취소할 수 있음
<img width="326" alt="image" src="https://user-images.githubusercontent.com/101856066/203335636-25441f42-6528-4b5c-9ec2-f5f3b590fc6b.png">
<img width="196" alt="image" src="https://user-images.githubusercontent.com/101856066/203335713-3a92d998-9c5f-4f48-b914-03e028bb20b7.png">

- 병합 취소할 때에는 --mainline 옵션을 사용할 수 있음
- 병합을 취소한 후 체크아웃 되는 브랜치를 표시하며 체크아웃으로 되돌아가는 커밋 번호를 의미함.
<img width="331" alt="image" src="https://user-images.githubusercontent.com/101856066/203336267-919ab9a2-e2bf-4b26-bd59-224771aa6f56.png">
<img width="311" alt="image" src="https://user-images.githubusercontent.com/101856066/203336316-bef72d5c-629d-4abe-8cc9-464a8cc65a0d.png">
<img width="224" alt="image" src="https://user-images.githubusercontent.com/101856066/203336498-abb93063-6799-4020-97df-4b05d768fc99.png">
<img width="305" alt="image" src="https://user-images.githubusercontent.com/101856066/203336575-78bdfb2c-b6f9-4198-93c0-db9174c567ec.png">

### 3-5. 리버트 히스토리
- 새 커밋이 추가되기에 커밋 이력이 복잡해짐
- 그럼에도 불구하고 저장소가 공개되었다면 리셋보단 리버트가 유용함
