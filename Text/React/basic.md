# 리액트(React)

- 페이스북에서 개발한 오픈소스 JavaScript 라이브러리인 React는 사용자 인터페이스(UI)를 만들기 위하여 사용되며, 웹 애플리케이션의 구성 요소를 만들고 관리하는 데에 도움이 됩니다.

<br>

### 리액트의 원리

1. 가상 DOM (Virtual DOM): React는 가상 DOM을 사용하여 UI를 효율적으로 업데이트합니다. 변경 사항은 먼저 가상 DOM에 반영되고, 이후에 실제 DOM에 반영됩니다. 이를 통해 성능이 향상되고 불필요한 DOM 조작을 최소화합니다.

2. 컴포넌트 기반 아키텍처: React는 UI를 독립적인 컴포넌트로 나누어 개발합니다. 각 컴포넌트는 자체적으로 상태를 관리하고 UI를 렌더링합니다. 이를 통해 재사용성이 높아지고 유지보수가 쉬워집니다.

3. 단방향 데이터 흐름: React는 단방향 데이터 흐름을 따릅니다. 부모 컴포넌트에서 자식 컴포넌트로 데이터가 전달되는 방식으로, 데이터의 흐름이 명확해지고 예측 가능성이 높아집니다.

<br>

### 리액트의 특징

1. JSX 문법: React는 JSX 문법을 사용하여 JavaScript 코드 안에 마크업을 작성할 수 있습니다. 이를 통해 UI를 선언적이고 간결하게 작성할 수 있습니다.

2. 단일 페이지 애플리케이션 (SPA) 지원: React는 SPA를 구축하는 데에 적합한 라이브러리입니다. 페이지 전환 시에도 페이지 전체를 다시 렌더링하지 않고 필요한 부분만 업데이트하여 사용자 경험을 향상시킵니다.

<br>

### 리액트의 장단점

- 장점: 가상 DOM을 통한 업데이트와 단방향 데이터 흐름을 통해 성능을 향상 시킬 수 있고, 컴포넌트 기반 아키텍처를 통해 코드의 재사용성이 높아지고 유지보수가 쉬워집니다.

- 단점: SEO (검색 엔진 최적화) 문제가 있습니다. SPA의 경우 초기 렌더링이 서버 측에서 이루어지지 않을 경우에는 검색 엔진 최적화에 어려움이 있을 수 있습니다.

<br>

### 가상 DOM(Virtual DOM)이란?

- 가상 DOM(Virtual DOM)은 실제 DOM(Document Object Model)의 가벼운 복사본이라고 생각할 수 있습니다. React에서 UI 업데이트를 효과적으로 하기위해 도입된 개념 입니다.

- 실제 DOM은 웹 페이지의 구조를 표현하는 트리 구조로, HTML 요소들을 나타냅니다. DOM은 웹 페이지의 상호작용 및 시각적 표현을 담당하는 핵심 요소입니다. 

- 그러나 실제 DOM을 직접 조작하는 것은 성능상의 문제가 발생할 수 있습니다. 특히 대규모 애플리케이션에서는 DOM 조작이 느려질 수 있고, 이로 인해 사용자 경험이 저하될 수 있습니다.

- 가상 DOM은 이러한 문제를 해결하기 위해 도입되었습니다. 가상 DOM은 실제 DOM의 가벼운 복사본으로, 메모리 상에 존재하며 React 라이브러리에서 관리 됩니다. 

- 가상 DOM은 React 컴포넌트의 상태 변화에 따라 실제 DOM과 동기화되며, 변경 사항을 일괄적으로 처리하여 성능을 향상시킵니다.

- React에서는 가상 DOM을 사용하여 UI를 업데이트할 때, 변경된 부분만 실제 DOM에 반영함으로써 불필요한 DOM 조작을 최소화합니다. 이는 웹 애플리케이션의 성능을 향상시키고 사용자 경험을 개선하는 데 도움이 됩니다.

<br>

#### 왜 실제 DOM을 조작하면 성능 저하가 일어나는가?

- DOM은 웹 페이지의 구조를 나타내는 트리 구조이며, 실제로 브라우저가 렌더링하고 조작하는 데에는 상당한 비용이 듭니다. 

- DOM을 직접 조작할 때마다 브라우저는 레이아웃(layout)과 리플로우(reflow)를 수행하여 변경 사항을 반영하고 화면을 다시 그리는 과정이 필요합니다.

- 특히 반복문과 같이 DOM을 반복적으로 조작하는 경우, 브라우저는 매번 레이아웃을 다시 계산하고 화면을 다시 그리는 작업을 수행해야 합니다. 이는 성능을 저하시키는 원인이 됩니다.

<br>

#### 왜 가상 DOM을 조작하는건 성능에 영향을 끼치지 않는가?

- 가상 DOM은 실제 DOM의 가벼운 복사본으로 메모리 상에서 동작하며, 브라우저의 렌더링 엔진과 직접 상호작용하지 않기 때문입니다.

<br>

#### 가상 DOM에 변경 사항을 적용하고 실제 DOM에 반영하는 과정

1. 상태 변경 감지: React 라이브러리는 상태(state)가 변경될 때마다 가상 DOM을 업데이트합니다.

2. 가상 DOM 업데이트: 변경된 상태를 기반으로 가상 DOM이 업데이트되고, 변경된 부분만을 실제 DOM과 비교합니다.

3. DOM 변경 사항 식별: 가상 DOM과 실제 DOM을 비교하여 변경된 요소를 식별합니다.

4. 실제 DOM 업데이트: 변경된 부분만을 실제 DOM에 반영하여 레이아웃 계산과 화면 다시 그리기를 최소화합니다. 이 과정은 브라우저의 렌더링 엔진에 의해 처리됩니다.

<br>

### JSX(JavaScript XML)

- JSX(JavaScript XML)는 JavaScript의 확장 문법으로, React에서 UI를 작성할 때 사용됩니다. JSX는 HTML과 유사한 문법을 가지고 있으며, JavaScript의 표현식을 포함할 수 있습니다.

1. HTML과 유사한 문법: JSX는 HTML과 매우 유사한 문법을 가지고 있어, 기존에 웹 개발에서 익숙한 사람들이 쉽게 사용할 수 있습니다. 예를 들어, div나 span과 같은 HTML 요소를 사용하여 UI를 작성할 수 있습니다.

2. JavaScript 표현식 포함: JSX 내에서 중괄호({})를 사용하여 JavaScript 표현식을 포함할 수 있습니다. 이를 통해 동적인 값이나 JavaScript의 변수, 함수 등을 JSX에 포함시킬 수 있습니다.

3. 컴파일 과정: JSX는 브라우저가 이해할 수 있는 JavaScript로 컴파일되어야 합니다. 이를 위해 Babel과 같은 도구를 사용하여 JSX 코드를 일반적인 JavaScript 코드로 변환합니다. 이러한 변환 과정을 거치면 JSX 코드는 React.createElement() 함수 호출로 변환되어 React 엘리먼트를 생성합니다.

4. 가독성과 유지보수성 향상: JSX를 사용하면 UI를 선언적이고 가독성 있게 작성할 수 있습니다. HTML과 JavaScript가 함께 사용되므로 코드의 일관성을 유지하고 유지보수성을 향상시킬 수 있습니다.

<br>

### 엘리먼트(Element) & 컴포넌트(Component)의 차이점

- 엘리먼트(Element)는 React 애플리케이션에서 UI를 구성하는 기본적인 요소입니다. div 또는 span 과 같은 HTML 태크를 엘리먼트라고 합니다.

- React 엘리먼트는 React.createElement() 함수를 사용하여 생성할 수도 있습니다. 애플리케이션에서 실제로 화면에 렌더링되는 가상의 DOM 요소를 나타냅니다.

- 컴포넌트(Component)는 UI를 독립적이고 재사용 가능한 단위로 나누어 구성하는데 사용됩니다.

- 일반적으로 함수형 컴포넌트(Functional Component) 또는 클래스형 컴포넌트(Class Component)로 정의됩니다.

- JSX 문법을 사용하여 컴포넌트를 작성하고, 프로퍼티(props)와 상태(state)를 가질 수 있으며, 이를 통해 동적인 UI를 구성하고 관리할 수 있습니다.

- 컴포넌트는 엘리먼트의 집합으로 이루어져 있습니다. 따라서 컴포넌트 안에 엘리먼트를 포함하여 UI를 작성합니다.

- 엘리먼트는 UI의 기본 요소 => 엘리먼트가 모여서 컴포넌트가 됨(재사용이 가능한 단위) => 필요에 따라 상태 & 프로퍼티를 관리하여 동적  UI 구현.

<br>

### 리액트에서 컴포넌트를 만드는 방법?

- React에서 컴포넌트를 생성하는 방법은 크게 두 가지입니다: 함수형 컴포넌트(Functional Component)와 클래스형 컴포넌트(Class Component)입니다.

- 함수형 컴포넌트(Functional Component): 함수형 컴포넌트는 함수로 정의되며, props를 인자로 받아 JSX를 반환하는 방식으로 작성됩니다. 

- 간단하고 명확한 구조로 코드를 작성할 수 있으며, 최신 React 버전에서는 훅(Hook)을 사용하여 상태와 생명주기 기능을 함수형 컴포넌트에서도 사용할 수 있습니다.

- 클래스형 컴포넌트(Class Component): 클래스형 컴포넌트는 ES6의 클래스로 정의되며, React.Component 클래스를 상속받아 작성됩니다. 

- 클래스형 컴포넌트는 render() 메서드를 포함하고, render() 메서드 내에서 JSX를 반환하여 UI를 정의합니다.

```
// 클래스형 간단 예시

import React, { Component } from 'react';

class ClassComponent extends Component {
  render() {
    return <div>Hello, {this.props.name}!</div>;
  }
}

export default ClassComponent;

```

- 생성된 컴포넌트들은 다른 파일에서 import 하여 사용할 수 있습니다. 

<br>

### 함수형과 클래스형의 차이점?

1. 구현방식
  - 함수형 컴포넌트는 함수로 정의되며, props를 인자로 받아 JSX를 반환하는 방식으로 작성됩니다. 
  - 클래스형 컴포넌트는 ES6의 클래스로 정의되며, React.Component 클래스를 상속받아 작성됩니다. render() 메서드를 포함하고, 이 메서드 내에서 JSX를 반환하여 UI를 정의합니다.

2. 상태(State)와 생명주기(Lifecycle)
  - 함수형 컴포넌트: 이전에는 상태와 생명주기 기능을 사용할 수 없었지만, React Hooks가 도입되면서 함수형 컴포넌트에서도 상태와 생명주기 기능을 사용할 수 있게 되었습니다. useState, useEffect와 같은 훅을 사용하여 상태 관리와 생명주기 기능을 구현할 수 있습니다.
  - 클래스형 컴포넌트는 상태(state)를 가질 수 있고, this.state를 통해 상태를 초기화하고 변경할 수 있습니다. 또한 생명주기 메서드를 사용하여 컴포넌트의 생명주기 이벤트를 처리할 수 있습니다.

3. 코드 구조
  - 함수형 컴포넌트: 간결하고 명확한 구조로 코드를 작성할 수 있습니다. 상태와 생명주기 메서드가 없기 때문에 코드가 더 단순하게 유지될 수 있습니다.
  - 클래스형 컴포넌트: 상태와 생명주기 메서드를 클래스 내에 정의하기 때문에 코드가 조금 더 복잡할 수 있습니다. 하지만 클래스형 컴포넌트는 더 많은 기능을 제공하므로 복잡한 UI나 상태 관리가 필요한 경우에 적합합니다.

<br>

### 리액트의 생명주기(Lifecycle)

- 컴포넌트가 생성되고 소멸되는 과정에서 발생하는 여러 이벤트를 의미합니다. 각 라이프사이클 이벤트는 특정한 시점에 호출되는 메서드로, 컴포넌트의 상태 변화나 UI 업데이트 등을 처리할 수 있도록 도와줍니다.

- 컴포넌트의 수명은 페이지에 렌더링 되기 전인 준비 과정 => 페이지에서 사라질 때 까지 입니다.

<img src="../../Images/React/reactlifecycle.png" />

- 리액트의 생명주기는 크게 세 가지로 나눌 수 있습니다. 

1. 마운팅(Mounting) 라이프사이클: 컴포넌트가 DOM에 삽입되는 과정을 다룹니다. 마운팅 라이프사이클 메서드는 컴포넌트가 생성되고 처음으로 렌더링될 때 호출됩니다.
  - 주요 메서드: constructor(), static getDerivedStateFromProps(), render(), componentDidMount()

2. 업데이팅(Updating) 라이프사이클: 컴포넌트의 속성(props)이나 상태(state)가 변경되어 UI를 업데이트하는 과정을 다룹니다. 업데이팅 라이프사이클 메서드는 컴포넌트의 속성이나 상태가 변경될 때 호출됩니다.
  - 주요 메서드: static getDerivedStateFromProps(), shouldComponentUpdate(), render(), getSnapshotBeforeUpdate(), componentDidUpdate()

3. 언마운팅(Unmounting) 라이프사이클: 컴포넌트가 DOM에서 제거되는 과정을 다룹니다. 언마운팅 라이프사이클 메서드는 컴포넌트가 제거되기 전에 호출됩니다.
  - 주요 메서드: componentWillUnmount()

- 외에도 리액트에는 라이프사이클 이벤트가 호출되기 전과 후에 실행되는 추가적인 메서드들이 있습니다. 

- 예를 들어, 에러가 발생했을 때 처리하는 componentDidCatch() 메서드나 라이프사이클 이벤트 호출 전에 발생하는 getDerivedStateFromError() 메서드 등이 있습니다.

- 라이프사이클을 이해하고 활용하면 컴포넌트의 동작을 더욱 세밀하게 제어하고, 성능을 최적화할 수 있습니다.

- 그러나 최신 버전의 React에서는 클래스형 컴포넌트보다는 함수형 컴포넌트와 React Hooks를 사용하는 것이 권장 됩니다. 이러한 라이프사이클 메서드들은 주로 클래스형 컴포넌트에서 사용됩니다.

<br>

### 함수형 컴포넌트의 Hooks 를 사용한 상태(useState) & 생명주기(useEffect)

- useState 훅을 사용한 상태관리: 함수형 컴포넌트 내에서 상태를 선언하고 변경할 수 있습니다. useState 훅은 배열을 반환하며, 첫 번째 요소는 상태 값이고, 두 번째 요소는 상태 값을 변경하는 함수입니다.

```
// useState 예시

import React, { useState } from 'react';

function FunctionalComponent() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

export default FunctionalComponent;
```

- useEffect 훅을 사용하여 생명주기 이벤트 처리: 함수형 컴포넌트 내에서 생명주기와 비슷한 동작을 처리할 수 있습니다. useEffect 훅은 컴포넌트가 렌더링될 때마다 실행되며, 두 번째 매개변수로 전달된 배열에 의해 의존성이 결정됩니다.

```
// useEffect 예시

import React, { useState, useEffect } from 'react';

function FunctionalComponent() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    // componentDidMount와 componentDidUpdate 역할을 수행
    console.log('Component has been mounted or count has been updated.');
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

export default FunctionalComponent;
```

- useEffect 훅의 두 번째 매개변수로 전달된 배열에는 의존성 목록을 지정할 수 있습니다. 

- 이 배열에 포함된 값들이 변경될 때마다 useEffect 콜백 함수가 호출됩니다. 만약 빈 배열을 전달하면 컴포넌트가 마운트될 때만 useEffect 콜백 함수가 호출됩니다.

<br>

### React Hooks

- React Hooks는 React v16.8에서 도입된 기능으로, 함수형 컴포넌트에서 상태(state)와 다른 React 기능들을 사용할 수 있게 해주는 API입니다. 

- Hooks를 사용하면 클래스형 컴포넌트를 작성하지 않고도 상태 관리, 생명주기 메서드, 컨텍스트(Context), 레퍼(ref) 등의 기능을 함수형 컴포넌트에서 사용할 수 있습니다. 

- 코드를 더 간결하고 재사용 가능하게 만들고, 클래스의 사용을 피하면서도 동일한 기능을 제공합니다. 다음과 같은 주요 Hooks가 있습니다.

#### 기본 Hooks

1. useState: [useState](https://ko.legacy.reactjs.org/docs/hooks-reference.html#usestate) 훅은 함수형 컴포넌트 내에서 상태를 추가하고 관리할 수 있도록 해줍니다. 이 훅을 사용하면 클래스형 컴포넌트의 this.state와 this.setState 메서드와 비슷한 동작을 수행할 수 있습니다.

2. useEffect: [useEffect](https://ko.legacy.reactjs.org/docs/hooks-reference.html#useeffect) 훅은 부수 효과(side effect)를 수행할 수 있도록 해줍니다. 이 훅을 사용하여 컴포넌트가 렌더링될 때나 상태가 업데이트될 때 특정한 동작을 수행할 수 있습니다. componentDidMount, componentDidUpdate, componentWillUnmount와 비슷한 역할을 합니다.

3. useContext: [useContext](https://ko.legacy.reactjs.org/docs/hooks-reference.html#usecontext) 훅은 React의 컨텍스트(Context)를 사용할 수 있도록 해줍니다. 이 훅을 사용하여 컴포넌트 트리 상에서 전역적인 데이터를 전달할 수 있습니다.


#### 추가 Hooks

4. useRef: [useRef](https://ko.legacy.reactjs.org/docs/hooks-reference.html#useref) 훅은 ref를 생성하고 다룰 수 있도록 해줍니다. 이 훅을 사용하여 DOM 요소에 직접 접근하거나 컴포넌트의 인스턴스 변수를 저장할 수 있습니다.

5. useReducer: [useReducer](https://ko.legacy.reactjs.org/docs/hooks-reference.html#usereducer) 훅은 Redux와 비슷한 방식으로 상태를 관리할 수 있도록 해줍니다. 이 훅을 사용하여 복잡한 상태 로직을 분리하고 관리할 수 있습니다.

- 외에도 다양한 특수 목적을 위한 Hooks 가 있으며 사용자 정의 훅을 만들어서 컴포넌트 로직을 재사용할 수도 있습니다.

<br>

### useEffect => componentDidMount, componentDidUpdate, componentWillUnmount

- 함수형 컴포넌트에서 클래스형 컴포넌트의 라이프사이클 메서드를 비슷하게 구현할 수 있는 방법의 예시로 React Hooks의 useEffect를 들어보겠습니다.

1. componentDidMount: 클래스형 컴포넌트에서 componentDidMount는 컴포넌트가 처음으로 렌더링 된 후 한번만 실행되는 메서드 입니다. 초기화 또는 외부 데이터 로딩에 사용됩니다.

- 함수형 컴포넌트에서 componentDidMount에 해당하는 동작은 useEffect 훅의 두 번째 인자로 빈 배열을 전달하여 구현할 수 있습니다. 이렇게 하면 컴포넌트가 처음으로 렌더링될 때 한 번만 실행되는 효과를 얻을 수 있습니다.

```
useEffect(() => {
  // componentDidMount
}, []);
```

2. componentDidUpdate: 클래스형 컴포넌트에서 componentDidUpdate는 컴포넌트가 업데이트될 때마다 실행되는 메서드입니다. 주로 이전 props나 state와 현재 props나 state를 비교하여 변경 사항을 처리하는데 사용됩니다. 

```
useEffect(() => {
  // componentDidUpdate
}, [update]);
```

- 함수형 컴포넌트에서 componentDidUpdate에 해당하는 동작은 useEffect 훅의 두 번째 인자로 특정 state나 props를 전달하여 구현할 수 있습니다. 이렇게 하면 해당 state나 props가 변경될 때마다 실행되는 효과를 얻을 수 있습니다.

3. componentWillUnmount: 클래스형 컴포넌트에서 componentWillUnmount는 컴포넌트가 제거되기 직전에 실행되는 메서드입니다. 주로 이벤트 리스너 해제나 타이머 제거 등의 정리 작업에 사용됩니다.

- 함수형 컴포넌트에서 componentWillUnmount에 해당하는 동작은 useEffect 훅의 반환 함수로 구현할 수 있습니다. 이렇게 하면 컴포넌트가 언마운트될 때 실행되는 효과를 얻을 수 있습니다.

```
useEffect(() => {
  return () => {
    // componentDidUnmount
  };
}, []);
```

<br>

