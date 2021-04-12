## 트리와 그래프

### 트리(Tree) 

`트리`의 탐색은 `배열`과 `연결리스트`같은 선형으로 구성된 자료구조와 달리 까다롭다.

> 트리의 기본 용어

|용어|설명|
|:---:|:---:|
|노드(Node)||
|가지(edge)||
|루트(Root)|트리의 가장 윗부분에 위치하는 노드<br/> 하나의 트리에는 하나의 루트가 있다.|
|리프(Leaf, terminal node, external node)|트리의 가장 아래 부분에 위치하는 노드<br/> 더 이상 뻗어나갈 수 없는 마지막 노드|
|자식(child)|어떤 노드로부터 가지로 연결된 아래쪽 노드<br/> 리프는 자식을 가질 수 없다.|
|부모(parent)|어떤 노드에서 가지로 연결된 위쪽 노드<br/> 노드는 1개의 부모를 갖는다.|
|형제(sibling)|같은 부모를 갖는 노드|
|조상(ancestor)|어떤 노드에서 가지로 연결된 위쪽 노드 전체|
|자손(descendant)|어떤 노드에서 가지로 연결된 아래쪽 노드 전체|
|레벨(level)|루트로부터 얼마나 떨어져 있는지에 대한 값 <br/> 루트의 레벨은 0이고 루트로부터 가지라 하나씩 아래로 뻗어나갈 때마다 레벨이 1씩 늘어난다.|
|차수(degree)|노드가 갖는 자식의 수 <br/> 모든 노드의 자식 수가 2개 이하인 경우는 이진트리라 부른다.|
|높이(height)|루트로부터 가장 멀리 떨어진 리프까지의 거리|
|서브 트리(subtree)|트리 안에 다시 어떤 노드를 루트로 정하고 그 자손으로 이루어진 트리|
|널 트리(null tree)|노드, 가지가 없는 트리|
|`순서 트리(ordered tree)` & `무순서 트리(unordered tree)`|형제 노드의 순서가 있는지 없는지에 따라 분류 <br/> 형제 노드의 순서를 따지는 경우 순서 트리, 그렇지 않으면 무순서 트리|

> 트리의 최소 성립 조건

- 트리는 하나의 `루트(root) 노드`를 갖는다.
- 루트 노드는 `0`개 이상의 `자식(child) 노드`를 갖고 있다.
- 그 `자식 노드` 또한 `0개 이상`의 `자식 노드`를 갖고 있고, 이는 반복적으로 정의 된다.
- 트리에는 `사이클(cycle)`이 존재할 수 없다.

> 트리를 구분하기 위한 차이점

- 트리 vs 이진 트리 (노드의 `차수(degree)`에 따른 분류)
   - 트리는 각 노드에 `자식노드`가 존재하는지에 따라 `이진(binary)트리`, 다진 트리로 분류된다.

- 이진 트리 vs 이진 탐색트리 (노드의 자식노드가 어떤 `규칙`으로 정렬되어 있는지에 따른 분류)
   - 이진 탐색트리는 특정 순서에 따라 자식노드가 정렬되어 있다.
   - `모든 왼쪽 자식 노드들(left child node)` <= `현재노드` < `모든 오른쪽 자식 노드들(right child node)`
   - 위 속성은 모든 노드 관계에 적용된다.

- 균형 vs 비균형
   - 균형이란 왼쪽과 오른쪽 부분 트리의 크기가 완전히 같게 하는 것을 의미하지는 않는다.
   - `insert`, `find` 작업을 할 때 작업 시간이 `O(logN)` 내에만 이루어지면 되는 정도를 뜻한다.
   - 균형트리의 일반적인 유형으로는 레드-블랙 트리, AVL 트리 두 가지 정도가 있다.

- `완전 이진트리(complete binary tree)`의 특성
   1. 트리의 모든 높이에서 노드가 꽉 차 있는 이진트리
   2. 마지막 단계(level)는 꽉 차 있지 않아도 되지만 노드가 왼쪽에서 오른쪽으로 채워져야 한다.

- `전 이진트리(full binary tree)`의 특성
   1. 모든 노드의 자식이 없거나 정확히 두 개 있는 경우, 즉 자식 노드가 하나만 존재해서는 안된다.
   
- `포화 이진 트리(perfect binary tree)`의 특성
   1. 전 이진트리이면서 완전 이진트리인 경우
   2. 모든 말단 노드는 같은 높이에 있어야 하며, 마지막 단계에서 노드의 계수가 최대가 되어야 한다.

> 순서 트리를 스캔하는 방법

|트리 자료구조|트리 탐색 방식|구현 방식|
|:---:|:---:|:---:|
|트리|너비 우선 탐색(Breadth First Search, BFS)|Queue|
|트리|깊이 우선 탐색(Depth First Search, DFS)|Stack|

- `너비 우선 탐색`
   - 낮은 레벨에서 시작해 왼쪽에서 오른쪽 방향으로 검색한다.
   - 한 레벨에서 검색이 끝나면 다음 레벨로 내려간다.

- `깊이 우선 탐색`
   - 리프까지 내려가면서 검색하는 것을 우선순위로 하는 탐색 방법
   - 리프에 도달해 더 이상 검색을 진행할 곳이 없는 경우 부모에게 돌아간다.
   - 그 다음 다시 자식 노드로 내려간다.
   - 이때, 루트 노드를 최대 3번 지나가게 된다.

- 깊이 우선 탐색을 진행하면서 `언제 루트 노드를 방문할 지`는 아래와 같이 세 가지의 방식으로 분류할 수 있다.

|트리 자료구조|트리 탐색 방식|탐색 순서|탐색 순서|주로 사용되는 상황|
|:---:|:---:|:---:|:---:|:---:|
|이진트리<br> 완전이진트리<br> 이진검색트리|전위 순회(pre-order)|루트를 가장 먼저 방문|current -> left -> right|DFS와 같은 탐색|
|이진트리<br> 완전이진트리<br> 이진검색트리|중위 순회(in-order)|결과가 오름차순 출력|left -> current -> right|delete를 구현할 때 주로 사용|
|이진트리<br> 완전이진트리<br> 이진검색트리|후위 순회(post-order)|루트를 가장 마지막에 방문|left -> right -> current|상향식 탐색 방식<br>(다이나믹 문제에서 자주 사용됨)|

> 이진 힙

- `최소 힙(min-heaps)`과 `최대 힙(max-heaps)`

1. 최소 힙
   - 원소가 오름차순으로 정렬
   - 트리의 마지막 단계에서 오른쪽을 뺀 나머지 부분이 가득 채워져 있다는 점에서 완전 이진 트리와 같다.
   - 각 노드의 원소가 자식들의 원소보다 작다는 특성을 갖고 있다.
   - 루트는 트리 전체에서 가장 작은 원소가 된다.

   - 최소 힙의 핵심 연산 두 가지
      - `Insert`
         - 원소를 삽입할 때 트리의 밑바닥에서부터 삽입
         - 완전 트리의 속성에 위배되지 않도록 밑바닥 가장 오른쪽 위치로 삽입
         - 새 원소가 제대로 된 자리를 찾을 때까지 부모 노드와 교환하여 최종은 최소 원소가 루트에 있는 상태를 유지
         - 힙의 노드 개수가 n인 경우 연산은 `O(logN)`이 걸린다.

      - `extract_min`
         - 최소 원소는 언제나 가장 위에 놓인다.
         - 최소 원소를 제거하고 힙에 있는 가장 마지막 원소와 교환
         - 최소힙의 성질을 만족하도록, 해당 노드를 자식 노드와 교환해 나감으로써 밑으로 내보낸다.
         - 자식 노드로 교환해나갈 때 왼쪽, 오른쪽 원소 중 더 작은 원소와 교환한다.
         - 이 알고리즘 또한 `O(logN)`이 걸린다.

> 트라이(Trie)

- `접두사 트리(prefix tree)`라고도 불린다.
- 트라이는 N-차 트리(N-ary tree)의 변종으로 각 노드에 문자를 저장하는 자료구조이다.
- 트리를 아래쪽으로 순회하면 단어 하나가 나온다.