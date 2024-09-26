## 선택정렬

<aside>

💡삽입 정렬은 전체 원소들 중에서 기준 위치에 맞는 원소를 찾아 선택하여 교환하는 방식으로 정렬하는 것


### 수행 방법

1. 전체 원소들 중에서 가장 작은 원소를 찾아 선택하여 첫 번째 원소와 자리를 교환한다.
2. 두 번째로 작은 원소를 찾아 선택하여 두 번째 원소와 자리를 교환한다.
3. 이 과정을 반복한다. 

### 시간 복잡도

- `O(n^2)`

### 장점

- 구현이 간단하다.
- 비교 횟수에 비해 교환이 적다.

### 단점

- 시간이 오래 걸린다.
- 적응성이 부족하다.

```c
void SelectionSort(int a[], int size) {
	int i, j, t, min, temp;
	for(i = 0; i<size-1; i++) {
		min = i;
		for(j = i+1; j<size; j++) {
			if(a[j] < a[min]) min = j;
		}
		temp = a[i];
		a[i] = a[min];		
		a[min] = temp;
		printf("\n %d단계: ",i+1);
		
		for(t = 0; t<size; t++) printf("%3d",a[t]);
	}
}
```
