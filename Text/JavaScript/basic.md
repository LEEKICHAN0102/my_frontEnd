# 자바스크립트(JavaScript)

-  넷스케이프 커뮤니케이션즈(Netscape comunications)는 정적인 HTML을 동적으로 표현하기 위해 경량의 프로그래밍 언어를 도입하기로 결정하였고 탄생한 것이 브렌던 아이크(Brendan Eich)가 개발한 자바스크립트 입니다.

- 자바스크립트는 웹 페이지를 동적으로 만들고 상호작용을 가능하게 하는 프로그래밍 언어입니다. 웹 브라우저에서 실행되며, HTML 및 CSS와 함께 웹 개발에서 중요한 역할을 합니다.

<br>

### 자바스크립트의 변수

- 변수(Variable)는 값(value)을 저장(할당)하고 그 저장된 값을 참조하기 위해 사용합니다. 사용하고 버리는 값이 아닌 캐싱할 필요가 있는 것을 변수에 할당하여 사용합니다.

- 변수는 위치(주소)를 기억하는 저장소입니다. 위치란 메모리 상의 주소(address)를 의미하고, 변수란 메모리 주소(Memory address)에 접근하기 위해 사람이 이해할 수 있는 언어로 지정한 식별자(identifier)를 말합니다.

<br>

### 변수의 선언, 할당, 초기화

- 변수의 선언(Declaration), 할당(Assignment), 초기화(Initialize)는 프로그램에서 데이터를 관리하고 조작하는 데 중요한 단계입니다. 

1. 선언(Declaration)

```
var x; // 변수 x를 선언
let y; // 변수 y를 선언
const z; // 에러: const 변수는 반드시 초기화되어야 합니다. Uncaught SyntaxError: Missing initializer in const declaration
```

- 변수를 만들어 사용하기 위해 메모리 공간을 확보하는 단계. var, let, const 키워드를 사용하여 변수를 선언할 수 있고 선언된 변수에는 초기값이 없을 수 있습니다.

- const 키워드를 사용하여 변수를 선언할 수 없습니다. 상수는 변수와는 달리 선언만 할 수가 없기때문에, 선언과 동시에 값을 할당해주는 초기화를 진행하여야 합니다. 또한 안에 있는 값을 수정하려고 하여도 오류가 발생합니다.

2. 초기화(Initialize)

```
var x = 10; // 변수 x를 초기화하여 값 10을 할당
let y = "Hello"; // 변수 y를 초기화하여 문자열 "Hello"를 할당
const z = true; // 변수 z를 초기화하여 boolean 값 true를 할당
```

- 변수에 값을 할당하여 초기화하는 단계입니다. 초기화하지 않은 변수의 값은 undefined가  할당 됩니다.

3. 할당(Assignment)

```
x = 20; // 변수 x에 새로운 값 20을 할당 (재할당)
y = "World"; // 변수 y에 새로운 문자열 "World"를 할당 (재할당)
// const 키워드는 재할당이 불가능합니다.
```

- 이미 선언되고 초기화된 변수에 값을 재할당하는 단계입니다. 할당 연산자 =를 사용하여 값을 변수에 할당하고 const 키워드의 경우 변수를 재할당할 수 없습니다.

- var의 경우 재선언(이미 초기화 된 변수를 다시 선언 할당함)이 가능합니다. 프로그램적으로 오류를 발생 시킬 수 있기 때문에 ES6 이전의 var 키워드를 사용하였던 초기 JavaScript(let, const가 없었음)가 개발자들 사이에서 근본 없는 프로그래밍 언어 취급을 받기도 하였습니다 ㅠㅠ

<br>

### 자바스크립트의 문(statement)

- 자바스크립트에서 "문(statement)"은 프로그램의 실행 단위를 나타냅니다. 문은 리터럴, 연산자(Operator), 표현식(Expression), 키워드(Keyword) 등으로 구성되며 세미콜론(;)으로 끝나야 합니다.

1. 할당문 (Assignment Statement): 변수에 값을 할당하는 문입니다.

2. 조건문 (Conditional Statement): 조건에 따라 코드 블록을 실행하는 문입니다.

3. 반복문 (Loop Statement): 조건이 참인 동안 코드 블록을 반복해서 실행하는 문입니다.

4. 함수 선언문 (Function Declaration Statement): 함수를 정의하는 문입니다.

5. return 문 (Return Statement): 함수에서 값을 반환하는 문입니다.

6. break 문과 continue 문 (Break and Continue Statements): 반복문에서 사용되며, 각각 반복문을 종료하거나 다음 반복으로 넘어가는 역할을 합니다.

```
// 할당문
var x = 10;

// 조건문
if (x > 5) {
    console.log("x는 5보다 큽니다.");
} else {
    console.log("x는 5보다 작거나 같습니다.");
}

// 반목문
for (var i = 0; i < 5; i++) {
    console.log(i);
}

// 함수 선언문
function greet(name) {
    console.log("Hello, " + name + "!");
}

// return 문
function add(x, y) {
    return x + y;
}

// break 문 & continue 문
for (var i = 0; i < 10; i++) {
  if (i === 5) {
      break; // 반복문 종료
  }
  if (i % 2 === 0) {
      continue; // 다음 반복으로 넘어감
  }
  console.log(i);
}
```

- 외에도 다양한 종류의 문이 있으며, 문들을 조합하여 로직을 구현할 수 있습니다. 

<br>

### 문(statement)와 표현식(expression)의 비교

- 표현식(Expression)은 하나의 값으로 평가(Evaluation)됩니다. 값(리터럴), 변수, 객체의 프로퍼티, 배열의 요소, 함수 호출, 메소드 호출, 피연산자와 연산자의 조합은 모두 표현식이며 하나의 값으로 평가(Evaluation)됩니다. 

- 표현식은 결국 하나의 값이 되기 때문에 다른 표현식의 일부가 되어 조금 더 복잡한 표현식을 구성할 수도 있습니다. 아래의 예에서 1 * 10은 10으로 평가 됩니다.

```
// 표현식
1             // 1
1 * 10        // 10
1 * 10 > 5   // true
(1 * 10 > 5) && (1 * 10 < 15)  // true
```

- 자연어에서 문(Statement)이 마침표로 끝나는 하나의 완전한 문장(Sentence)이라고 한다면 표현식은 문을 구성하는 요소입니다. 표현식은 그자체로 하나의 문이 될 수도 있습니다.

```
// 선언문(Declaration statement)
var x = 5 * 10; // 표현식 x = 5 * 10를 포함하는 문.
// 할당문(Assignment statement)
x = 100; // 이 자체가 표현식이지만 완전한 문이기도 함.
```

- 표현식과 문은 매우 유사하여 구별이 어려울 수 있습니다. 표현식은 평가되어 값을 만들지만 그 이상의 행위는 할 수 없고 문은 var, function과 같은 선언 키워드를 사용하여 변수나 함수를 생성하기도 하고 if, for, while 문과 같은 제어문을 생성하여 프로그램의 흐름을 제어하기도 합니다. 

- 표현식을 통해 평가한 값을 통해 실제로 컴퓨터에게 명령을 하여 무언가를 하는 것은 결국 문(statement)입니다.

<br>

### 자바스크립트이 원시 자료형(primitive data type)

- 원시 자료형은 변경 불가능한(immutable) 값으로, 단일 값만을 저장하고  숫자(number), 문자열(string), 불리언(boolean), null, undefined, Symbol이 있습니다. 변수에 원시 자료형을 할당하면 변수에는 실제 값이 직접 저장됩니다.

```
let num = 10; // 숫자 타입 || 자바스크립트에는 정수와 실수의 구분이 없음 - 2^53 - 1까지 안정적으로 표현 더 큰 수는 BigInt 
let str = "Hello"; // 문자열 타입
let bool = true; // 불리언 타입
let n = null; // null 타입
let u; // undefined 타입
let sym = Symbol("symbol"); // Symbol 타입

console.log(n, typeof n); // null의 예외성
```

- 예외적으로 null의 경우 typeof 를 사용하여 검사하였을 때 'object'를 반환하는 것을 확인할 수 있습니다. null은 원시 값 중의 하나인데 왜 object 타입을 반환하는지에 대한 이유를 Chat GPT에게 물어보았더니 나온 이유는 다음과 같습니다.

- null은 객체가 아니라 값이 없음을 나타내는 원시 데이터 타입으로 처리되어야 할 것이지만, JavaScript의 초기 버전에서 typeof null을 평가하면 "object"가 반환되는 오류가 있었습니다.

- 이는 1995년에 JavaScript의 초기 버전에서 누락된 부분이었고, 이후 JavaScript 엔진에 새로운 기능을 추가하거나 기존 기능을 수정하는 것이 매우 어려워졌기 때문에 호환성을 위해 유지되었습니다. 결국 이 문제를 수정하려는 시도는 더 복잡한 문제를 초래할 수 있었기 때문에 그냥 남겨두게 되었습니다.

- 따라서 현재에도 typeof null은 "object"를 반환합니다. 하지만 null은 원시 값이므로 실제로는 객체가 아니라는 것을 명심하는 것이 중요합니다.

<br>

### 동적타입 & 인터프리터

- 자바스크립트는 동적타입을 가진 언어입니다. 특정 값이 할당된 변수에, 그와 다른 자료형의 값을 넣는 것이 가능합니다. 자유롭지만 그만큼 자료형 관련 오류들에 취약하다는 단점이 있습니다. 타입이 다른 값의 재할당이 가능한 이유가 바로 자바스크립트가 동적 타입(재선언이 가능함)을 가진 언어 이기 때문입니다.

- 자료형이 다르기 때문에 일어날 수 있는 오류를 알아보겠습니다.

```
// 주어진 문자열을 대문자로 바꾸는 함수
// 다른 자료형에 대한 예외처리 없음
function getUpperCase(str) {
  return str.toUpperCase();
}

console.log(getUpperCase('hello')); // "HELLO"

console.log(getUpperCase(1)); // 에러발생
```

- getUpperCase 함수의 매개변수로 숫자를 전송시 에러가 발생합니다. 왜 에러가 발생하는가? 에 대한 설명을 하기전에 자바스크립트가 인터프리터 언어인 것을 알고 넘어가야 합니다.

- 인터프리터 언어는 C,C++ 등의 언어등과 다르게 특별히 컴파일의 단계를 거치지 않고 사용자에게 바로 그 결과가 보이게 됩니다. 소스 코드를 한 번에 전체적으로 컴파일하는 대신, 코드를 한 줄씩 읽고 해석하여 실행하는 방식 입니다.

- 위 코드를 C,C++ 에서 작성하게 될 경우 실행 이전 코드 작성 단계 부터 빨간색 밑줄로 에러가 나오는 것을 보게 될 것 입니다.(애초에 작성이 안됨)

- 자바스크립트는 사용자가 잘못 작성 했는지 애초에 관심을 가지지 않습니다. 인터프리터 언어이기 때문에 타입 오류에 대한 검증이 없이 우선 실행부터 시키는 것 입니다. 의도와 다른 연산에 대해서도 살펴봅시다.

```
1 + 1 // 2
'1' + 1 // 11
```

- JS 개발자라면 한번쯤 보았을 법한 JS 논리 오류 입니다. 현재는 이러한 문제점을 보완하기 위한 정적 타입 지정 기능을 추가한 언어인 타입스크립트가 출시 되었습니다. 타입스크립트 코드는 일반적으로 컴파일하여 자바스크립트 코드로 변환됩니다. 따라서 타입스크립트는 컴파일러 언어에 더 가깝습니다.

<br>

### 자바스크립트의 연산자

- 논리적인 계산을 수행하는 기호나 키워드를 말합니다. 변수, 상수, 리터럴과 같은 피연산자들을 이용하여 다양한 연산을 수행하는데 사용됩니다.

1. 산술 연산자 (Arithmetic Operators): 덧셈(+), 뺄셈(-), 곱셈(*), 나눗셈(/), 나머지(%) 등을 수행합니다.

2. 할당 연산자 (Assignment Operators): 변수에 값을 할당하기 위해 사용됩니다. 예를 들어, =는 오른쪽 값을 왼쪽 변수에 할당합니다.

3. 비교 연산자 (Comparison Operators): 두 값을 비교하여 논리적인 참 또는 거짓을 반환합니다. 예를 들어, >, <, >=, <=, ===, !== 등이 있습니다.

4. 논리 연산자 (Logical Operators): 논리적인 연산을 수행하여 논리값(참 또는 거짓)을 반환합니다. && (논리 AND), || (논리 OR), ! (논리 NOT) 등이 있습니다.

5. 조건(삼항) 연산자 (Conditional (Ternary) Operator): 조건문을 축약하여 표현할 수 있는 연산자입니다. condition ? expr1 : expr2의 형태로 사용됩니다.

6. 타입 연산자 (Type Operators): 자료형을 확인하는데 사용되는 연산자로, typeof와 instanceof가 있습니다.

7. 비트 연산자 (Bitwise Operators): 이진수를 비트 단위로 조작하는 연산자로, 비트 AND(&), 비트 OR(|), 비트 XOR(^), 비트 NOT(~) 등이 있습니다.

8. 쉼표 연산자 (Comma Operator): 여러 표현식을 연결하여 순차적으로 실행할 때 사용합니다.

<br>

### 자바스크립트의 참조 타입(reference type)

- 참조 타입은 객체(Object), 배열(Array), 함수(Function)와 같이 데이터를 저장하는 데 사용되는 자바스크립트의 데이터 타입입니다. 이러한 데이터 타입은 실제로 메모리의 주소를 참조하여 값을 저장하고 접근합니다. 자바스크립트에서 원시 타입이 아닌 모든 데이터는 근본적으로 객체입니다.

- 따라서 이러한 데이터 타입을 변수에 할당할 때, 변수는 값 자체를 저장하는 것이 아니라 값이 저장된 메모리 위치를 참조하게 됩니다.

1. 객체(Object): 객체는 여러 개의 속성(또는 키-값 쌍)을 포함하는 컨테이너입니다. 속성은 이름(키)과 값으로 구성되며, 값으로는 숫자, 문자열, 불리언, 배열, 다른 객체 등 모든 자바스크립트 데이터 타입이 올 수 있습니다.

```
const person = {
    name: "John",
    age: 30,
    address: {
        city: "New York",
        country: "USA"
    }
};
```

2. 배열(Array): 배열은 순서대로 나열된 데이터의 모음입니다. 각 데이터 요소는 인덱스를 사용하여 접근할 수 있습니다.

```
const fruits = ["apple", "banana", "orange"];
```

3. 함수(Function): 함수는 재사용 가능한 코드 블록을 정의하는 객체입니다. 함수는 코드 블록을 실행하고 결과를 반환할 수 있습니다. 함수는 변수에 할당하거나 다른 함수에서 반환될 수도 있습니다.

<br>

- 참조 타입은 메모리를 효율적으로 사용하며, 복잡한 데이터 구조를 생성할 수 있는 강력한 도구입니다. 참조 타입은 값 복사가 아니라 참조 복사이므로 변수 간의 데이터 공유가 발생할 수 있습니다.

```
(객체)
const obj1={num:1 , str : "ABC"};
const obj2=obj1;

obj2.num = 2;
obj2.str = "가나다";
console.log(obj1,obj2);
```

- 위 코드에서 obj1 도 변경된 obj2 의 값과 동일해진 것을 확인할 수 있습니다. JavaScript에서 객체는 참조 타입에 해당하며, 변수에 객체를 할당하면 변수에는 객체가 저장된 메모리 주소가 저장됩니다. 

- 따라서 obj2에 obj1을 할당하면, obj2는 obj1과 동일한 메모리 주소를 참조하게 되며 이로 인해 obj1과 obj2는 같은 객체를 가리키게 되는 것.

<br>

### 자바스크립트의 블록과 스코프

1. 블록문: 0개 이상의 statement(문 {})을 묶은 단위를 말하며 제어문 , 함수에서 사용합니다. 블록안에서 선언된 변수를 블록 외부에서 접근할 수 없습니다. 

2. 스코프: 변수가 유효한 범위를 나타내는 개념 입니다. 전역 스코프(Global Scope)와 지역 스코프(Local Scope)로 나뉩니다.

```
{
  const x = 'Hello'; // 지역 스코프
  let y = 'world!';
  console.log(x, y); // Hello World!
}

console.log(x); // error
console.log(y); // error
(스코프의 안에서는 바깥의 것들을 사용이 가능 합니다)

let x = 'Hello'; // 전역 스코프
{
    const y = 'World!';
    console.log(x,y); // Hello World!
}
```

<br>

### 자바스크립트의 호이스팅

- 호이스팅(hoisting)은 자바스크립트에서 변수 및 함수 선언이 스코프 내의 최상위로 끌어올려지는 현상을 말합니다. 이는 코드 실행 전에 발생하며, 코드 블록 내에서 변수 및 함수가 선언되기 전에도 참조할 수 있다는 특징을 가지고 있습니다.

1. 변수 호이스팅(Variable Hoisting): 변수 선언은 해당 스코프의 최상위로 끌어올려집니다. 이때 변수의 초기화는 끌어올려지지 않습니다. const와 let은 블록 스코프(block scope)를 갖기 때문에 호이스팅되지 않습니다. 

- 이는 변수가 선언된 블록 내부에서만 유효하며, 블록 외부에서는 접근할 수 없음을 의미합니다. 따라서 블록 내부에서 변수가 선언되기 전에 해당 변수에 접근하려고 하면 에러가 발생합니다.

```
console.log(x); // undefined
var x = 10;

// 실제 동작시
var x;
console.log(x); // undefined
x = 10;
```

2. 함수 호이스팅(Function Hoisting): 함수 선언은 해당 스코프의 최상위로 끌어올려집니다. 이때 함수의 정의부가 끌어올려지며, 함수 표현식은 호이스팅되지 않습니다

```
// 함수는 실행문보다 나중에 정의하는 것이 가능
// 변수나 상수는 불가능! (var 제외: 변수 호이스팅)
console.log(add(2, 7));

function add (x, y) {
  return x + y;
}
```

- 호이스팅의 경우 코드의 가독성을 해치거나 예상하지 못한 결과를 만들어 낼 수 있기에 변수, 함수를 사용되기 전 적절한 위치에 선언하는 것이 중요합니다.

<br>

### 일급 객체(First Class Object)

- 프로그래밍 언어는 해당 언어의 함수들이 다른 변수처럼 다루어질 때 일급 함수를 가진다고 합니다. 예를 들어, 일급 함수를 가진 언어에서 함수는 다른 함수들에 전달인자로 제공되고, 다른 함수에 의해 반환될 수 있으며, 변수에 값으로서 할당될 수 있습니다.

- 쉽게 말하자면 "함수를 변수와 같이 다루는 언어에 있는 개념" 이라고 표현할 수 있습니다. 자바스크립트의 함수 또한 일급 객체 입니다.

1. 함수의 자료형

```
// ⭐️ 함수의 자료형
function addNumbers (a, b) { return a + b; }
console.log(typeof addNumbers); // function 출력
console.log(addNumbers instanceof Object) // 함수가 객체에 속하는지를 물어보는 개념 , true 가 출력 되는 것을 확인 할 수 있음.
```

2. 일급 객체의 특징: 상수 또는 변수에 할당 될 수 있습니다, 다른 함수에 인자로 전달 될 수 있고 결과 값으로 반환 될 수 있습니다.

```
// 함수를 변수에 할당
function isOddNum (number) {
  console.log(
    (number % 2 ? '홀' : '짝')
    + '수입니다.'
  ); 
  return number % 2 ? true : false;
};

const checkIfOdd = isOddNum; // 뒤에 괄호 없음 유의
// isOddNum(); 괄호를 붙이게 되면 함수가 즉시 실행 됩니다.

console.log(checkIfOdd(23)); // true 반환
```

<br>

```
// 참조 타입
let x = 7, y = 3;

let func1 = (a, b) => a + b; // Arrow function
let func2 = (a, b) => a - b;
console.log(func1(x, y), func2(x, y)); // 10 , 4 출력

func1 = func2 // func1에 func2 할당
console.log(func1(x, y), func2(x, y)); // 4 , 4 출력
```

<br>

```
// 객체의 요소로 들어가는 함수

let person = {
  name: '홍길동',
  age: 30,
  married: true,
  introduce: function (formal) {
    return formal
    ? '안녕하십니까. 홍길동 대리라고 합니다.'
    : '안녕하세요, 홍길동이라고 해요.';
  } 
};

console.log(person.introduce(true));
console.log(person.introduce(false));

// 배열에서 Arrow function 사용 하기

let arithmetics = [
  (a, b) => a + b,
  (a, b) => a - b,
  (a, b) => a * b,
  (a, b) => a / b
];

for (arm of arithmetics) {
  console.log(arm(5, 3));
}
```

<br>

- 객체(Object) 에서 사용되는 함수 프로퍼티를 메서드(method) 라고 구분하여 불렀으나 ES6 부터는 메서드의 정의가 달라졌습니다.

<br>

### 자바스크립트의 고차함수 & 콜백함수

- 함수가 다른 함수를 인자로 전달 받을 때 전달받는 함수를 고차 함수(highter-order function) 전달되는 함수를 콜백 함수(callback function)라고 합니다.

```
let list = [1, 2, 3, 4, 5];

function doInArray (array, func) {
  for (item of array) {
    func(item);
  }
}

// console.log - console이란 객체에서 log란 키에 할당된 함수
// doInArray : 고차 함수
// console.log : 콜백 함수
doInArray(list, console.log);
```

- doInArray 함수를 살펴보면 인자로 배열과 함수를 받아 func(item) 을 실행하는 것을 볼 수 있습니다. doInArray(list , console.log) 함수를 호출 하는 부분에서 list(배열)을 받아서 console.log(func) 모든 배열을 console.log 하겠다! 라는 의도를 확인할 수 있습니다.

### 커링(currying)

- currying 이란 필요한 인자보다 적은 수의 인자를 받으면, 나머지 인자를 인자로 받는 다른 함수를 반환하는 것을 말합니다.

```
function addMultSubt (a, b, c, d) {
  return (a + b) * c - d;
}

const addMultSubt2 = (a, b, c, d) => (a + b) * c - d;

console.log(
  addMultSubt(2, 3, 4, 5), // print 15
  addMultSubt2(2, 3, 4, 5), // print 15
);
```

- 숫자 4개를 받아서 더하고 , 곱하고 , 뺀것의 값을 반환 하는 기본 함수, Arrow function 임을 확인 할 수 있습니다. 이것을 커링으로 작성 해보겠습니다.

```
// ⭐ 커링으로 작성된 함수
function curryAddMultSubt (a) {
  return function (b) {
    return function (c) {
      return function (d) {
        return (a + b) * c - d;
      } // (a)를 받은 함수는 
    } // (b)를 받는 함수를 리턴하고
  } // 얘는 또 (c)를 받는 함수를 리턴하고
} // 얘는 또 (d)를 받아서 a,b,c,d 로 계산 하여 return 하는 함수

const curryAddMultSubt2 = a => b => c => d => (a + b) * c - d;
```

<img src="https://velog.velcdn.com/images/rlcks01537/post/e44111e7-1ec6-48ab-80f9-9690c837f14d/image.png" />

- 이런 방식으로 코드를 수정하는 것이 가능합니다. 결과 값을 출력 하는 방법은 실행 괄호를 연속으로 사용해서 값을 호출할 수 있습니다.

```
console.log(
  curryAddMultSubt(2)(3)(4)(5), //실행 괄호를 연속으로 사용 합니다.
  curryAddMultSubt2(2)(3)(4)(5) // 15
);
```

<br>

### 재귀 함수(recursive function)

- 함수 안에서 해당 함수를 또 다시 호출하는 함수입니다.

```
function upto5 (x) {  // upto5 function 선언
  console.log(x);
  if (x < 5) {
    upto5(x + 1);  //자기 자신을 호출
  } else {
    console.log('- - -');
  };
}

upto5(1);
upto5(3);
upto5(7);
```

- 재귀함수를 잘못 사용하면 무한루프에 빠지게 될 수 있습니다. 또한 stack 영역에서 많은 메모리를 사용하기 때문에 stack overflow 발생하여 오류를 만들 수 있습니다.

- 함수가 잘 작동하기 위해서는 외부환경에 영향을 받는 함수, 또는 외부 환경을 변경 시키는 함수를 작성하지 않는 것이 좋다는 것을 알 수 있습니다.

- 이상적인 함수는 받은 값들을 처리하여 새 값을 반환 하고, 한 함수에 너무 많은 역할을 부여하는 것이 아닌, 적은 기능을 수행하는 여러개의 함수를 작성 하는 것이 좋다고 생각됩니다.

<br>