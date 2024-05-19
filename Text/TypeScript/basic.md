# 타입스크립트(TypeScript)

- 자바스크립트는 Dynamic Typing이 가능한 언어입니다.(5 - "3" 과 같은 연산이 가능) 코드가 길어질 수록 이러한 점들은 자바스크립트의 약점이 되는데 이를 보완하기 위해 나온 것이 타입스크립트 입니다.

- 자바스크립트와 동일한 문법을 사용하지만 타입 부분에 대해서 엄격하게 검사한다는 점이 다릅니다. 자바스크립트의 에러 메시지는 약간 추상적인 부분이 많아 어떤 부분이 정확한 에러인지 알기 어려운 반면, 타입스크립트는 타입에 대한 에러 & 단어의 스펠링또한 체크해줍니다.

- 또한 잘못된 코드를 작성해도 별 관심 없는 자바스크립트와 다르게 코드 작성 시 잘못된 형식을 기재 하였을 때, 오류를 표시 해줍니다.(정적 언어 처럼: 빨간색 밑줄 표시가 출력). 에러가 뜨는 것은 부정적인것이 아니라 버그를 미연에 방지해주는 역할을 하기 때문에 타입스크립트를 사용하는 것은 현 시점에서 필수적이 되었습니다.

<br>

### 기본 타입(Primitive types)

- 변수에 타입을 지정하는 방법으로 콜론(:)을 사용할 수 있습니다. 변수명:타입명 으로 선언 합니다. => let name: string = "KICHAN";

- name 변수에 다른 타입의 값을 할당하면 에러가 발생합니다. => name = 123 (Type 'number' is not assignable to type 'string'). ts

- 기본 타입 모두 사용 가능합니다. number, string, boolean, null, undefined, symbol

<br>

### 참조 타입(Reference types)

- array 자료 타입 지정이 가능합니다. => let developer: string[] = ["FE", "BE", "DevOps"] | 알아야 할 점은 :array와 같이 지정하는 것이 아닌 대괄호 기호를 통해 타입 지정이 가능합니다.

- 배열에 들어가는 타입에 대해 지정할 수 있습니다. :string[] 의 경우 문자열로 된 요소만이 이 배열안에 들어갈 수 있습니다.

- Object 는 다음과 같이 타입 지정이 가능합니다. => let developer: { role1: string role2: string } = { role1 : "FE" , role2 : "BE" }

<br>

### union, any, unknown

- 여러가지 타입을 지정할 수 있는 변수를 만들 때 Union 타입을 사용할 수 있습니다. let variable: (number | string) = 123;

- |(or) 기호를 사용하여 작성할 수 있습니다. ()소괄호는 생략 가능하고 지정한 타입들의 변수를 선언하여 가변적 활용이 가능합니다. variable = "KICHAN"; 

- 배열과 오브젝트 타입에도 동일하게 사용 가능합니다. let array: (number | string)[] = [1, "2", 3]; 주의해야 할 점은 소괄호를 생략하게 되면 number 타입, string 배열 타입이 지정 됩니다. 동일하게 배열로 받고 싶은 경우 소괄호를 잘 지정해주어야 합니다.

- any 타입은 모든 타입을 허용 해줍니다. 모든 것을 허용하면 자바스크립트를 사용하는 것과 다를게 없으니 받을 데이터형이 정확하지 않을 때 사용하여 테스트하고 후에 타입을 지정해주는 것이 좋습니다.

- unknown 타입 또한 모든 자료형을 허용 해줍니다. 다른 점은 any 보다는 조금 안전합니다. 예시 코드를 작성해보겠습니다.

```
let var1: any;
var1 = 123;
var1 = "KICHAN";

let var2: unknown;
let var2: 456;
let var2: "LEE;

let 변수1: string = var1 // 타입 에러가 나지 않습니다.

let 변수2: string = var2 // 타입 에러 발생
```

- 타입스크립트는 엄격한 타입검사를 하기 때문에 unknown 타입을 사용하여 타입에 대한 검증을 할 수 있습니다.

- let num1: unknown = 1; num1 - 1 => 이 결과를 확인하면 에러가 나는 것을 확인할 수 있습니다. 숫자가 할당되어 자동으로 number 타입으로 지정하는 것이 아닌 여전히 unknown 타입으로 사용 되는 것을 확인 가능합니다.

<br>

### 함수의 타입

- 함수의 파라미터와 반환(return) 값 또한 타입 지정을 할 수 있습니다.

```
function calc(x: number) : number(return 값의 타입 지정){
  return x * 2; // return 값을 여기서 지정하는게 아님!
}

calc("10") // 타입 에러 검증
```

- 함수에서 반환 값을 받고 싶지 않을 때 void 타입을 사용하여 좀 더 철저하게 타입을 지정해줄 수 있습니다.

```
function calc2 (y: number): void {
  1 + 1;
}

// 실수로 return 하였을 때 오류 발생
```

- 자바스크립트의 함수와 또 다른 점은 타입 지정 된 파라미터를 필수적으로 사용하여야 합니다. 만약 파라미터 타입을 지정해주고 함수 호출 시 파라미터의 값이 없다면 에러가 발생합니다. 

- 이것을 핸들링 하기 위해 ?(옵셔널 체이닝)을 사용하여 값이 들어올 수도, 아닐 수도 있음을 명시해주어야 합니다.

- 변수?: number 는 정확하게는 => 변수: number | undefined 와 같습니다.(union 타입)

<br>

### Narrowing & Assertion

- Type이 아직 하나로 확정되지 않았을 때 Type Narrowing 을 사용할 수 있습니다.

```
function calc(x: number|string) {
  return x + 1; // 에러가 발생함
}

calc(1);
// JS에서 기본적으로 number & string 모두 합 연산이 가능하지만 위 파라미터는 Union 타입이기 때문
```

- Narrowing 의 대표적인 방법은 typeof 연산자를 사용하는 방법 입니다. EX => if(typeof x === "string")

- 또는 in, instanceof 등의 문법을 사용하여 Type Narrowing 을 할 수도 이습니다.

- Type Assertion을 사용하면 if 문 없이도 구현이 가능합니다.

```
function calc(x: number|string) {
  let arr: number[] = [];
  arr[0] = x as number; // 왼쪽(x)의 변수를 오른쪽(number)의 타입으로 덮어 씌워주세요 라는 뜻
}

calc(123);
```

- 주의 해야 할 점은 Assertion 문법은 여러가지 타입들 중 하나를 확정하기 위해 사용 되는 것이기에 이미 확정 된 타입을 다른 타입으로 변경하는 것은 안됩니다. => 여러개 중 하나는 되지만 A를 B로 바꾸는 건 안된다는 소리

- 따라서 어떤 타입이 들어올지 100%(세상에 100%는 없지만) 확신이 가능할 때 Assertion 문법을 사용하는 것이 좋습니다.

<br>

### type alias

- 타입이 너무 길때 type alias 를 사용하여 타입을 만들어줄 수 있습니다. 

```
type Something = string | number | undefined;

let var: Something = "타입 변수";

type SomeObj {
  name: string,
  age: number
}

let person: SomeObj = { name: "LEEKICHAN", age: 25 };
```

- const 키워드는 변수의 재할당을 막지만 자료형의 수정까지는 막지 못합니다. readonly 속성을 사용하여 이를 방지할 수 있습니다. 

```
const region = { name : "Boryung" };

region.name = "seoul"; // 객체 속성 수정하는 것을 막지 않음

// readonly를 사용

type MyRegion {
  readonly name: string,
}

const realRegion: MyRegion = { name : "Boryung" }

realRegion.name = "seoul" // 타입 에러 발생
```

- 하지만 에러를 띄워줄 뿐 실행을 막는 것이 아니기 때문에(에디터 경고사항) 실제 자바스크립트 컴파일이 되면서 바뀌게 된다. readonly를 사용하는 이유는 에러가 날 수 있는 할당 과정들을 사용자에게 시각적으로 보여주기 위해 사용할 수 있다.


- type alias 를 합칠 수 있습니다. 

<br>

```
type Name = string;
type age = number;

type Person = Name | age;

// 객체 type extend
type RealName = { name : string };
type RealAge = { age : number };

type RealPerson = RealName & RealAge
```

<br>

### type alias 에 함수의 타입 지정

- type alias 에 함수의 타입을 지정할 수 있습니다.

```
type FuncType = (a: string) => number; // 파라미터는 string 반환 값은 number 타입

let Func1: FuncType = function (a){
  return 10;
}

function Func2() {
  // 이와 같은 방식은 함수 선언식이라고 합니다.
}
```

- 객체 내에 지정된 함수를 메서드(method) 라고 합니다. 메서드에서도 타입을 지정할 수 있습니다.

```
type Person = {
  name: string,
  age: number,
  agePlus: ( x: number) => number,
}
```

<br>

### 클래스의 타입 지정

- 타입스크립트 클래스의 타입을 지정할 수 있습니다.

```
// 기존의 클래스 문법
class Person {
  constructor() {
    this.name = "KICHAN";
  }
}

const person1 = new Person();

// 위와 같은 방식으로 new 키워드를 통해 객체의 생성이 가능합니다.
```

<br>

```
// 타입스크립트에서 클래스 생성시

class Person {
  name :string;  // 클래스의 필드 값, TS에서 지정 해주지 않으면 에러> Error : Property 'name' does not exist on type 'Person' 
    constructor(a: string) {
      this.name = "KICHAN";
    }
}

const person1 = new Person();
```

<br>

### interface

- interface 키워드를 사용하여 객체 타입을 지정해줄 수 있습니다. type 과 유사하지만 "=" 기호가 필요하지 않고 클래스와 유사하게 동작합니다. 또 콤마(,) 가 아닌 세미콜론(;)을 사용하여 마칠 수 있습니다. 또한 extends로의 상속이 가능합니다.

<br>

```
// interface 비교
type Person = {
  name: string,
  age: number
}

interface Person2 {
  name: string,
  age: number;
}

// extends
interface Kid {
  name: string;
}

interface Parent extends Kid {
  kidName: string;
}

// name 속성을 상속 클래스와 유사하게 동작함
```

- type 키워드의 경우 intersection(교차) 라는 비슷한 방식으로 구현이 가능합니다. 차이점은 extends 와 같은 복사가 아닌 타입을 모두 만족하는 타입을 새로 생성한다는 점이 다릅니다. intersection은 interface 도 사용이 가능합니다.

```
type Animal = { name: string }

type Dog = { age: number } & Animal // intersection
```

- 거의 유사해보이는데 굳이 type 과 interface를 구분 해놓은 가장 큰이유는 interface는 중복선언이 가능하기 때문 입니다. (type의 경우에는 Duplicate 에러가 발생함)

```
interface Coffee {
  name: string
}

interface Coffee {
  price: number
}

// 이렇게 해도 아무런 오류가 나지 않습니다. 중복 선언된 interface는 자동으로 extends 되며 아래와 같이 새로운 오브젝트로 지정됩니다.

interface Coffee { name: string; price: number }
```

<br>

### rest parameter & destructuring

- rest parameter는 파라미터에 매개 변수로 몇 개가 들어올지 알 수 없을 때 사용할 수 있습니다. ...parameter 로 작성하고 타입을 지정할 수 있습니다. 다수의 파라미터는 배열로 지정되며 다수의 매개변수가 있을 때 맨 마지막에 작성해야 합니다.

```
function Array(...x: number[]){
  console.log(x);
}

Array(1,2,3,4,5,6); // [1,2,3,4,5,6] 출력 
```

- 배열안에서는 spread operator로 바뀝니다. 이는 괄호를 없애고 요소를 하나씩 출력하는 방법으로 사용됩니다.

```
const arr = [1,2,3];
const arr2 = [4,5];
const arr3 = [...arr, ...arr2] // console.log(arr3) => [1,2,3,4,5]
```

- 배열의 요소를 변수로 변경할 때 destructuring을 사용하여 쉽게 가능합니다. 객체와 함수에서의 매개변수로도 사용이 가능합니다.

```
let [var, var2] = [10, "하이"];
console.log(var) // 10
console.log(var2) // 하이

let { adult , age } = { adult : true , age : 20 };
console.log(adult) // true
console.log(age) // 20

// 함수

function IsAdult({ adult , age }: { adult: boolean , age: number }){
  console.log( adult , age);
}

IsAdult({ adult : true , age : 20 })
```

<br>

### React + TypeScript

- React 에서 사용되는 JSX 문법의 타입을 지정할 수 있습니다.

> let jsxType :JSX.Element = `<div></div>`;

- Component 또한 동일하게 타입을 지정할 수 있습니다. return 값을 JSX.Element 로 또는 컴포넌트에서 받는 props 의 타입을 지정 & type 로 설정해줄 수 있습니다.

<br>

```
// import Profile Component

type ProfileType = {
  name: string,
  age: number,
}

function App(){
  return(
    <div>
      <Profile name={"KICHAN"} age={20} />
    </div>
  )
}

// profile Component

function Profile(props: { name: string, age: number }): JSX.Element {
  return(
    <div>
      <span>{props.name} 입니다.</span>
      <span>{props.age} 살 입니다.</span>
    </div>
  )
}
```

<br>

- useState 의 경우 여러가지 타입이 들어올 수 있을 때 Generic을 사용하여 타입을 지정해줄 수 있습니다.

> const [ user, setUser ] = useState< string | number >("KICHAN");

<br>

