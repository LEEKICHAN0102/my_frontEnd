# React의 상태 관리(State Management) 라이브러리

- 리액트(React)에서 상태 관리란 컴포넌트의 상태(state)를 효율적으로 관리하고 업데이트하는 방법을 의미합니다. 상태는 컴포넌트의 동작과 UI 렌더링을 결정하는 중요한 데이터를 말합니다.

- 상태 관리를 통해 UI 일관성 유지, 컴포넌트 간의 데이터 공유, 애플리케이션의 예측 가능성 증가, 성능 최적화, 코드 구조의 명확성 등의 효과를 얻을 수 있으며 상태관리의 방법을 간단하게 표현하자면 다음과 같이 나뉘게 됩니다.

<br>

```
- 상태 관리의 방법들

- 로컬 상태 관리: 상태가 한 컴포넌트 내에서만 필요한 경우, useState 훅을 사용하여 관리합니다.

- 전역 상태 관리: 여러 컴포넌트에서 상태를 공유해야 할 경우, Context API, Redux, Recoil, Jotai, Zustand 등의 라이브러리를 사용합니다.

- 서버 상태 관리: 서버에서 데이터를 가져오고 이를 관리할 필요가 있을 경우, React Query와 같은 라이브러리를 사용합니다.
```

- 이러한 상태 관리 방법들 중 다양한 라이브러리들에 대해서 공식문서를 읽고 제가 알게 된 내용들에 대하여 다루어보도록 하겠습니다.

<br>

### npm Trends로 살펴본 상태관리 라이브러리들

<img src="/Images/React/image.png" />

<br>

- npm trends를 통하여 찾아본 상태관리 라이브러리들의 최근 1년간의 다운로드 건 수를 그래프로 나타낸 표입니다.  예상대로 react-redux가 1등을 그리고 Zustand, react-query, jotai와 recoil은 거의 동일 선상에 위치한 것을 확인할 수 있습니다.

- 개발자들이 상태관리 라이브러리를 선택하는 기준은 여러가지가 있습니다. 최근 기술 트렌드를 따라가거나, 패키지의 크키, 러닝커브, 커뮤니티 크기 등의 이유가 있는데 왜 위와 같은 결과로 나타난건지 라이브러리들의 장점과 단점을 알아보겠습니다. 

<br>

### react-redux

- 가장 먼저 알아볼 것은 [react-redux](https://react-redux.js.org/) 입니다. 가장 많이 사용되는 라이브러리 중 하나이며 어떤 특징을 가지는지에 대하여 알아봅시다.

- react-redux 는 Redux 패턴(flux 패턴에 영감을 받은)을 따릅니다. Redux 패턴은 JavaScript 애플리케이션에서 상태 관리를 위해 설계된 아키텍처 패턴입니다. 단일 스토어에 애플리케이션의 모든 상태를 중앙 집중식으로 저장하고, 상태 변경이 예측 가능하도록 만들어줍니다. 이 패턴은 단일 방향 데이터 흐름을 따르며, 이를 통해 상태 관리의 복잡성을 줄이고 디버깅을 용이하게 합니다.

- Redux와 flux 패턴의 차이점을 간단하게 보면 Redux는 Flux 패턴의 영감을 받아 개발되었지만, 더 단순하고 유연한 상태 관리를 위해 Flux 패턴을 개선하였습니다. Redux는 단일 스토어, 불변성, 중앙 집중식 리듀서 등의 특징을 갖추고 있으며, 이러한 특징들은 Flux 패턴과는 조금 다릅니다.

<br>

```
npm install @reduxjs/toolkit react-redux // npm 설치 명령어

- 스토어(Store): 애플리케이션의 모든 상태를 저장하는 객체입니다. 단일 스토어 패턴을 따르며, 상태 트리가 하나의 스토어에 저장됩니다.

- 액션(Action): 상태를 변경하기 위한 의도를 나타내는 객체입니다. 액션은 type 필드와 선택적인 페이로드를 포함합니다.

- 리듀서(Reducer): 액션을 처리하여 새로운 상태를 반환하는 순수 함수입니다. 이전 상태와 액션을 입력으로 받아 새로운 상태를 반환합니다.

- 디스패치(Dispatch): 액션을 스토어에 보내는 함수입니다. store.dispatch(action) 형태로 사용합니다.

- 셀렉터(Selector): 상태 트리에서 특정 데이터를 추출하는 함수입니다.
```

- Redux의 주요 개념은 위와 같이 나뉘며 각각 어떻게 사용 되는지에 대하여 알아봅시다. 

1. Store

- 보통 src/app/store.js 라는 파일을 생성하여 작성합니다. configureStore API 객체를 "Redux Toolkit" 에서 호출하여 비어있는 Redux 저장소를 만들고 내보내는 것부터 시작합니다. 

```
// src/app/store.js

import { configureStore } from '@reduxjs/toolkit'

export default configureStore({
  reducer: {},
})
```

- 위와 같이 작성하였을 경우 Redux 저장소가 생성되고, 개발 중에 저장소를 검사할 수 있도록 Redux DevTools 확장도 자동으로 구성됩니다.

2. Provider

- 스토어가 생성되면 `<Provider>`애플리케이션 주변에 React Redux를 배치하여 React 구성 요소에서 이를 사용할 수 있도록 할 수 있습니다. src/index.js 에서 방금 생성한 Redux 스토어 import 하여 `<Provider>`의 props 으로 store 를 사용합니다. 

```
// src/index.js

import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App'
import store from './app/store'
import { Provider } from 'react-redux'

// As of React 18
const root = ReactDOM.createRoot(document.getElementById('root'))

root.render(
  <Provider store={store}>
    <App />
  </Provider>,
)
```

- 이제 `<App />` 에서 기본적으로 전역 상태 관리를 사용할 준비가 되었습니다. 이제 createSlice 를 사용할 차례 입니다.

<br>

3. createSlice

- Redux의 slice는 Redux Toolkit에서 제공하는 기능으로, Redux 상태 관리의 복잡성을 줄이고 개발 생산성을 높이기 위해 설계되었습니다. createSlice 함수는 상태(slice)를 정의하고 액션 및 리듀서를 생성하는 간편한 방법을 제공합니다.

```
// src/features/counter/counterSlice.js

import { createSlice } from '@reduxjs/toolkit'

export const counterSlice = createSlice({
  name: 'counter', // 이 slice의 이름을 정의합니다. 액션타입을 구분하는데 사용
  initialState: {
    value: 0, // 초기 상태 정의 counterSlice 밖에서 초기화 한 뒤 객체에서 사용할 수도 있습니다.
  },
  reducers: {
    increment: (state) => {
      // Redux Toolkit은 리듀서에서 "변이" 로직을 작성할 수 있게 해줍니다.
      // 실제로 상태를 변이시키지는 않는데, 이는 Immer 라이브러리를 사용하기 때문입니다.
      // Immer는 "초안 상태(draft state)"에 대한 변경 사항을 감지하고, 
      // 이러한 변경 사항을 기반으로 새로운 불변 상태를 생성합니다.
      // 또한, 이러한 함수들에서는 반환문이 필요하지 않습니다.
      state.value += 1
    },
    decrement: (state) => {
      state.value -= 1
    },
    incrementByAmount: (state, action) => {
      state.value += action.payload
    },
  },
})

// 액션 생성자와 리듀서를 export
export const { increment, decrement, incrementByAmount } = counterSlice.actions

export default counterSlice.reducer
```

<br>

- 생성된 reducer를 export 하였으니 이전에 생성한 스토어에서 sliceReducer를 추가해봅시다. 

```
import { configureStore } from '@reduxjs/toolkit'
import counterReducer from '../features/counter/counterSlice'

export default configureStore({
  reducer: {
    counter: counterReducer,
  },
})
```

<br>

4. useSelector & useDispatch

- 이제 React Redux hooks를 사용하여 React 구성 요소가 Redux 저장소와 상호 작용할 수 있습니다. 

```
import React from 'react'
import { useSelector, useDispatch } from 'react-redux'
import { decrement, increment } from './counterSlice'

export function Counter() {
  const count = useSelector((state) => state.counter.value)
  const dispatch = useDispatch()

  return (
    <div>
      <div>
        <button
          onClick={() => dispatch(increment())} // useDispatch를 사용하여 reducer 함수를 호출
        >
          Increment
        </button>
        <span>{count}</span> // useSelector를 사용하여 store의 데이터를 읽어옴
        <button
          onClick={() => dispatch(decrement())} // useDispatch를 사용하여 reducer 함수를 호출
        >
          Decrement
        </button>
      </div>
    </div>
  )
}
```

- 위와 같이 React Redux hooks인 useSelector와 useDispatch를 사용하여 store에 저장 되어진 상태(count)를 가져오고 그 상태를 바꾸는 리듀서 함수를 useDispatch를 사용하여 호출하고 사용할 수 있습니다. hooks에는 이외에도 다른 것들이 존재하나 기본적인 사용방법에 대해서만 간략하게 알아보았습니다.

<br>

5. 간단 요약

- configureStore를 사용하여 Redux 저장소 생성(관례적으로 store 라는 이름의 폴더를 만들어 store.js | ts 라는 이름으로 생성함).

- `<App />` 에서 적용하기 위하여 감싸고 있는 Provider의 props 으로 store를 사용해야함. 기본적인 사용 준비

- createSlice를 생성. 이 곳에서는 초기 상태(initial state), 상태를 업데이트하는 함수(reducer 객체의 메서드 state, action을 입력 받을 수 있음) , 각 리듀서 함수에 대한 액션 생성자를 자동으로 만듭니다.

- 사용 될 컴포넌트에서 hooks 를 import (useSelector, useDispatch) 이 두 개의 hooks은 useSelector(store에 저장 된 상태를 가져옴), useDispatch(상태를 변경하는 함수(reducer 메서드)를 호출함) 로 나뉘어 사용이 가능함. hooks는 또 다른 것들도 존재하지만 기본 사용 방법은 여기까지.

- Redux는 가장 많이 사용되는 라이브러리 이지만, 어느 정도의 러닝커브가 있어 최근에는 사용 수가 조금 감소하긴 하였습니다.(다른 쉽게 사용 가능한 것들이 많이 나와서) 하지만 단점을 상쇄할만한 대규모 커뮤니티가 있고 주기적인 업데이트를 통하여 사용하기 더욱 용이해지고 있기에 계속해서 사용 될 것이라 예상 됩니다.

<br>

### Zustand

- 다음으로 알아볼 것은 [Zustand](https://docs.pmnd.rs/zustand/getting-started/introduction) 입니다. Redux 다음으로 많은 사람들이 사용하고 있는 라이브러리이며 최근 Zustand 기술 스택을 요구하는 회사들도 많아져 꼭 한번 배워보고 싶었습니다.

- Zustand는 React 애플리케이션에서 상태를 관리하기 위한 작고, 빠르고, 가벼운 상태 관리 라이브러리입니다. 독일어로 "상태"를 의미하는 "Zustand"라는 이름을 가진 이 라이브러리는 간단하고 직관적인 API를 통해 상태 관리를 손쉽게 할 수 있도록 설계되었습니다. Zustand는 Flux 패턴을 따르지 않으며, 대신 훅 기반의 접근 방식을 사용합니다.

<br>

```
// npm i zustand 

Zustand의 주요 특징

- 간결한 API: Zustand는 매우 간결하고 사용하기 쉬운 API를 제공합니다. 불필요한 보일러플레이트 코드를 줄여주어 개발자가 상태 관리 로직에 집중할 수 있게 합니다.

- 간단한 상태 정의: 상태와 상태 업데이트 함수를 정의하는데 복잡한 설정이 필요하지 않습니다. 간단한 함수 호출로 상태와 액션을 정의할 수 있습니다.

- 퍼포먼스: Zustand는 성능에 중점을 두고 설계되었습니다. 필요할 때만 상태를 업데이트하고, 필요한 컴포넌트만 다시 렌더링합니다.

- 미들웨어 지원: 로깅, 퍼시스턴스(persistence), DevTools 통합 등 다양한 미들웨어를 지원합니다.
```

<br>

- Zustand의 간단한 사용법에 대해 알아보겠습니다. Redux와는 다르게 매우 간결하게 진행되는 것을 확인할 수 있습니다.

1. store 

- Redux와 동일하게 store를 생성합니다. 

```
import { create } from 'zustand'

const useStore = create((set) => ({
  count: 0, // 초기값
  increment: () => set((state) => ({ count: state.count + 1 })), // reducer 객체를 생성하지 않고 바로 정의 
  decrement: () => set((state) => ({ count: state.count - 1 })), // set() 함수는 state를 병합 합니다. 
}));

export default useStore
```

<br>

2. 컴포넌트에서 사용

- 이제 사용할 수 있습니다. Provider의 props으로 store를 전달하거나 할 필요 없이 바로 컴포넌트에서 import 하여 사용 할 수 있습니다.

```
// Counter.js

import React from 'react';
import useStore from './src/store/useStore.js'; // 상태가 정의된 파일 경로

const Counter = () => {
  const { count, increment, decrement } = useStore();

  return (
    <div>
      <p>{count}</p> // useSelector 로 불러올 필요 없음
      <button onClick={increment}>Increment</button> // useDispatch로 호출 안해도 댐
      <button onClick={decrement}>Decrement</button>
    </div>
  );
};

export default Counter;
```

<br>

3. 결론

- Zustand가 Redux와 비교하였을 때 사용하기 간편하고 쉬운 것을 알 수 있습니다. 그렇다면 우리는 Zustand를 사용하는 것이 정답이구나! 라고 생각할 수 있지만, 각각의 장단점이 있습니다. Zustand와 Redux를 비교하였을 때 단점은 다음과 같습니다.

- 미들웨어 생태계 부족: Redux만큼 다양한 미들웨어와 도구가 존재하지 않습니다. 특정 기능을 추가하려면 직접 구현해야 할 수도 있습니다. (Redux Thunk, Redux Saga, Redux Observable 등 다양한 미들웨어가 Redux에 존재함. 이것들의 사용 방법은 다음에...)

- 중앙 집중식 관리의 부재: Redux처럼 중앙 집중식으로 상태를 관리하지 않기 때문에, 대규모 애플리케이션에서 상태 관리를 체계적으로 하는 데 어려움이 있을 수 있습니다.

- 작은 커뮤니티: Zustand는 상대적으로 새로운 라이브러리이므로, Redux에 비해 커뮤니티와 생태계가 작습니다. 이에 따라 리소스와 지원이 적을 수 있습니다.

- 결론적으로 Zustand는 간단하고 직관적인 API로 빠르게 상태 관리를 시작할 수 있으며, 성능 최적화와 코드 간결성 면에서 장점을 가지고 있습니다. 그러나 미들웨어와 커뮤니티 지원이 상대적으로 부족할 수 있습니다. 따라서 어떤 라이브러리를 선택할지는 온전히 개발자의 몫이며 프로젝트의 크키, 러닝커브등을 고려하여 선택하면 될 것 같습니다.(간편하긴 진짜 간편하네요. 얼마나 간편한지 본인들이 [Redux랑 비교](https://docs.pmnd.rs/zustand/getting-started/comparison) 하는 부분도 공식문서에 있음 ㄷㄷ)

<br>


### tanStack-query(react-query)

- 다음으로 알아볼 라이브러리는 [tanStack-query](https://tanstack.com/query/latest/docs/framework/react/overview) 입니다. 여타 다른 상태관리 라이브러리들과는 차이점이 있습니다. 위 라이브러리들이 클라이언트 중심의 데이터를 관리한 것과는 다르게 tanStack-query는 서버의 데이터 상태를 관리하는데에 중점적(데이터 페칭 및 캐싱 위주)으로 사용되는 라이브러리 입니다.

- 엄밀하게 살펴보면 상태관리 라이브러리가 아닌 데이터 관리 라이브러리에 가깝습니다. 실제로 store를 생성하거나 클라이언트의 데이터 관리를 하는데 tanStack-query는 적합하지 않으나, 클라이언트 측의 상태를 관리하기 위해 사용될 수도 있습니다. 

- 예를 들어, API 호출의 로딩 상태, 오류 상태 등을 관리할 수 있습니다. 또한 tanStack-query의 쿼리 키와 같은 기능을 사용하여 일부 클라이언트 측 상태를 관리할 수도 있습니다. 따라서 tanStack-query는 데이터 관리에 사용되지만, 일부 상황에서는 상태 관리에도 활용될 수 있습니다. 

- React-query는 최근에 TanStack으로 병합되면서 이름이 TanStack Query로 변경 되었습니다(v5).사용법도 약간 변경 되었는데 그 부분에 대해서 중점적으로 확인해보겠습니다.

<br>

```
// npm i @tanstack/react-query 

tanStack-query의 특징

- 상태 및 비동기 데이터 관리: tanStack-query는 비동기 데이터를 관리하고 UI 상태를 업데이트하는 데 사용됩니다. API 호출, 데이터 로딩, 오류 처리 등을 편리하게 처리할 수 있습니다.

- 자동 캐싱 및 리렌더링: 데이터를 자동으로 캐싱하여 성능을 향상시킵니다. 동일한 데이터 요청이 다시 발생할 때 캐시된 데이터를 사용하여 네트워크 요청을 줄입니다.

- 옵티미스틱 업데이트: 옵티미스틱 업데이트를 지원하여 UI에 즉시 변경 사항을 반영할 수 있습니다. 네트워크 요청을 보내기 전에 UI를 업데이트하고, 성공 또는 실패 여부에 따라 다시 업데이트할 수 있습니다.

- 재시도 및 폴링: API 호출이 실패할 경우 자동으로 재시도하거나 주기적으로 데이터를 다시 가져오는 기능을 제공합니다. 이를 통해 네트워크 오류에 강건한 애플리케이션을 만들 수 있습니다.

- 서버 상태 관리: 서버의 상태를 관리하고 효율적으로 처리할 수 있는 기능을 제공합니다. 예를 들어, 서버 상태가 변경되면 자동으로 데이터를 다시 가져오거나 UI를 업데이트할 수 있습니다.
```

<br>

- tanStack-query의 사용법에 대해 알아봅시다. 여타 라이브러리들과 다르게 상당히 방대한 내용을 가지고 있기에, 공식 문서의 [Quick Start](https://tanstack.com/query/latest/docs/framework/react/quick-start) 부분에 명시되어 있는 내용들 위주로 작성해보겠습니다.

<br>

```
import {
  QueryClient,
  QueryClientProvider,
} from '@tanstack/react-query'

import { ReactQueryDevtools } from '@tanstack/react-query-devtools' // Devtools를 사용하고 싶을 때

const queryClient = new QueryClient() // Redux와 동일하게 인스턴스를 생성 후 최상단에서 감싸줍니다. | 따로 store를 생성하는 것은 아님

export default function App() {
  return (
    <QueryClientProvider client={queryClient}> // client 속성에 적용
      <Example />
      <ReactQueryDevtools initialIsOpen={false} /> // 앱 하단에 작성하여 사용
    </QueryClientProvider>
  )
}
```

- queryClient는 여러가지 옵션을 적용할 수 있습니다. staleTime(캐싱 적용 시간)등... [공식문서](https://tanstack.com/query/latest/docs/reference/QueryClient#queryclient)

- [Devtools](https://tanstack.com/query/latest/docs/framework/react/devtools) 는 NODE_ENV 환경변수가 development일 떄만 적용 되는 tanStack-query에서 지원하는 dependencies 라이브러리 입니다. 여러가지 옵션을 적용할 수 있으며 내부 동작을 시각화 할 수 있습니다.

<br>

- 기본적으로 사용 할 준비가 완료 되었으니 가상의 API 호출 함수를 이용하여 직접 사용해보겠습니다. tanStack-Query 에는 다양한 API reference가 존재하는데 그 중 서버의 GET 요청에 대한 데이터를 관리해주기 위해 useQuery 를 사용합니다. useQuery 는 v5 부터 인자로 단 하나의 객체만을 받고 그 중에 queryKey, queryFn 는 필수 값 입니다.

```
import {
  useQuery,
  useMutation,
  useQueryClient,
  QueryClient,
  QueryClientProvider,
} from '@tanstack/react-query'
import { getTodos, postTodo } from '../my-api' // 가상 API | 각각 get, post 요청

// queryClient 인스턴스 생성
const queryClient = new QueryClient()

export default function App() {
  return (
    // client Props 적용
    <QueryClientProvider client={queryClient}>
      <Todos />
    </QueryClientProvider>
  )
}

export default function Todos() {
  // 쿼리 데이터를 관리하고 조작하기위해 인스턴스 생성
  const queryClient = useQueryClient()

  // Fetching Todos (Queries)
  const query = useQuery({ queryKey: ['todos'], queryFn: getTodos }) 

  // Mutations
  const mutation = useMutation({
    mutationFn: postTodo,
    onSuccess: () => {
      // Invalidate and refetch
      queryClient.invalidateQueries({ queryKey: ['todos'] })
    },
  })

  return (
    <div>
      <ul>{query.data?.map((todo) => <li key={todo.id}>{todo.title}</li>)}</ul>

      <button
        onClick={() => {
          mutation.mutate({
            id: Date.now(),
            title: 'Do Laundry',
          })
        }
      }>
        Add Todo
      </button>
    </div>
  )
}

render(<App />, document.getElementById('root'))

```

- useQuery의 queryKey는 캐싱 및 재사용을 위해 사용되는 고유 키입니다. queryFn은 실제 데이터를 가져오는 함수 (getTodos)입니다.

- [useMutation](https://tanstack.com/query/latest/docs/framework/react/reference/useMutation#usemutation) 훅은 새로운 할 일을 추가하는 데 사용되며 useQuery와 같은 queryKey는 받지 않습니다. mutationFn은 서버에 새로운 할 일을 추가하는 함수 (postTodo)입니다. 쉽게 말해 useQuery 는 서버에서 데이터를 GET 할 때 사용되고, 그 이 외의 POST, PATCH, PUT, DELETE 인 경우는 useMutation 을 사용합니다.

- 호출을 하기 위해 mutation 객체의 mutate 메서드를 사용합니다. mutation 객체에서 정의 될 수 있는 것은 여러가지가 있는데, onMutate는 mutation 함수가 실행되기 전에 실행되고, onSettled 는 try-catch-finally 의 finally 처럼 요청이 성공하든 에러가 발생되든 상관없이 마지막에 실행됩니다. 더욱 자세한 옵션은 위의 공식 문서에서 확인 ^^;(너무 많음)

- onSuccess는 변이(mutation)가 성공적으로 완료되었을 때 실행되는 콜백 함수입니다. 여기서 onSuccess는 [queryClient.invalidateQueries](https://tanstack.com/query/latest/docs/reference/QueryClient#queryclientinvalidatequeries)를 호출하여 queryKey가 ['todos']인 쿼리를 무효화합니다. 

- 무효화는 해당 쿼리가 최신 상태가 아님을 나타내며, tanStack-Query는 이를 감지하고 데이터를 다시 가져옵니다.(최신 상태가 아니면 자동으로 캐싱) 즉, 새로운 할 일을 추가한 후, 할 일 목록을 다시 가져와서 UI를 업데이트합니다.

<br>

- useQuery는 단일 데이터를 get 호출 하는데 병렬로 요청하는 방법도 존재합니다. 바로 useQueries 를 사용하는 것 입니다.

- 아래는 제가 프로젝트에서 적용하였던 useQueries를 통한 병렬적인 데이터 처리 방식 입니다.

```
import { useQueries } from "react-query";
import {
  getAllPokemon,
  getPokemonID,
  getPokemonImage,
  getPokemonName,
  getPokemonType,
  getKorPokemonType,
  getKorPokemonRegion,
} from "../../api/pokemon/getPokemon"; // pokeAPI에서 포켓몬 이름, ID, Image 등을 get 요청한 함수들

export default function usePokemonData(page) { // usePokemonData Custom hook 작성
  const queries = useQueries([ // useQueries는 배열안에서 작성됩니다.
    { queryKey: ["pokemon", page], queryFn: () => getAllPokemon(page) }, 
    { queryKey: ["id", page], queryFn: () => getPokemonID(page) },
    { queryKey: ["name", page], queryFn: () => getPokemonName(page) },
    { queryKey: ["image", page], queryFn: () => getPokemonImage(page) },
    { queryKey: ["type", page], queryFn: () => getPokemonType(page) },
    { queryKey: ["korType", page], queryFn: () => getKorPokemonType(page) },
    { queryKey: ["korRegion", page], queryFn: () => getKorPokemonRegion(page) },
  ]); 
  // pagination을 사용하여 page가 바뀔 때 보여져야 할 포켓몬도 바뀌어야 하기에 queryKey 배열에 page가 추가 되었습니다.

  const isLoading = queries.some((query) => query.isLoading); // queries.some 으로 모두 fresh 한 상태가 아니라면 isLoading === true

  const data = {
    pokemon: queries[0].data, // 이게 결국 queries 배열의 첫 번째 data | { queryKey: ["pokemon", page], queryFn: () => getAllPokemon(page) }
    id: queries[1].data,
    name: queries[2].data,
    image: queries[3].data,
    type: queries[4].data,
    korType: queries[5].data,
    korRegion: queries[6].data,
  };

  // data 객체에 할당

  return { data, isLoading };
}
```

<br>

- 이제 usePokemonData 를 PokemonCard 컴포넌트에서 호출하여 다음과 같이 사용하였습니다.

<br>

```
import { Container, CardContainer, Info, InfoBox, MainImage, Type, TypeBox, TypeImg } from "./style";
import Title from "../Title";
import typeIcons from "../../styles/typeIcon";
import colors from "../../styles/typeColor";
import usePokemonData from "../../hooks/Pokemon/usePokemonData";
import { Link, useParams, useNavigate } from "react-router-dom";
import Pagination from "react-js-pagination";
import "../../styles/Paging.css";
import Loader from "../Loader";

export default function PokemonCard() {
  const { page } = useParams(); // useParams로 현재 어느 페이지에 존재하는지 확인
  const navigate = useNavigate();
  const { data, isLoading } = usePokemonData(page); // usePokemonData에 page를 전달

  const handlePageChange = (newPage) => {
    navigate(`/pokemon/${newPage}`);
  };

  if (isLoading) {
    return <Loader />;
  }
  
  return ( // 받은 data를 렌더링
    <>
      <Title name="포켓몬 도감" />
      <Container>
        {data.id.map((_, item) => (
          <Link key={item} to={`/pokemon/detail/${data.id[item]}`}>
            <CardContainer color={data.type[item].map(typeItem => colors[typeItem])}>
              <Info>
                <InfoBox>
                  no.{data.id[item]}
                </InfoBox>
                <InfoBox>
                  {data.name[item]}
                </InfoBox>
              </Info>
              <MainImage src={`${data.image[item]}`} alt={`${data.name[item]}`} />
              <Type>
                {data.type[item].map((typeItem, typeIndex) => (
                  <TypeBox key={typeIndex} color={`${colors[typeItem]}`}>
                    <TypeImg src={`${typeIcons[typeItem]}`} />
                    {data.korType[item][typeIndex]}
                  </TypeBox>
                ))}
              </Type>
            </CardContainer>
          </Link>
        ))}
      </Container>
      <Pagination
        activePage={parseInt(page)}
        itemsCountPerPage={21}
        totalItemsCount={1025}
        pageRangeDisplayed={5}
        prevPageText={"‹"}
        nextPageText={"›"}
        onChange={handlePageChange}
      />
    </>
  );
}
```

- tanStack-query는 서버 데이터의 상태관리를 하기에 적합한 라이브러리 입니다. 적용이 가능한 옵션이 많고 선택사항이 많기에 어느정도 러닝커브가 있을 수 있지만, 큰 커뮤니티, 많은 양의 공식문서를 통해 학습하여 사용이 가능합니다. 실제 프로젝트에 적용하는 것은 선택사항이나 성능 개선을 위해 필수적이라고 생각되어 알아보았습니다. 

- Devtools가 존재하는 것은 알고 있었으나 실제로 프로젝트에 도입해서 사용해본적이 없기에, 추가적으로 다시 한번 짚고 넘어갈 예정입니다.

<br>

### jotai

- 이번에는 [jotai](https://jotai.org/docs/introduction) 입니다. Recoil과 거의 비등비등하지만 조금 더 앞서있는 jotai에 대해서 먼저 알아보겠습니다. jotai는 원자(atom) 단위로 상태를 관리하는 것을 목표로 합니다. Jotai는 React의 훅(hook) 기반 API와 잘 통합되며, 사용자가 React 컴포넌트의 로컬 상태를 간단하게 전역 상태로 변환할 수 있게 합니다.

- jotai의 핵심 로직으로는 atom, useAtom, Store, Provider가 있습니다. 

```
// npm i jotai

jotai의 주요 특징

- 작고 경량: Jotai는 매우 작고 가벼운 라이브러리입니다. 이는 성능 최적화와 빠른 로딩 시간을 보장합니다.

- 단순성: Jotai의 API는 간단하고 직관적이며, React 훅의 개념을 확장합니다.

- 컴포저블 상태: 원자(atom) 단위로 상태를 관리하여, 상태를 쉽게 조합하고 관리할 수 있습니다.

- 타입스크립트 지원: 타입스크립트를 지원하여, 타입 안전성을 제공합니다.

- 최소 재렌더링: 상태가 변경될 때, 관련된 컴포넌트만 재렌더링 되어 성능을 최적화합니다.
```

- jotai 는 react의 useState와 거의 동일하게 atom과 useAtom을 사용하는데 어떤 식으로 작동하는지 살펴보겠습니다.

<br>

```
import React from 'react';
import { atom, useAtom } from 'jotai';

// 1. 원자(atom) 생성
const countAtom = atom(0); // atom  초기 값

// 또한 다른 원자(atom)를 기반으로 하는 파생된 상태를 쉽게 생성 가능 합니다.

const doubleCountAtom = atom((get) => get(countAtom) * 2) // get으로 다른 원자 호출

function Counter() {
  // 2. useAtom 훅을 사용하여 원자(atom) 상태와 상태 업데이트 함수를 가져옴
  const [count, setCount] = useAtom(countAtom);
  
  const [doubleCount] = useAtom(doubleCountAtom);

  return (
    <div>
      <p>Count: {count}</p>
      <p>Doubled Count: {doubledCount}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

function App() {
  return (
    <div>
      <h1>Jotai Counter Example</h1>
      <Counter />
    </div>
  );
}

export default App;
```

<br>

- react의 useState를 사용해보았다면 문제 없이 쉽게 사용할 수 있다는 것을 알 수 있습니다. 또한 원자를 바탕으로 다른 원자를 get으로 호출하여 쉽게 파생하여 사용할 수 있습니다.

- jotai는 기본적으로 React Context를 사용하여 전역 상태를 관리하지만, 필요에 따라 커스텀 [store](https://jotai.org/docs/core/store)나 [provider](https://jotai.org/docs/core/provider)를 사용할 수 있는 유연성을 제공, 이 기능은 상태 관리의 범위를 한정하거나 여러 상태 컨텍스트를 사용하는 애플리케이션에서 유용하며 사용방법은 Redux와 동일 합니다.

- 또한 다음과 같이 비동기 작업을 하는 Async Atom (비동기 원자)을 쉽게 생성할 수 있습니다. Redux의 경우 비동기 작업을 하기 위해서는 Redux-thunk와 같은 미들웨어 라이브러리를 설치해야하기 때문에 더욱 간단하게 사용이 가능하다는 장점이 있습니다.

<br>

```
import { atom, useAtom } from 'jotai';

const userAtom = atom(async () => {
  const response = await fetch('/api/user');
  const user = await response.json();
  return user;
});

function UserProfile() {
  const [user, setUser] = useAtom(userAtom);
  return (
    <div>
      {user ? <p>{user.name}</p> : <p>Loading...</p>}
    </div>
  );
}
```

- jotai는 기술스택에 요구되거나 따로 사용하는 분들을 많이 보지 못해서 등한시 하고있었는데, 공식 문서 UI가 가장 읽기 좋게 되어 있다는 점이 마음에 들었습니다. jotai 또한 매우 가벼운(zustand의 2배 => 얘가 비정상적으로 가벼움;;) 라이브러리 이고 커스텀 하여 사용할 수 있기에 경쟁력이 있다는 생각이 들었습니다.

<br>

### 💡 면접 대비를 위한 CS tip : 상태관리에 대한 3가지 접근 방식

1. Flux

- 저장소(store) / 액션함수(action) / 리듀서 등을 통해서 상태를 업데이트 하는 방식 | Redux, Zustand

2. Proxy

- 컴포넌트에 사용되는 일부 상태를 자동으로 감지해서 업데이트 하는 방식 | Mobx, Valtio

3. Atomic

- React에 사용되는 state와 비슷하게 리액트 트리 안에서 상태를 저장하고 관리하는 방식 | Recoil, Jotai