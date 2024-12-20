# Interview Data Structure

### 자료구조란 무엇인지 설명해주세요.

- 자료 구조는 효율적으로 데이터를 관리하고 수정, 삭제, 탐색, 저장 할 수 있는 데이터의 집합을 말합니다. 자료구조의 효율성은 복잡도라는 수치를 사용해서 나타낼 수 있는데, 크게 시간 복잡도와 공간 복잡도로 나뉘게됩니다.

<br>
<br>
<br>

### 시간 복잡도와 공간복잡도가 무엇인가요?

- 시간 복잡도란 "문제를 해결하는 데 걸리는 시간과 입력의 함수 관계"를 말합니다. 어떤 알고리즘의 로직이 얼마나 오랜 시간이 걸리는 지를 나타낼 때 사용 되며, 이를 보통 빅오 표기법으로 나타냅니다. 시간 복잡도가 필요한 이유는 바로 효율적인 코드를 개선하는 데 쓰이는 척도가 되기 때문 입니다. 

- 공간 복잡도는 프로그램을 실행 시켰을 때 필요로 하는 자원 공간의 양을 말합니다.

> int a[1004]; // C++

- 위 C++ 예시에서는 a 배열은 1004 X 4 바이트의 크기를 가지게 되는데, 이러한 공간을 말합니다.

<br>
<br>
<br>

### 시간 복잡도의 단위에 대해 설명해주세요.

1. 𝑂(1) - 상수 시간 (Constant Time)

```
- 특징: 입력 크기와 무관하게 항상 일정한 시간에 작업이 완료됩니다. 
- EX: 배열에서 특정 인덱스의 값을 접근하기, 스택의 push/pop 연산. 
- 속도: 가장 빠름.
```

2. O(log 𝑛) - 로그 시간 (Logarithmic Time)

```
- 특징: 입력 크기가 증가할수록 작업 시간은 느리게 증가합니다. 일반적으로 이진 탐색과 관련.
- EX: 이진 탐색(Binary Search), 균형 이진 탐색 트리(BST)에서 삽입/삭제.
- 속도: 매우 빠름.
```

3. O(𝑛) - 선형 시간 (Linear Time)

```
- 특징: 입력 크기 𝑛 에 비례하여 시간이 증가합니다.
- EX: 배열에서 모든 요소를 순회(탐색)하기.
- 속도: 중간 수준, 데이터 크기가 클수록 느려짐.
```

4. O(𝑛log 𝑛) - 로그 선형 시간 (Log-Linear Time)

```
특징: 𝑛번 반복하며 각 반복에 대해 log𝑛 시간 작업을 수행.
EX: 효율적인 정렬 알고리즘(퀵 정렬, 병합 정렬).
속도: 선형보다 느리지만 𝑂(𝑛2) 보다는 빠름.
```

5. O(n^2) - 이차 시간 (Quadratic Time)

```
- 특징: 입력 크기 𝑛에 대해 n2번 작업을 수행.
- EX: 중첩된 루프, 버블 정렬, 삽입 정렬.
- 속도: 느림. 입력 크기가 클수록 급격히 느려짐.
```

6. 𝑂(𝑛!) - 팩토리얼 시간 (Factorial Time)

```
- 특징: 𝑛의 팩토리얼(𝑛!)에 따라 작업 시간 증가.
- EX: 외판원 문제(모든 경로 탐색), 순열 생성.
- 속도: 가장 느림. 현실적으로 다루기 힘듦.
```


### 선형 자료구조란 무엇인가요?

- 선형 자료 구조란 요소가 일렬로 나열 되어져 있는 자료 구조를 말합니다. 대표적으로 연결 리스트, 배열, 스택, 큐등의 자료구조를 에시로 들 수 있습니다.

<br>
<br>
<br>

### 연결리스트(Linked List)에 대해 설명해주세요.

- 연결 리스트는 데이터를 감싼 노드를 포인터로 연결해서 공간 효윬성을 극대화 시킨 자료 구조 입니다. 삽입, 삭제가 상수 시간이 걸리며 탐색에는 선형 시간이 걸립니다.

- 연결 리스트는 크게 싱글 연결, 이중 연결, 원형 이중 연결 리스트 등으로 나뉘며 각각 next 포인터, next | prev 포인터, 마지막 노드의 next 포인터가 헤드 포인터(가장 첫 번쨰 노드)를 가리킨다는 특징을 가지고 있습니다.

<br>
<br>
<br>

### 배열에 대해 설명해주세요.

- 배열은 같은 타입의 변수들로 이루어져 있고, 크기가 정해져 있으며 인접한 메모리 위치에 있는 데이터들을 모아놓은 집합을 말합니다.

- 중복을 허용하고 순서가 존재 하며, 탐색에 상수 시간이 소모 되며 랜덤 접근이 가능합니다. 삽입, 삭제에는 선형 시간이 걸립니다.

<br>
<br>
<br>

### 랜덤 접근과 순차적 접근에 대해 설명해주세요.

- 직접 접근 이라고도 하는 랜덤 접근은 배열과 같은 순차적인 데이터가 있을 떄, 동일한 시간에 임의의 인덱스에 해당하는 데이터에 접근 가능한 기능을 말합니다. 데이터를 저장 된 순서대로만 검색해야 하는 순차적 접근과는 반대의 개념에 있습니다.

<br>
<br>
<br>

### 배열과 연결리스트를 비교 설명해주세요.

- 배열 => 상자를 순서대로 나열한 데이터의 구조 | 몇 번째 상자 인지만 알면 해당 상자에 해당하는 요소를 가져올 수 있습니다.

- 연결 리스트 => 상자를 선으로 연결한 형태의 데이터 구조 | 상자 안의 요소를 알기 위해서는 하나씩 상자의 내부를 확인 해봐야 하는 점이 다릅니다.

- 랜덤 접근가능(배열) , 랜덤 접근 불가능(연결 리스트)

- 따라서 탐색은 배열이 빠르고(상자만 알면 요소 확인 가능), 데이터의 추가 또는 삭제(상자에 선을 연결하거나 끊어서 추가, 삭제)는 연결 리스트가 빠르다는 것을 알 수 있습니다.

<br>
<br>
<br>

### 스택에 대해 설명해주세요.

- 스택은 가장 마지막으로 들어간 데이터가 가장 첫 번째로 나오는 성질(LIFO, Last In First Out)을 가진 자료 구조 입니다. 재귀 함수, 알고리즘에 사용 되며 웹 브라우저 방분 기록 등에 사용 됩니다. 삽입, 삭제에 상수 시간, 탐색에 선형 시간이 걸립니다. === 연결 리스트와 동일 시간 복잡도를 가지고 있습니다.

<br>
<br>
<br>

### 큐에 대해 설명해주세요.

- 큐는 먼저 집어넣은 데이터가 먼저 나오는 성질(FIFO, First In First Out)을 지닌 자료 구조 입니다. CPU 작업을 기다리는 프로세스, 스레드 행렬, 네트워크 접속을 기다리는 행렬, 너비 우선 탐색, 캐시 등에 사용 합니다.

- 스택과는 반대가 되는 개념을 가졌으며 삽입, 삭제에 상수 시간, 탐색에는 선형 시간이 걸립니다. === 시간 복잡도는 연결 리스트, 스택과 동일합니다.

<br>
<br>
<br>

### 비선형 자료구조란 무엇인가요?

- 비선형 자료 구조란 일렬로 나열하지 않고 자료 순서나 관계가 복잡한 구조를 가진 것을 말합니다. 대표적으로 트리, 그래프로 나뉩니다.

<br>
<br>
<br>

### 그래프에 대해 설명해주세요.

- 그래프는 정점 & 간선으로 이루어진 자료 구조를 말합니다. A <=> B(양방향 간선) 로 이동 할 때, A,B 는 정점(vertex), <=> 는 간선(edge)이 됩니다. 한 곳으로 이동하는 A => B 와 같은 경우를 단방향 간선 이라고 합니다.

- 정점으로 부터 나가는 간선을 해당 정점의 outDegree 라고 하며, 들어오는 간선을 해당 정점의 inDegree 라고 합니다. 정점의 약자는 V & U 라고 합니다. 위 설명한 정점과 간선으로 이루어진 집합을 그래프라고 합니다.

- 가중치: 가중치란 간선과 정점 사이에 드는 비용을 말합니다. A노드에서 B노드로의 가는 비용이 한 칸 이라고 하면 가중치는 한 칸 입니다.

<br>
<br>
<br>

### 트리 구조에 대해 설명해주세요.

- 트리는 그래프 중 하나로 그래프의 특징과 같이 정점과 간선으로 이루어져 있으며, 트리 구조로 배열된 계층적 데이터의 집합을 말합니다. 루트 노드, 내부 노드, 리프 노드 등으로 구성 되어 있으며 트리로 이루어진 집합을 "숲" 이라고 합니다.

- 부모, 자식의 계층 구조를 가집니다. 같은 경로 상의 어떤 노드 보다 위에 있으면 부모, 아래에 있으면 자식 노드가 됩니다. V(노드의 수) - 1 = E(간선의 개수) 라는 특징이 있습니다. 간선의 수는 노드 수 -1 입니다. 임의의 두 노드 사이의 경로는 유일무이 하게 반드시 존재 합니다.

- 이진 트리는 최대 2개의 자식 노드를 가질 수 있는 트리 구조를 말합니다. 크게 다음과 같이 나뉘어 집니다.

```

- 정이진 트리(Full Binary Tree): 자식 노드가 0 또는 두개인 이진 트리를 의미.

- 완전 이진 트리(Complete Binary Tree): 왼쪽에서 부터 채워진 이진 트리를 의미. 마지막 레벨을 제외 모든 레벨이 완전히 채워져 있으며 마지막의 경우 왼쪽 부터 채워져 있음.

- 변질 이진 트리(Degenerate Binary Tree): 자식 노드가 하나 밖에 없는 이진 트리를 의미.

- 포화 이진 트리(Perfect Binary Tree): 모든 노드가 꽉 차 있는 이진 트리를 의미.

- 균형 이진 트리(Balanced Binary Tree): 왼쪽, 오른쪽 노드의 높이차이가 1 이하인 이진트리를 의미. map, set => 레드 블랙 트리(군형 이진 트리 중 하나)

```

### 이진 탐색트리에 대해 설명해주세요.

- 이진 탐색 트리(BST)란 노드의 오른쪽 하위 트리에는 노드 값보다 큰 값이 있는 노드만 포함되고, 왼쪽 하위 트리에는 노드 값 보다 작은 값이 들어 있는 트리를 의미합니다.

- 위와 같은 특성을 가지고 있기에 "검색"에 용이 합니다. 왼쪽에는 작은 값, 오른 쪽에는 큰 값이 이미 정해져 있기 때문에, 특정 값을 찾으려고 한다면 루트 노드의 특징에 따라 큰 값 또는 작은 값만을 찾으면 되기 떄문 입니다.

- 보통 요소를 찾을 떄 이진 탐색 트리의 경우 로그 시간이 소요 됩니다. 최악의 경우 상수 시간이 소요 됩니다. 여기서 최악의 경우란 예를 들어 모든 노드의 값이 루트노드보다 값이 클 때를 말합니다. 1-2-3-4 의 노드가 있다고 가정할 때 이진 탐색 트리가 선형적인 구조를 가지게 되는데 4의 값을 찾기 위해서 모든 노드를 찾아봐야 하기에 최악의 경우가 발생할 수 있는 것 입니다.

<br>
<br>
<br>

### 힙에 대해 설명해주세요.

- 힙은 완전 이진 트리 기반의 자료 구조이며 최소힙과 최대힙 두 가지가 있습니다. 해당 힙에 따라 특정한 특징을 지닌 트리를 말합니다.

- 최대힙: 루트 노드에 있는 키는 모든 자식에 있는 키 중에서 가장 커야 합니다.

- 최소힙: 최소힙에서 루트 노드에 있는 키는 모든 자식에 있는 키 중에서 최솟값이어야 합니다. 또한 각 노드의 자식 노드와의 관계도 이 특징이 재귀적으로 
이루어져야 합니다.

- 최대힙의 삽입 & 삭제는 다음과 같은 방식으로 이루어집니다. 

- 힙에 새로운 요소가 들어오면, 우선 새로운 노드를 힙의 마지막 노드에 이어서 삽입 합니다. 이후 새로운 노드를 부모 노드들과의 크기를 비교해가며 교환하여 힙의 성질을 만족 시킵니다.

- 최대힙에서 최댓값은 루트 노드이므로 루트 노드가 삭제되고, 이후 마지막 노드와 루트 노드를 스왑 => 또 다시 스왑 하는 과정을 거쳐 재구성 합니다.

<br>
<br>
<br>

### 우선 순위 큐에 대해 설명해주세요.

- 우선순위 큐는 우선순위 대기열 이라고도하며, 대기열에서 우선순위가 높은 요소가 우선 순위가 낮은 요소보다 먼저 제공 되는 자료구조를 말합니다. 우선순위 큐는 힙을 기반으로 구현 됩니다.

<br>
<br>
<br>

- ### 해시 테이블에 대해 설명해주세요.

- 해시 테이블은 무한에 가까운 데이터를 유한한 개수의 해시 값으로 매핑한 테이블을 말합니다. 삽입, 삭제, 탐색 시 평균적으로 상수 시간의 시간 복잡도를 가집니다. JavaScript 에서 객체(Object)는 해시 테이블의 일종으로 볼 수 있습니다.