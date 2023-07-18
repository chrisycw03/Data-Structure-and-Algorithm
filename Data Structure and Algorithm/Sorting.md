# Insertion Sort 插入排序

- 以下為直接插入排序，其他插入排序還有：折半插入排序、希爾排序
- 時間複雜度 O(n^2)
- 空間複雜度 O(1)

```c
void InsertionSort(int* arr, int size){
	for(int i = 1; i < size; i++){
		int key = arr[i];
		int j = i - 1;
		while(key < arr[j] && key >= 0){
			arr[j + 1] = arr[j];
			j--;
		}
	arr[j + 1] = key;
	}
}	
```

# Bubble Sort 泡沫排序

- 時間複雜度 O(n^2)
- 空間複雜度 O(1)

```c
void BubbleSort(int* arr, int size){
	for(int i = 0; i < size - 1; i++){
		for(int j = 1; j < size - i; j++){
			if(arr[j] < arr[j-1]){
				int temp = arr[j];
				arr[j] = arr[j-1];
				arr[j-1] = temp;
			}
		}
	}
}
```

# Quick Sort 快速排序

- 時間複雜度 O(n log n)

```c
int Partition(int* arr, int low, int high){
	int temp = arr[low];
	while(low < high){
		while(low < high && arr[high] >= temp){
			high--;
		}
		arr[low] = arr[high];
		while(low < high && arr[low] <= temp){
			low++;
		}
		arr[high] = arr[low];
	}
	arr[low] = temp;
	
	return low;
}

void QuickSort(int* arr, int low, int high){
	if(low >= high) return;
	int pivot = Partition(arr, low, high);
	QuickSort(arr, low, pivot - 1);
	QuickSort(arr, pivot + 1, high);
}
```

# Selection Sort

- 時間複雜度 O(n^2)
- 空間複雜度 O(1)

```c
void SelectionSort(int* arr, int size){
	int min_location = 0;
	for(int i = 0; i < size - 1; i++){
		for(int j = i; j < size - i; j++){
			if(arr[j] < arr[min_location]){
				min_location = j;
			}
		}
	int temp = arr[i];
	arr[i] = arr[min_location];
	arr[min_location] = temp;
	}
}				
```

# Heap Sort 堆積排序

- 時間複雜度 O(n log n)
- 空間複雜度 O(1)

```c
void Heapify(int* arr, int root, int size){
	temp = arr[root];
	int i = 1;

	while(i <= size - 1){
		if(i < size - 1 && arr[i + 1] > arr[i]){
			i++;
		}
		if(temp > arr[i]){
			break;
		}
		arr[root] = arr[i];
		root = i;
		i = i * 2 + 1;
	}
	arr[root] = temp;
}

void HeapSort(int* arr, int size){
	for(int i = size / 2 - 1; i >= 0; i--){
		Heapify(arr, i, size);
	}
	int temp;
	for(int i = size - 1; i >= 0; i--){
		temp = arr[0];
		arr[0] = arr[i];
		arr[i] = temp;
		Heapify(arr, 0, i);
	}
}
```

# Merge Sort 合併排序

- 時間複雜度 O(n log n)
- 空間複雜度 O(n)

```c
void Merge(int* arr, int begin, int mid, int end){
    // 將begin到end的元素合併為一個有序的陣列
    int size = end - begin + 1;
    int begin_l = begin;
    int begin_r = mid + 1;
    int *temp = (int*)calloc(size, sizeof(int));
    int i = 0;
    while(begin_l <= mid && begin_r <= end){
        // 依序比較左右半邊的元素，最小的元素存入temp中
        if(arr[begin_l] < arr[begin_r]){
            temp[i++] = arr[begin_l++];
        }else{
            temp[i++] = arr[begin_r++];
        }
    }
    
    // 當其中一邊的元素已經完全存入temp中，把另一邊剩餘的元素也存入temp
    while(begin_l <= mid){
        temp[i++] = arr[begin_l++];
    }
    while(begin_r <= end){
        temp[i++] = arr[begin_r++];
    }
    
    int j = 0;
    for(i = begin; i <= end; i++){
        arr[i] = temp[j++];
    }
}

void MergeSort(int* arr, int begin, int end){
    // divide and conquer
    if(begin >= end)
        return;
    int mid = (begin + end) / 2;
    MergeSort(arr, begin, mid); // 對左半邊子陣列進行合併排序
    MergeSort(arr, mid + 1, end); // 對右半邊子陣列進行合併排序
    Merge(arr, begin, mid, end); // 將左半邊和右半邊子陣列和併
}
```