# 자바스크립트의 참조 타입(reference type)

- 참조 타입은 객체(Object), 배열(Array), 함수(Function)와 같이 데이터를 저장하는 데 사용되는 자바스크립트의 데이터 타입입니다. 이러한 데이터 타입은 실제로 메모리의 주소를 참조하여 값을 저장하고 접근합니다. 자바스크립트에서 원시 타입이 아닌 모든 데이터는 근본적으로 객체입니다.

- 따라서 이러한 데이터 타입을 변수에 할당할 때, 변수는 값 자체를 저장하는 것이 아니라 값이 저장된 메모리 위치를 참조하게 됩니다.

### 객체(Object)

-  객체(Object): 객체는 여러 개의 속성(또는 키-값 쌍)을 포함하는 컨테이너입니다. 속성은 이름(키)과 값으로 구성되며, 값으로는 숫자, 문자열, 불리언, 배열, 다른 객체 등 모든 자바스크립트 데이터 타입이 올 수 있습니다.

```
const person1 = {
  name: '김철수', // property
  age: 25,	// property
  married: false	// property
};

console.log(typeof person1); //object
console.log(person1);	// JS 개발자 도구에서 객체를 자세히 볼 수 있다. (+[prototype]) 
```

- 객체의 속성 값을 가져오는 방법입니다.

```
// 점 표기법(Dot Notation)
console.log(person1.name); 
console.log(person1.age);
console.log(person1.married);

// 괄호 표기법(Bracket Notation)
console.log(
  person1['name'], // 속성명을 string으로
  person1['age'],
  person1['married'],
);
//속성 이름이 유효한 식별자가 아닐 때 , 동적으로 속성의 이름을 결정 할때 유용

//존재 하지 않는 key 로 접근 시 undifined를 반환 합니다.
console.log(person1.birth); // undifined
```

- 객체의 특정 키 포함 여부를 확인

```
console.log(
    'age' in person1, // true
    'job' in person1  // false
);
```

- 프로퍼티의 수정 & 추가하는 법

```
// 특정 프로퍼티의 값 변경
  person1.age = 26;
  person1['married'] = true

  console.log(person1);

// 새 프로퍼티 추가
  person1.job = 'FEdeveloper';
  person1['bloodtype'] = 'B'

  console.log(person1);
```

<br>

### 배열(Array)

- 배열(Array): 배열은 순서대로 나열된 데이터의 모음입니다. 각 데이터 요소는 인덱스를 사용하여 접근할 수 있습니다.

```
const winners = [12, 592, 7, 48];
const weekdays = ['월', '화', '수', '목', '금', '토', '일'];

// 자료형에 관계없이 한 배열에 넣을 수 있음
const randoms = ['이기찬', -24, true, null, undefined];

console.log(typeof winners); //object
console.log(winners, weekdays, randoms);
```

- console.log(winners) 의 결과 값을 확인해보면 object가 출력 되는 것을 확인 할 수 있습니다.

```
[12, 592, 7, 48]
0: 12
1: 592
2: 7
3: 48
length: 4
[[Prototype]]: Array(0)

console.log(winners.length) // 배열의 길이에 접근하는 법 winners 객체(배열)의 length
```

- x : y (키 & 값)와 같은 형태로 값이 나오는 이유는 배열 또한 객체에 속하기 때문입니다. 배열은 위 person1 객체와 다르게 length 라는 키 와 4라는 값이 나오는 것을 확인 할 수 있고 이를 활용하여 배열의 길이를 알 수 있습니다.

```
// 특정 순서의 값에 접근하는 법 (0부터 시작)
console.log(winners[0], weekdays[6], randoms[3]);
```

- 프로그래밍에서 시작은 0부터이기에 배열의 첫 번째 값을 얻고 싶다면 `array[0]` 을 통해 그 값을 알 수 있습니다. 마찬가지로 배열의 마지막 값을 알고 싶다면 `array[array.length-1]` 을 사용 할 수 있습니다.

- 배열의 수정과 추가는 어떻게 이루어지는지 알아봅시다.

```
const numbers = [1, 2, 3];

// 특정 위치의 값 수정
numbers[2] = 5;

console.log(numbers); // (3)[1,2,5]

// 맨 끝에 값 추가
numbers.push(10);

console.log(numbers); // (4)[1,2,5,10]
```

- 만약 배열의 범주를 넘은 값에 접근하게 된다면 undefined를 반환하게 됩니다.

```
const winners = [12, 592, 7, 48];
console.log(winners[winners.length]); // undefined
console.log(winners[-1]); // undefined
```

### 동적 메모리 할당(dynamic memory allocation)

- 앞서 말했듯이 JavaScript에서 객체는 참조 타입에 해당하며, 변수에 객체를 할당하면 변수에는 객체가 저장된 메모리 주소가 저장됩니다.

```
(참조 타입간단 예시)
const obj1={num:1 , str : "ABC"};
const obj2=obj1;

obj2.num = 2;
obj2.str = "가나다";
console.log(obj1,obj2);
```

- heap 영역이 가리키는 값을 변경하면 obj1이 가리키는 메모리 주소 또한 동일해지기 때문에 값이 변경이 되는 것 인데 여기서 heap 영역에 대해 알아봅시다.

- Heap 영역은 프로그램 실행 중 동적으로 메모리를 할당하는 데 사용됩니다. 프로그램이 실행되는 동안 컴파일 시점에 크기를 알 수 없는 데이터나 런타임에 생성되는 데이터 구조(예: 배열, 객체 등)는 Heap 영역에 할당되는데 이를 동적 메모리 할당 이라고 합니다.

- Heap 영역은 객체를 생성하는 데 사용되는데 객체는 주로 여러 프로퍼티를 포함하고 있으며, 이러한 복잡한 데이터 구조들은 Heap 영역에서 동적으로 생성됩니다. 

<br>

#### 원시 타입은 어떨까?

- 원시 타입(Primitive Types)은 컴파일 시점에 크기가 정해져 있고, 스택(Stack) 영역에 직접 값을 저장합니다. 스택은 함수 호출과 관련된 지역 변수들을 저장하는 영역으로, 자동으로 메모리를 관리합니다. 원시 타입 데이터는 스택에 직접 저장되기 때문에 메모리를 할당하거나 해제하는 과정이 필요하지 않습니다.
