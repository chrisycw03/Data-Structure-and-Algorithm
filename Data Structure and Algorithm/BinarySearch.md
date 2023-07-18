# Binary Search

- 時間複雜度：O(log n)
- 空間複雜度：O(1)

```c
int BinarySearch(int* a, int size, int key){
	int low = 0;
	int high = size - 1;
	while(low <= high){
		int mid = (low + high) / 2;
		if(key == a[mid]) return mid;
		if(key > a[mid]) low = mid + 1;
		if(key < a[mid]) high = mid - 1;
	}
	return -1;
}
```