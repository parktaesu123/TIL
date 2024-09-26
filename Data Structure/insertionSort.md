## 삽입 정렬

<aside>

💡정렬 되어있는 부분 집합에 정렬할 새로운 원소의 위치를 찾아 삽입한다.

</aside>

### 수행 방법

- **S** : 정렬된 앞부분의 원소들                 **U** : 아직 정렬되지 않은 나머지 원소들
1. U의 첫 원소를 꺼내 S의 마지막 원소와 비교한다.
2. U가 더 작으면 앞으로 가면서 비교한다.
3. U가 더 크면 위치에 삽입한다.
4. U가 비어있으면 삽입 정렬을 멈춘다.

### 시간 복잡도

- **최선 :** `O(n)`
- **최악 :** `O(n^2)`

### 장점

- 최선의 경우 `O(n)`으로 정렬이 가능하다.
- 빠른 효율성을 가지고 있다.

### 단점

- 최악의 경우 `O(n^2)`이 걸린다.
- 데이터의 크기와 상태에 따라 성능의 편차가 크다.

```c
void insertionSort(int a[], int size) {
	int i, j, t, temp;
	
	for(i = 1; i<size; i++) {
		temp = a[i];
		j = i;
		while((j>0) && (a[j-1] > temp)) {
			a[j] = a[j-1];
			j = j-1;
		}
		a[j] = temp;
		printf("\n %d단계: ",i);
		for(t = 0; t<size; t++) printf("%3d",a[t]);
	}
}
```