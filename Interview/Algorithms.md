## 알고리즘

### 거품 정렬 (Bubble Sort)
- 서로 인접한 두 원소의 대소를 비교하고, 조건에 맞지 않다면 자리를 교환하며 정렬하는 알고리즘
- 최선, 평균, 최악의 경우 모두 시간복잡도가 O(n^2) 으로 동일
- 주어진 배열 안에서 교환(swap)을 통해, 정렬이 수행되므로 O(n)

```javascript
function bubbleSort(arr) {
    let temp = 0;
	for(let i = 0; i < arr.length; i++) {
		for(let j= 1 ; j < arr.length-i; j++) {
			if(arr[j-1] > arr[j]) {
				temp = arr[j-1];
				arr[j-1] = arr[j];
				arr[j] = temp;
			}
		}
	}
}
```