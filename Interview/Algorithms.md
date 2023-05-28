# 알고리즘

## 거품 정렬 (Bubble Sort)
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
		for j := 1; j < len(arr) - i; j++ {
			if arr[j-1] > arr[j] {
				temp := arr[j-1]
				arr[j-1] = arr[j]
				arr[j] = temp
			}
		}
	}
}
```

## 선택 정렬 (Selection Sort)
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

## 삽입 정렬(Insertion Sort)
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

## 퀵 정렬(Quick Sort)
- 분할 정복 알고리즘의 하나로, 평균적으로 매우 빠른 수행 속도를 자랑하는 정렬하는 알고리즘
- 평균과 최선의 경우는 O(nlogn), 최악의 경우 O(n^2) 의 시간복잡도

```javascript
function quickSort (arr) {
  if (arr.length <= 1)
  	return arr;

  const pivot = arr[0];
  const leftArray = [];
  const rightArray = [];

  for (let i = 1; i < arr.length; i++) {
    if (arr[i] <= pivot)
		leftArray.push(arr[i]);
    else
		rightArray.push(arr[i]);
  }

  const sortedLeftArray = quickSort(leftArray);
  const sortedRightArray = quickSort(rightArray);
  return [...sortedLeftArray, pivot, ...sortedRightArray];
}
```

```go
func QuickSort(arr []int) []int {
	if len(arr) <= 1{
		return arr;
	}

	pivot := arr[0]
	lowPart := make([]int, 0, len(arr))
	highPart := make([]int, 0, len(arr))
	middlePart := make([]int, 0, len(arr))

	for _, item := range arr {
		switch {
		case item < median:
			lowPart = append(lowPart, item)
		case item == median:
			middlePart = append(middlePart, item)
		case item > median:
			highPart = append(highPart, item)
		}
	}

	lowPart = quickSort(lowPart)
	highPart = quickSort(highPart)

	lowPart = append(lowPart, middlePart...)
	lowPart = append(lowPart, highPart...)

	return lowPart
}
```

## 합병 정렬(Merge Sort)
- 분할 정복 알고리즘의 하나로, 요소를 쪼갠 후, 다시 합병시키면서 정렬해나가는 방식으로 정렬하는 알고리즘
- 평균과 최선, 최악의 경우 O(nlogn)

```javascript
function mergeSort(arr){
    let left = 0, right = arr.length - 1;
    divide(arr,left,right);
}

function divide(arr, left, right){
    if(left < right){
        const mid = Math.floor((left+right)/2);
        divide(arr,left,mid);
        divide(arr,mid+1,right);
        conquer(arr,left,mid,right);
    }
}

function conquer(arr,left,mid,right){
    const LeftArray = arr.slice(left,mid+1);
    const RightArray = arr.slice(mid+1,right+1);
    let i = 0, j = 0, index = left;
    const LeftLength = LeftArray.length, RightLength = RightArray.length;

    while(i < LeftLength && j < RightLength){
        arr[index] = LeftArray[i] <= RightArray[j] ? LeftArray[i++] : RightArray[j++];
        index++;
    }
    
    while(i < LeftLength){
        arr[index++] = LeftArray[i++];
    }
    
    while(j < RightLength){
        arr[index++] = RightArray[j++];
    }
}
```

## 합병 정렬(Counting Sort)
- `범위 조건`이 있는 경우에 한해서 굉장히 빠른 알고리즘
- 시간 복잡도는 O(N)

```javascript
function countingSort (arr, min, max) {
	let answer = new Array(arr.length).fill(0);
	let matrix = new Array(max + 1).fill(min - 1);
	for(let i = 0; i < arr.length; i++)
		matrix[arr[i]]++;
	let j = 0;
	for(let i = min; i <=max; i++){
		if(matrix[i] > min - 1){
			answer[j++] = i;
			matrix[i--]--;
		}
	}
	return answer;
}
```