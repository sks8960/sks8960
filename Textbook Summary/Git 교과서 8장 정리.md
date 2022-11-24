# 1. 병합

### 1-1. 수동 병합
- 하나씩 직접 비교하는 방식임
- 양쪽 파일을 일일이 비교하며 바뀐점을 찾아서 적용해야함.
- 오류없이 코드를 병합하는 것은 간단하지 않고, 사람의 기억력에 대한 한계점이 명확함


### 1-2. 깃으로 자동 병합
- 복잡한 파일을 좀 더 간편하게 병합할 수 있음
- 모든 코드를 완벽하게 병합하는 것은 아니며, 이로 인해 발생하는 현상을 충돌이라고함
- 브랜치를 기준으로 병합하며, 같은 저장소 내 서로 독립적인 작업을 분리한 영역이다.
- 각각의 브랜치에서 수정된 사항을 하나의 브랜치로 병합한다. 이때 병합하려는 브랜치는 같은 로컬 저장소에 있어야 한다.

### 1-3. 병합 방식
- 병합에 있어서 상대적인 기준을 판별하는 알고리즘이 존재한다.
- Fast-Forward와, 3-way 병합 방식을 제공한다.

#### 실습 전 준비
<img width="416" alt="ㄱ" src="https://user-images.githubusercontent.com/101856066/200574247-dde5b86f-9eb3-4c81-9663-76bd5df49033.png">


# 2. Fast-Foward 병합
- 영어 표현으로 풀어쓰면 빨리감기라는 의미를 갖고있음
- 혼자 개발할 때 보통 사용함
- 생성된 커밋에 따라 순차적으로 분기되며 수정 조차도 순차적으로 될 때가 많음.
- 이러한 순차적 커밋에 맞추어 병합을 처리하는 방식임

### 2-1. 브랜치 생성 및 수정 작업
<img width="416" alt="ㄴ" src="https://user-images.githubusercontent.com/101856066/200574319-0df94778-473b-44ef-80e4-7b0348b77221.png">
<img width="185" alt="ㄷ" src="https://user-images.githubusercontent.com/101856066/200574402-b426de9a-ea91-4b09-bcf3-250dde3fbd68.png">
<img width="414" alt="ㅁ" src="https://user-images.githubusercontent.com/101856066/200574564-60cdb554-933b-47ba-a70f-ae883f6caca7.png">
<img width="411" alt="ㄹ" src="https://user-images.githubusercontent.com/101856066/200574598-330cb274-3eae-4bd1-8758-1e56f8499203.png">
<img width="369" alt="ㅂ" src="https://user-images.githubusercontent.com/101856066/200574763-82e01ee0-5db2-4246-a36f-549d913a74b9.png">

### 2-2. 병합 위치
- git의 merge 명령어는 브랜치를 병합함. 현재 브랜치를 기준으로 다른 브랜치의 모든 커밋을 병합함
- 명령어 형식은 __git merge 브랜치이름__ 형태로 사용하면 됨.
- 기준과 대상이 있어야 하는데, 기준은 체크아웃된 현재 브랜치, 대상은 병합하고자 하는 브랜치를 의미한다.
<img width="412" alt="ㅅ" src="https://user-images.githubusercontent.com/101856066/200575144-e1e7e28d-d837-46ce-8662-9e678a56d8dc.png">


### 2-3. Fast-Forward 병합 적용
- 병합 메시지에 Fast-Forward 방식으로 적용 되었다고 출력된다.
- git log를 찍어보면 작업한 브랜치의 시작 커밋을 원본 브랜치 이후의 커밋으로 가리키는 것을 확인할 수 있다.
 <img width="315" alt="ㅇ" src="https://user-images.githubusercontent.com/101856066/200575247-160b9ddc-48e9-49d1-ad7e-76e45a50c0b4.png">
 <img width="253" alt="ㅈ" src="https://user-images.githubusercontent.com/101856066/200575690-07804d3f-8c07-41d4-a50a-a089c7d22d06.png">

- 이를 통해 Fast-Forward 병합은 병합할 하나의 브랜치 파일을 기준 브랜치로 복사하여 수정된 파일을 원본에 그대로 적용한 것과 같다는 점을 알 수 있다.

# 3. 3-way 병합
- 좀 더 복잡한 병합을 처리할 수 있는 방법.
- 여러 개발자와 협업으로 작업하는 경우 대부분 3-way 병합을 사용.

### 3-1. 브랜치 생성과 수정 작업
- Fast-Forward 병합과 유사.
- Fast-Forward 병합에서는 생성한 브랜치에만 수정과 커밋을 했고, 원본 master 브랜치에서는 어떤 작업도 하지 않았다.
<img width="413" alt="ㅊ" src="https://user-images.githubusercontent.com/101856066/200575965-ef562d37-cd2c-4946-a3b1-0f2bf5444289.png">
<img width="415" alt="ㅋ" src="https://user-images.githubusercontent.com/101856066/200576018-301cbe4d-5c82-401f-8180-a3808fd77fd2.png">
<img width="232" alt="ㅌ" src="https://user-images.githubusercontent.com/101856066/200576062-27322d10-f50d-46c5-8f2d-54913b655b19.png">

### 3-2. 마스터 변경
- 기준 커밋에서 서로 다른 브랜치의 커밋이 연결됨.
<img width="410" alt="ㅍ" src="https://user-images.githubusercontent.com/101856066/200576211-2afbf5bf-354b-41aa-9c3b-8d057ccfaada.png">
<img width="414" alt="ㅎ" src="https://user-images.githubusercontent.com/101856066/200576265-bec8778e-02e6-4634-8755-8e5398a07ff9.png">
<img width="182" alt="가" src="https://user-images.githubusercontent.com/101856066/200576319-149aa91f-8478-48b1-a125-ed297f24d8e3.png">

### 3-3. 공통 조상
- 브랜치 모양이 갈라지는 형태로 나뉠 때는 Fast-Forward 방식의 알고리즘을 적용 불가하며 3-way방식을 이용하야 함.
- 두 브랜치를 병합하려면 먼저 분할 기준인 공통 커밋을 찾아야 하는데 이를 공통 조상 커밋이라 부른다.
- 공통 조상 커밋을 포함하는 브랜치와 새로운 두 브랜치, 총 3개를 하나로 병합해야한다.
- 브랜치가 3개 있다고 해서 '3-way 병합'라고 부른다.

### 3-4. 병합 커밋
- 3-way 병합은 두 브랜치에서 공통 조상 커밋을 자동으로 찾아 주며, 공통 조상 커밋을 기준으로 브랜치 병합.
- 병합을 성공적으로 완료한 후에는 새로운 커밋을 추가로 하나 생성.
- 새로 생성된 커밋을 병합 커밋이라고 부름.
- 병합 커밋은 부모 커밋이 2개라는 특징이 있다.
<img width="346" alt="나" src="https://user-images.githubusercontent.com/101856066/200576398-d627dbef-acfc-4225-b14a-a1602b651a3a.png">
<img width="219" alt="다" src="https://user-images.githubusercontent.com/101856066/200576407-c7c91494-2410-48d0-ac1b-fdc67d29cc89.png">


### 3-5. 병합 메시지
- 3-way 병합은 Fast-Forward 병합과 달리 병합 메시지가 필요.
- 깃은 두 브랜치를 병합한 후에 새로운 커밋을 하면서 동시에 메시지를 자동 생성.
- 자동으로 작성되는 메시지 외에 직접 커밋 메시지를 작성할 수 있다. merge 명령어를 실행 할 때 -e 또는 --edit 사용.
- 병합 메시지를 입력할 수 있는 vi 에디터 차잉 열림
<img width="460" alt="라" src="https://user-images.githubusercontent.com/101856066/200576520-0a33a95c-c79e-46b9-a6f5-607c06a9a412.png">
<img width="310" alt="마" src="https://user-images.githubusercontent.com/101856066/200576531-fde5b58d-242e-4c4e-813b-36a08e96e16c.png">


# 4. 브랜치 삭제

### 4-1. 병합 후 삭제
- 병합된 브랜치의 커밋은 모두 원본 브랜치에 적용.
- 중복되는 커밋을 가지는 별도의 브랜치를 유지할 필요가 없다. 따라서 불필요한 브랜치는 삭제를 해준다.
- 브랜치를 삭제할 때는 -d 옵션을 사용. -d 옵션은 병합을 완료한 브랜치만 삭제 가능.
- 병합을 완료하지 않은 브랜치를 삭제하고 싶다면 대문자 -D 옵션을 사용.
<img width="307" alt="바" src="https://user-images.githubusercontent.com/101856066/200576548-be245ad2-65bc-46ae-928c-111c533cf622.png">

# 5. 충돌

### 5-1. 충돌이 생기는 상황
- 여러 사람과 개발 작업을 하다 보면 예상외로 충돌이 자주 발생.
- 대부분의 충돌 원인은 같은 위치의 코드를 동시에 수정했기 때문.
- 파일을 수정할 때 여러 개발자가 서로 다른 위치를 수정했다면 깃에서 서로 다른 위치의 소스를 자동으로 병합하기 때문에 문제 없음.
- 하지만 파일에서 동일한 위치에 두 명 이상이 서로 다르게 수정했다면 충돌이 발생.

### 5-2. 실습을 위한 충돌 만들기
<img width="329" alt="a" src="https://user-images.githubusercontent.com/101856066/201971237-a6512e22-3184-485f-81e0-300b666309d4.png">
<img width="426" alt="b" src="https://user-images.githubusercontent.com/101856066/201971261-0d5361a6-8202-417a-9e67-bcfebdfda523.png">
<img width="317" alt="c" src="https://user-images.githubusercontent.com/101856066/201971273-0704faf6-2acc-43f9-bab7-3e87550c7570.png">
<img width="409" alt="d" src="https://user-images.githubusercontent.com/101856066/201971282-b3122056-ec69-4e5e-a0ef-c53e02d1e83f.png">
<img width="313" alt="e" src="https://user-images.githubusercontent.com/101856066/201971298-ca6cc752-af16-4b4b-907b-b5784bb4d710.png">
<img width="273" alt="f" src="https://user-images.githubusercontent.com/101856066/201971313-8f8109e3-ab3a-4e07-8654-d195ee1c412c.png">
<img width="362" alt="g" src="https://user-images.githubusercontent.com/101856066/201971322-619d79c8-1f1d-430d-92b6-24cf07cbfd0e.png">

- 자동으로 병합하지 않고 충돌이 발생.
- 자동으로 병합하는 과정에서 충돌이 발생되면 깃은 "Merge Conflicts" 메시지를 출력.
- 소스트리에서 그래프를 확인하면 충돌이 발생하여 커밋도ㅓㅣ지 않은 변경 사항이 추가.
<img width="204" alt="h" src="https://user-images.githubusercontent.com/101856066/201971153-669ff044-f238-4829-8b02-18390cd8b388.png">

- 병합 충돌이 발생하면 자동으로 커밋이 생성되지 않음.
<img width="378" alt="i" src="https://user-images.githubusercontent.com/101856066/201971042-22e70582-805e-42de-b779-61c53f6d433d.png">

- 방금 실행한 병합을 취소할 때는 --abort 옵션 실행

### 5-3. 수동으로 충돌 해결
- 병합 충돌이 발생하면 수동으로 해결해야 함.
- 직접 소스 코드를 보고 충돌된 부분을 확인한 후 코드를 수정.
<img width="386" alt="j" src="https://user-images.githubusercontent.com/101856066/201971458-cfe8a38f-22ee-47de-87a5-d9d9fc054cb6.png">
<img width="232" alt="k" src="https://user-images.githubusercontent.com/101856066/201971813-a0e60f87-1f0f-43e6-a4c3-13e8f32b414c.png">
<img width="356" alt="l" src="https://user-images.githubusercontent.com/101856066/201971841-a4ea8914-0d2e-4483-b8b4-dde3e566076f.png">

- 충돌한 내용을 수정할 때는 깃에서 표시한 충돌 기호도 함께 삭제해야 함.
- 충돌을 해결한 후 병합 커밋을 직접 만들어야 함.
- 병합 커밋을 생성하면 깃의 충돌 마크는 자동으로 없어짐.

### 5-4. 소스트리에서 충돌 해결
- 충돌이 발생하면 '스테이지에 올라간 파일'과 '스테이지에 올라가지 않은 파일' 두 영역에 파일이 표시.
- 파일을 클릭하면 충돌 메시지를 확인 가능.
- 충돌 해결 메뉴를 선택하면 다양한 해결 옵션이 보임.
- 옵션들을 사용하여 충돌을 간단하게 해결 가능.
- 하지만 가능하면 직접 수동으로 수정하는 것이 안전.
- 충돌을 해결하면 두 브랜치가 하나로 표시.

# 6. 브랜치 병합 여부 확인
- 다수 브랜치가 있을 때는 어느 브랜치가 병합 완료된 것인지 알기 힘듬
- 병합 후에 삭제하면 혼동을 줄일 수 있음
- 병합하지 않은 브랜치와 병합한 브랜치를 구분하는 옵션을 제공함.
- git branch --merged로 구분할 수 있음
- 병합하지 않은 브랜치는 --no-merged로 구분함
- 병합된 브랜치는 -d로 삭제가 되나 아닌 경우에는 -D로 강제 삭제해야 함
<img width="312" alt="m" src="https://user-images.githubusercontent.com/101856066/201971908-a8c7e59e-5e51-4c40-ae07-e7b3412f6c76.png">

# 7. 리베이스
- 브랜치를 합치는 방식에는 병합과 리베이스가 있음
- 커밋 순서를 재배열하는 것이 리베이스임

### 7-1. 베이스
- 모든 브랜치는 뿌리가 있음(master 예외)
- 특정 커밋은 브랜치가 파생된 기준이 됨
- 베이스란, 공통 조상 커밋이라고도 하는데 해당 커밋을 기준으로 커밋이 여러갈래로 갈라지는 경우를 의미함.

### 7-2. 베이스 변경
- 베이스 앞에 re라는 의미가 붙음
- 베이스 커밋을 변경하는 것을 말함
- 이를 통해 병합을 하면서 일어나는 공통 조상 커밋 찾기 과정 등을 생략할 수 있음
- 여러갈래의 커밋 진행을 일원화 하면서 쉽게 파악할 수 있음

### 7-3. 리베이스 vs 병합
- 병합은 파생된 두 브랜치를 합치는 과정
- 공통 조상 커밋을 찾고 3-way 병합을 진행해야 함
- 리베이스는 브랜치를 서로 비교하지 않고 순차적으로 병합을 진행함
- 가장 큰 차이점은 3-way 병합은 병합 커밋이 존재하지만 리베이스는 병합 커밋이 없음
- 브랜치의 마지막을 가리키는 커밋 위치가 다르다는 점도 존재함

### 7-4. 리베이스 명령어
- git rebase [브랜치] 를 사용한다
<img width="415" alt="n" src="https://user-images.githubusercontent.com/101856066/201972349-9ea06247-729e-4868-8fde-c8d7adaef173.png">
<img width="344" alt="o" src="https://user-images.githubusercontent.com/101856066/201972354-760d1cd9-b5a6-48f8-b724-7b977a8e7a58.png">
<img width="431" alt="p" src="https://user-images.githubusercontent.com/101856066/201972356-aa6c6d3e-a9b5-4823-9dc8-7bc65c65d074.png">
<img width="309" alt="q" src="https://user-images.githubusercontent.com/101856066/201972359-d66af931-a629-49c6-b131-6612c49769ef.png">
<img width="416" alt="r" src="https://user-images.githubusercontent.com/101856066/201972362-bf2ec497-7da0-4a6f-a85b-1df4a92df25c.png">
<img width="308" alt="s" src="https://user-images.githubusercontent.com/101856066/201972364-0e4e842e-eee1-4719-8c43-a816b0a8ceca.png">
<img width="251" alt="t" src="https://user-images.githubusercontent.com/101856066/201972367-12a2e218-a868-4bb2-a87c-7127280d0de4.png">

### 7-5. 리베이스 병합
- 리베이스는 병합 기준 브랜치가 merge와 반대임
- merge는 파생 브랜치에서 부터 원본 브랜치로 병합
- rebase는 원본 브랜치로부터 파생 브랜치로 병합을 진행
<img width="355" alt="u" src="https://user-images.githubusercontent.com/101856066/201972756-043526fd-1fa0-4607-8d0e-a773f226dc4f.png">

- 리베이스가 실행되면 파생 브랜치의 커밋들은 기준 브랜치의 마지막 커밋으로 재정렬됨
<img width="240" alt="v" src="https://user-images.githubusercontent.com/101856066/201972825-72e4154a-13bc-4b40-b094-959790f95781.png">


### 7-6. 리베이스 되었는지 확인
- 리베이슨느 베이스 커밋을 변경하여 병합
- 재배치 과정에서 커밋의 해시 값이 변경됨
<img width="398" alt="w" src="https://user-images.githubusercontent.com/101856066/201972886-73a1243c-7fb7-41a3-a618-24b2f9d6601f.png">

- 해시 값 중복 방지를 위해 새로운 커밋 해시를 생성함

### 7-7. 리베이스 후 브랜치
- 리베이스 이후 커밋은 정리되었으나 모양이 달라짐
- 병합 후 두 브랜치는 같은 커밋 ID 가리키는게 일반적이긴 함.
- 리베이스는 커밋 위치를 재조정하지만, HEAD포인터의 위치까지 옮겨주지는 않음
- rebase 후 HEAD 포인터를 맞춰줘야 한다는 의미
<img width="357" alt="x" src="https://user-images.githubusercontent.com/101856066/201973030-cadb74b6-b266-4161-92fe-d6be9de20e0f.png">
<img width="275" alt="y" src="https://user-images.githubusercontent.com/101856066/201973093-90320c16-ac67-44e7-9034-0eea469892ad.png">

- 리베이스 이후 실행한 병합 메시지를 보면 Fast-forward 방식으로 병합을 했다는 것을 알 수 있음
- 리베이스 및 병합을 완료하면 필요없는 브랜치는 삭제

### 7-8. 충돌과 해결
- 리베이스 역시 병합 과정에서 충돌이 발생할 수 있음
- 사용자가 직접 수동으로 충돌을 해결해야 함
<img width="410" alt="z" src="https://user-images.githubusercontent.com/101856066/201973296-a23c6a03-b279-434e-bdc6-41c282cbea44.png">
<img width="424" alt="aa" src="https://user-images.githubusercontent.com/101856066/201973392-9050421a-ab82-4738-a5c4-9284c7a3f13b.png">
<img width="307" alt="bb" src="https://user-images.githubusercontent.com/101856066/201973417-2fe77486-919c-4515-b740-b3c20c9725d6.png">
<img width="428" alt="cc" src="https://user-images.githubusercontent.com/101856066/201973470-a348fc3b-725f-47a8-b22d-183e4f14ef0f.png">
<img width="321" alt="dd" src="https://user-images.githubusercontent.com/101856066/201973504-369e2157-d9f2-4dde-89bd-cb023193ca31.png">

<img width="496" alt="ee" src="https://user-images.githubusercontent.com/101856066/201973578-561aa11c-24e8-49fc-b230-bf4029fadc07.png">
<img width="386" alt="ff" src="https://user-images.githubusercontent.com/101856066/201973637-81295f8d-7cab-4efb-a742-7e33f7a71389.png">
<img width="413" alt="gg" src="https://user-images.githubusercontent.com/101856066/201973689-42d09c87-c0ad-454e-8140-6c6fdd19a2a3.png">

- 리베이스는 커밋을 하나씩 따라가면서 위치를 재조정함. 충돌을 수정한 후에는 rebase 명령어와 --continue 옵션을 사용
<img width="495" alt="hh" src="https://user-images.githubusercontent.com/101856066/201973722-05f3fe49-4708-4545-9c9f-f6d1db8fdbd6.png">

- 리베이스를 취소하고 싶다면 rebase --abort를 사용하면 된다.
- --skip 옵션으로 특정 충돌을 제외할 수 있으나 추천하는 방법은 아님

### 7-9. 커밋 수정
- 마지막 커밋은 --amend 옵션으로 수정할 수 있다.
- 리베이스는 커밋 위치를 재조정하여 병합과 유사한 효과를 보임(실제 병합은 아님)
- 여러 커밋을 한 커밋으로 묶을 수도 있음 이때는 -i 옵션을 사용하면 됨
<img width="354" alt="ii" src="https://user-images.githubusercontent.com/101856066/201973939-4f8aa4cb-bafa-4029-9c4e-a177978abd0a.png">
<img width="232" alt="jj" src="https://user-images.githubusercontent.com/101856066/201974025-c3eaa54f-8bd7-4c77-844d-d99ae27d8290.png">
<img width="344" alt="kk" src="https://user-images.githubusercontent.com/101856066/201974085-b272ad9d-d188-4ebc-88ed-42c985cf0396.png">

- 이를 입력하면 메시지를 입력할 수 있는 vi 에디터가 실행됨. 정보 또한 자동으로 작성됨
- 합친 커밋에는 새 해시 값이 부여됨

### 7-10. 리베이스할 때 주의점
- 리베이스는 커밋 위치와 해시 값을 변경함.
- 저장소를 외부에 공개했다면 공개 순간부터 커밋은 리베이스를 사용하지 않는 것을 원칙으로 함
- 외부로 코드 푸시 및 공개 전에 로컬에서만 실행하는 것이 좋음
- 커밋 위치와 해시 값이 변경되기 때문에 혼란을 야기할 수 있음
- 공개 커밋 변경 시에는 revert를 사용함.(다음에 구체적으로 언급)


