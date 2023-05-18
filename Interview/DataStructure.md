# 자료구조

<details>
  <summary>해시(Hash)에 대하여 설명해 주세요.</summary>
  <br>

- 데이터를 효율적으로 관리하기 위해, 임의의 길이 데이터를 고정된 길이의 데이터로 매핑하는 것입니다.
- 해시 함수를 구현하여 데이터 값을 해시 값으로 매핑합니다.
- 데이터가 많아지면, 다른 데이터가 같은 해시 값으로 충돌나는 현상이 발생함 `collision` 현상
    - 그래도 해시 테이블을 쓰는 이유는?
        - 적은 자원으로 많은 데이터를 효율적으로 관리하기 위해
        - 하드디스크나, 클라우드에 존재하는 무한한 데이터들을 유한한 개수의 해시값으로 매핑하면 작은 메모리로도 프로세스 관리가 가능해짐
        - 언제나 동일한 해시값 리턴, index를 알면 빠른 데이터 검색이 가능해짐
해시테이블의 시간복잡도 O(1) - (이진탐색트리는 O(logN))

### 충돌 문제 해결
- 체이닝 : 연결리스트로 노드를 계속 추가해나가는 방식 (제한 없이 계속 연결 가능, but 메모리 문제)
- Open Addressing : 해시 함수로 얻은 주소가 아닌 다른 주소에 데이터를 저장할 수 있도록 허용 (해당 키 값에 저장되어있으면 다음 주소에 저장)
- 선형 탐사 : 정해진 고정 폭으로 옮겨 해시값의 중복을 피함
- 제곱 탐사 : 정해진 고정 폭을 제곱수로 옮겨 해시값의 중복을 피함

</details>

<details>
  <summary>트리에 대하여 설명해 주세요.</summary>
  <br>

- 값을 가진 노드(Node)와 이 노드들을 연결해주는 간선(Edge)으로 이루어진 자료구조입니다.
- 모든 노드들은 0개 이상의 자식(Child) 노드를 갖고 있으며 보통 부모-자식 관계로 부릅니다.

### 특징
- 트리에는 사이클이 존재할 수 없다. (만약 사이클이 만들어진다면, 그것은 트리가 아니고 그래프다)
- 모든 노드는 자료형으로 표현이 가능하다.
- 루트에서 한 노드로 가는 경로는 유일한 경로 뿐이다.
- 노드의 개수가 N개면, 간선은 N-1개를 가진다.

### 트리 순회 방식
- 전위 순회(pre-order) : 각 루트(Root)를 순차적으로 먼저 방문하는 방식입니다. (Root → 왼쪽 자식 → 오른쪽 자식)
- 중위 순회(in-order) : 왼쪽 하위 트리를 방문 후 루트(Root)를 방문하는 방식입니다. (왼쪽 자식 → Root → 오른쪽 자식)
- 후위 순회(post-order) : 왼쪽 하위 트리부터 하위를 모두 방문 후 루트(Root)를 방문하는 방식입니다. (왼쪽 자식 → 오른쪽 자식 → Root)
- 레벨 순회(level-order) : 루트(Root)부터 계층 별로 방문하는 방식입니다.

</details>

<details>
  <summary>힙(heap)에 대하여 설명해 주세요.</summary>
  <br>

- 우선순위 큐를 위해 만들어진 자료구조입니다.
- 완전 이진 트리의 일종이며 반 정렬 상태입니다. 삽입과 삭제의 시간 복잡도가 O(logN)입니다.
- 여러 값 중, 최대값과 최소값을 빠르게 찾아내도록 만들어진 자료구조입니다.

### 종류
- 최대 힙(max heap)
- 최소 힙(min heap)

### 구현
- maxheap(class version)
```javascript
class maxheap{
    constructor() {
        this.heap = [];
    }

    swap(a,b){
        [this.heap[a],this.heap[b]] = [this.heap[b],this.heap[a]];
    }

    size(){
        return this.heap.length;
    }

    add(value){
        this.heap.push(value);
        let ind = this.size() - 1;
        let parent = Math.floor((ind-1)/2);
        while(value > this.heap[parent]){
            this.swap(ind,parent);
            ind = parent;
            parent = Math.floor((ind-1)/2);
        }
    }

    del(){
        if(this.size() === 0)
            return -1
        const last = this.size() - 1;
        let ind = 0;
        this.swap(ind,last);
        const temp = this.heap.pop();

        while(ind < last){
            let left = ind * 2 + 1, right = ind * 2 + 2;
            if(left >= last)
                break
            else if(right >= last){
                if(this.heap[left] > this.heap[ind]){
                    this.swap(ind,left);
                    ind = left;
                }
                else
                    break;
            }
            else{
                if(this.heap[left] < this.heap[right]){
                    if(this.heap[right] > this.heap[ind]){
                        this.swap(right,ind);
                        ind = right;
                    }
                    else
                        break;
                }
                else{
                    if(this.heap[left] > this.heap[ind]){
                        this.swap(left,ind);
                        ind = left;
                    }
                    else
                        break;
                }
            }
        }
        return temp;
    }
}
```
- minheap (array version)
```javascript
let minheap = [];

function insert(heap, num){
    heap.push(num);
    let ind = heap.length;
    while(ind>1){
        if(heap[Math.floor(ind/2)-1]>heap[ind-1]){
                const temp = heap[ind-1];
                heap[ind-1] = heap[Math.floor(ind/2)-1];
                heap[Math.floor(ind/2)-1] = temp;
                ind = Math.floor(ind/2);
        }
        else{
            break;
        }
    }
    return heap;
}

function del(heap){
    heap[0] = heap[heap.length-1];
    heap.pop();
    const len = heap.length;
    let ind = 1;
    while(ind*2<=len){
        if(heap[ind-1]>heap[ind*2-1] && (heap[2*ind]===undefined ||heap[ind*2-1] < heap[ind*2])){
            const temp = heap[ind*2-1];
            heap[ind*2-1] = heap[ind-1];
            heap[ind-1] = temp;
            ind = ind*2
        }
        else if(heap[ind-1]>heap[ind*2]){
            const temp = heap[ind*2];
            heap[ind*2] = heap[ind-1];
            heap[ind-1] = temp;
            ind = ind*2+1
        }
        else
            break;
    }
    return heap
}
```

</details>