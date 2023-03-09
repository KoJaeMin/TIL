## 알고리즘

### 거품 정렬 (Bubble Sort)
- 서로 인접한 두 원소의 대소를 비교하고, 조건에 맞지 않다면 자리를 교환하며 정렬하는 알고리즘
- 최선, 평균, 최악의 경우 모두 시간복잡도가 O(n^2) 으로 동일
- 주어진 배열 안에서 교환(swap)을 통해, 정렬이 수행되므로 공간복잡도는 O(n)

```javascript
function bubbleSort(arr) {
	for(let i = 0; i < arr.length; i++) {
		for(let j= 1 ; j < arr.length-i; j++) {
			if(arr[j-1] > arr[j]) {
				const temp = arr[j-1];
				arr[j-1] = arr[j];
				arr[j] = temp;
			}
		}
	}
}
```
```go
func BubbleSort(arr []int) {
	for i := 0; i < len(arr); i++ {
		for j := i + 1; j < len(arr); j++ {
			if arr[j-1] > arr[j] {
				temp := arr[j-1]
				arr[j-1] = arr[j]
				arr[j] = temp
			}
		}
	}
}
```

### 선택 정렬 (Selection Sort)
- 해당 순서에 원소를 넣을 위치는 이미 정해져 있고, 어떤 원소를 넣을지 선택하는 알고리즘
- 최선, 평균, 최악의 경우 시간복잡도는 O(n^2) 으로 동일
- 주어진 배열 안에서 교환(swap)을 통해, 정렬이 수행되므로 공간복잡도는 O(n)

```javascript
function selectionSort(arr){
	for(let i = 0; i < arr.length; i++){
		let index = i;
		for(let j = i + 1; j < arr.length; j++){
			if(arr[index] > arr[j]){
				index = j;
			}
		}
		const temp = arr[index];
		arr[index] = arr[i];
		arr[i] = temp;
	}
}
```

```go
func SelectionSort(arr []int) {
	for i := 0; i < len(arr); i++ {
		index := i
		for j := i + 1; j < len(arr); j++ {
			if arr[index] > arr[j] {
				index = j
			}
		}
		temp := arr[i]
		arr[i] = arr[index]
		arr[index] = temp
	}
}
```

### 삽입 정렬(Insertion Sort)
- 2번째 원소부터 시작하여 그 앞(왼쪽)의 원소들과 비교하여 삽입할 위치를 지정한 후, 원소를 뒤로 옮기고 지정된 자리에 자료를 삽입 하여 정렬하는 알고리즘
- 최선의 경우는 O(n), 평균과 최악의 경우 O(n^2) 의 시간복잡도
- 주어진 배열 안에서 교환(swap)을 통해, 정렬이 수행되므로 공간복잡도는 O(n)

```javascript
function insertionSort(arr){
	for(let i = 1; i < arr.length; i++){
		const temp = arr[i];
		let pre = i - 1;
		while(pre >= 0 && arr[pre] > temp){
			arr[pre + 1] = arr[pre];
			pre--;
		}
		arr[pre+1] = temp;
	}
}
```

```go
func InsertionSort(arr []int) {
	for i := 0; i < len(arr); i++ {
		temp := arr[i]
		pre := i - 1
		for ; pre >= 0 && arr[pre] > temp; pre-- {
			arr[pre+1] = arr[pre]
		}
		arr[pre+1] = temp
	}
}
```