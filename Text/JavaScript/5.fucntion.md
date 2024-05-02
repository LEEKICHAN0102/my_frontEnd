# 함수(function)

- 함수란 자신의 외부(재귀 함수의 경우 스스로) 코드가 '호출'할 수 있는 하위 프로그램입니다. 프로그램과 마찬가지로, 함수 역시 명령문의 시퀀스로 구성된 함수 본문을 가집니다. 함수에 값을 '전달'하면, 함수는 값을 '반환'할 것입니다.

- 함수의 특징은 반복 될 수 있는 작업을 정의,  input 을 받아 output 을 return , 호이스팅 등이 있습니다. 하나씩 살펴봅시다.

### 기본적인 함수의 작성

- 우선 함수의 기본 작성 방법입니다. 함수는 함수명을 가지며 input을 받아 수행할 statement를 진행한 뒤 output을 반환합니다. 함수명() 으로 함수를 호출할 수 있습니다.

```
(기본 문법)
function 함수명 (input) {
  // 수행할 statement
  return output // 존재 할때
}

함수명(입력값); // 함수를 호출하는 법
```

<br>

- 다음과 같이 반복되는 작업에서 유용하게 사용할 수 있습니다. x, y input을 받고 수행한 결과 값을 return 합니다.

```
function addNum(x,y){
	console.log(x+y);
}

let num1=1 ,num2=2; 
addNum(num1,num2);  // 작업이 여러번 반복 수행 할 시에 함수 정의
let num3=3 ,num4=4; 
addNum(num3,num4);  // 작업이 여러번 반복 수행 할 시에 함수 정의
let num5=5 ,num6=6; 
addNum(num5,num6);  // 작업이 여러번 반복 수행 할 시에 함수 정의
```

<br>

- 모든 함수가 꼭 인자를 받거나 값을 반환 하는것은 아닙니다.

```
let currentTemp = 24.5;

function logCurrentTemp () {
  console.log(`현재 온도는 섭씨 ${currentTemp}도입니다.`);
}

console.log('반환값:', logCurrentTemp()); // 반환값:undefined 출력
```

<br>

### 호이스팅(hoisting)

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

- 객체(Object) 에서 사용되는 함수 프로퍼티를 메서드(method) 라고 구분하여 불렀으나 ES6 부터는 메서드의 정의가 달라졌습니다. ES6부터는 메서드를 정의할 때 메서드 이름과 함수를 구분하기 위해 콜론(:)을 사용하지 않고, 함수명만 작성하며 함수 표현식이나 화살표 함수를 사용할 수 있습니다.

<br>

### this

- 객체의 프로퍼티를 메서드에서 사용할 때 this 키워드를 사용합니다. 

```
let person = {
  name: '홍길동', // 이걸 메서드에서 사용하고 싶어! => this.name 으로 활용 가능
  age: 30,
  married: true,
  introduce() {  // ES6 부터 사용되는 : 을 붙이지 않은 메서드 선언 방식
    return `저는 ${this.name}, ${this.age}살이고 `
    + `${this.married ? '기혼' : '미혼'}입니다.`;
  }
}

console.log(person.introduce());
```

<br>

### 화살표 함수(Arrow Function)

- 화살표 함수(arrow function)는 ES6(ECMAScript 2015)에서 도입된 새로운 함수 정의 방식입니다. 기존의 함수 표현식에 비해 간결하고 간편하게 함수를 정의할 수 있으며, 주로 익명 함수나 콜백 함수를 작성할 때 많이 사용됩니다.

```
// 기본 작성 방식 (함수명 X)
const arrowFunc = (parameters) => {
    // 함수 내용
};
```

- 화살표 함수의 대표적인 특징으로 자기 바인딩(this binding)이 있습니다. 자기 바인딩이란 화살표 함수는 자신의 this를 바인딩하지 않고, 외부 스코프의 this를 그대로 사용합니다. 이는 화살표 함수가 생성될 때의 상위 스코프의 this를 기억하고 있기 때문입니다.

```
const obj = {
    name: '기찬',
    greet: function() {
        console.log('Hello, ' + this.name);
    },
    greetArrow: () => {
        console.log('Hello, ' + this.name); 
    }
};

obj.greet(); // 출력: Hello, 기찬
obj.greetArrow(); // 출력: Hello, 

// 화살표 함수에서 정상 출력을 하기위해선 this 가 아닌 obj.name으로 변경하여야 합니다.
```

- 위 예시에서 greetArrow 메서드는 화살표 함수이므로 내부의 this는 외부 스코프의 this를 가리키게 되어 " " 가 출력 되게 됩니다. 아마 화살표 함수가 가리키는 this는 window가 될 것입니다(전역 스코프의 this는 window 객체임).

- 대부분의 경우 window.name은 현재 창 또는 프레임의 이름을 나타내는데 사용됩니다. 하지만 일반적으로 이 값은 비어 있거나 웹 개발자가 명시적으로 설정한 값이 들어가게 됩니다. `console.log(window.name)`

<br>

- 또한 단일 표현식의 경우 중괄호 생략할 수 있습니다. 함수의 내용이 단일 표현식인 경우 중괄호 {}와 return 키워드를 생략할 수 있고 이때 화살표 오른쪽에는 표현식이 오게 됩니다.  (간단 예시) `const pow = x => x ** 2; console.log(pow(3));`

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

### 매개 변수

- 함수의 매개변수 갯수를 넘어가는 인수는 어떻게 될까요? 

```
function addNum (x,y) {
	return x+y;
}

console.log(
	addNum(1,3), // 4
    addNum(1,3,5), // 4
    addNum(1,3,5,7), // 4
);
따로 오류를 일으키지 않고 추가적인 인자를 그냥 무시해버립니다. (모두 4 가출력)
```

<br>

- 매개 변수의 기본 값? (default Parameter)

```
function addNum (x=2,y=4) {
	return x+y;
}

console.log(
	  addNum(),  // 6
    addNum(1), // 5
    addNum(1,3) // 4
);
```

- 함수를 선언시 매개변수에 x=2, y=4 라는 default parameter 를 작성하였습니다. 함수 호출 시에 전달해 줄 argument 가 없을 때 default parameter 를 사용해 값을 나타내는 것을 확인 할 수 있습니다.

- argument 가 한 개 일땐 매개변수의 순서대로 x의 값이 1 이 되고 모두 전달 하였을 때 전달 된 값으로 결과를 반환 하는 것을 알 수 있습니다.

<br>

### arguments

- arguments란 배열의 형태를 한 객체(배열도 객체긴 함 ㅇㅇ;) arguments 는 함수 호출 시 전달된 모든 인수들을 배열 형태로 가집니다. Arrow function 에서는 arguments 사용이 불가능 합니다.

```
function add(a, b) {
  console.log('1.', arguments); // Arguments (4) 전달된 인수를 배열의 형태로 나타냄
  console.log('2.', arguments[2]); // 5
  console.log('3.', typeof arguments);  // object
  return a + b;
}

console.log(
  '4.', add(1, 3, 5, 7) // 4
);
```

<br>

### Rest Parameters

- Rest Parameter란 특정 매개변수들 뒤에 정해지지 않은 수의 매개변수들을 받을 때 사용 됩니다. 마지막 인자로만 사용이 가능하고 arguments와는 달리 실제 배열이라는 특징을 가지고 있습니다.

```
console.log(
  '3.',
  classIntro(3, '김민지', '영희', '철수', '보라')
); // 호이스팅

function classIntro (classNo, teacher, ...children) {
  console.log('1.', children);
  console.log('2.', arguments);

  let childrenStr = '';
  for (const child of children) {
    if (childrenStr) childrenStr += ', ';
    childrenStr += child;
  }
  return `${classNo}반의 선생님은 ${teacher}, `
    + `학생들은 ${childrenStr}입니다.`
}
```

<br>

코드를 확인해보면 ...chidlren(나머지 매개변수)를 사용해 첫 console.log('1.', children); 에서 매개변수 순서 대로 함수가 실행 됬을 시 teacher는 '김민지' 이기 때문에 그 나머지인 '영희', '철수', '보라'가 children 이 되는 것을 확인할 수 있습니다.

<br>

### 불변성(immutability)

- 아래 예시 코드를 따로따로 실행 해봅시다.

```
let x = 1;
let y = {
  name: '홍길동',
  age: 15
}
let z = [1, 2, 3];

function changeValue (a, b, c) {
  a++;
  b.name = '전우치';
  b.age++;
  c[0]++;

  console.log(a, b, c);
}

changeValue(x, y, z);  // 2 {"전우치", 16} [2,2,3] 출력
```

```
console.log(x, y, z); // 1 {"전우치", 16} [2,2,3] 출력
```

<br>

- x의 값이 변경 되지 않은 것을 확인 할 수 있습니다. let x = 1; 은 원시타입이기 때문입니다. 

- 객체나 배열은 인자로 들어간 함수 내에서 요소가 변하면 실제로도 변합니다. 복사된 값도 같은 객체나 배열을 가리키기 때문인데, x=1 과 같은 원시타입은 인자로 들어간 함수 내에서의 변경에 영향 받지 않습니다. ( 실제 값이 아니라 복사된 값이 들어갔기 때문에!)


