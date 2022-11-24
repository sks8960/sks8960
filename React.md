## React

### React란
- UI 자바스크립트 라이브러리로써 싱글 페이지 애플리케이션의 UI(User Interface)를 생성하는데 집중한 라이브러리이다.
- 자바스크립트에 HTML을 포함하는 JSX(JavaScript XML)이라는 간단한 문법과 단방향 데이터 바인딩(One-way Data Binding)을 사용하고 있다.
- 가상 돔(Virtual DOM)이라는 개념을 사용하여 웹 애플리케이션의 퍼포먼스를 최적화한 라이브러리이다.
![image](https://user-images.githubusercontent.com/101856066/203021759-f781f308-a9a0-446b-bcfe-53253b6c5d6a.png)


### React의 특징
1. Data Flow
 - React는 데이터의 흐름이 한 방향으로만 흐르는 단방향 데이터 흐름을 가진다.
 - Augular.js와 같은 양방향 데이터 바인딩은 규모가 커질수록(대규모 애플리케이션의 경우) 데이터의 흐름을 추적하기가 힘들고 복잡해지는 경향이 있어, 복잡한 앱에서도 데이터 흐름에서 일어나는 변화를 보다 예측 가능할 수 있도록 단방향 흐름을 가지도록 했다고한다.
2. Component 기반 구조
  - React는 UI(View)를 여러 컴포넌트(component)를 쪼개서 만든다.
  - 한 페이지 내에서도 여러 각 부분을 독립된 컴포넌트로 만들고, 이 컴포넌트를 조립해 화면을 구성한다.
  - 컴포넌트 단위로 쪼개져 있기 때문에, 전체 코드를 파악하기가 상대적으로 쉬우며, 재상용성이 높다.
  - 따라서 코드는 반복해 입력할 필요 없이, 컴포넌트만 import해 사용하면 된다는 간편함이 있으며, 애플리케이션이 복잡해지더라도 코드의 유지보수, 관리가 용이해지는 장점을 가진다.
  
3. Virtual DOM
  - DOM은 Document Object Model의 약자이며, html, xml, CSS 등을 트리 구조로 인식하고, 데이터를 객체로 간주하고 관리한다.
  - React는 이 DOM Tree 구조와 같은 구조체를 Virtual DOM으로 가지고 있다.
  - 이벤트가 발생할 때마다 Virtual DOM을 만들고, 다시 그릴 때마다 실제 DOM과 비교하고 전후 상태를 비교해, 변경이 필요한 최소한의 변경사항만 실제 DOM에 반영해, 앱의 효율성과 속도를 개선할 수 있다.
4. Props and state
  - Props
    - Props란 부모 컴포넌트에서 자식 컴포넌트로 전달해 주는 데이터이다.
    - 자식 컴포넌트에서 전달받은 props는 변경이 불가능하고 props를 전달해준 최상위 부모 컴포넌트만 props를 변경할 수 있다.
  - State
    - State는 컴포넌트 내부에서 선언하며 내부에서 값을 변경할 수 있다.
    - 동적인 데이터를 다룰 때 사용하며, 사용자와의 상호작용을 통해 데이터를 동적으로 변경할 때 사용한다.
    - 래스형 컴포넌트에서만 사용할 수 있고, 각각의 state는 독립적이다.
5. JSX
  - 자바스크립트와 HTML을 동시에 사용하며, HTML에 자바스크립트의 변수들을 바로 사용할 수 있는 일종의 템플릿 언어(Template language)이다.  
  ![image](https://user-images.githubusercontent.com/101856066/203021605-ce6d402c-7bb1-4758-b0c0-70f05af6e4e7.png)
  - 위와 같이 자바스크립트에서 HTML 태그를 사용할 수 있으며, 자바스크립트 변수를 HTML 태그에서 바로 호출하여 사용할 수 있다.
  - React가 더욱 도움이 되는 에러 및 경고 메시지를 표시할 수 있게 해준다.