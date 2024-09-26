## 버블 정렬

<aside>

💡인접한 두 개의 원소를 비교하여 자리를 교환하는 방식

</aside>

### 수행 방법

1. 첫 번째 원소부터 마지막 원소까지 반복하여 한 단계가 끝나면 가장 큰 원소가 맨 마지막으로 감
2. 첫 번째 원소부터 인접한 원소까지 비교하여 자리를 교환하면서 정렬한다.

### 시간복잡도

- `O(n^2)`

### 장점

- 구현이 쉽다.
- 직관적이다.

### 단점

- 시간이 오래 걸린다.
- 비교 횟수가 많다.

```c
void bubbleSort(int a[], int size) {
	int i, j, t, temp;
	for(i = size-1; i>0; i--) {
		printf("\n %d단계>> ",size - i);
		for(j = 0; j<i; j++) {
			if(a[j] > a[j+1]) {
				temp = a[j];
				a[j] = a[j+1];
				a[j+1] = temp;
			}
		printf("\n\t");
		for(t = 0; t<size; t++) printf("%3d",a[t]); 	
		}
	}
}
```
