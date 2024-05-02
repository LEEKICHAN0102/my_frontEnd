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

