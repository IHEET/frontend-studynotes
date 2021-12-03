## 插入排序


### 直接插入排序
<strong>基本思想：</strong>将一个待排序的数与前面已经排好的有序列进行比较，插入到合适的位置形成新的长度增1的有序列。（对于少量元素的排序，它是一个有效的算法。）

<strong>性能：</strong>

- 最好时间复杂度：O(n)。当数组刚好是完全顺序时，每次只用比较一次就能找到正确的位置；这个过程重复 n 次，就可以清空未排序区间。

- 最坏时间复杂度：O(n^2)。当数组刚好是完全逆序时，每次都要比较 n 次才能找到正确位置；这个过程重复 n 次，就可以清空未排序区间。

- 平均时间复杂度：O(n^2)。往数组中插入一个元素的平均时间复杂度为 O(n)，而插入排序可以理解为重复 n 次的数组插入操作。

- 空间复杂度：O(1)。不需要开辟额外的空间。

- 稳定性：元素相同时不做交换，是稳定的排序算法。


假设前面n-1(n>=2)个数是已经排好序的，将第n个数插入到前面的有序列表中，使得插入第n个数后的序列也是排好序的。按照此法对所有元素进行插入，直到整个序列排为有序的过程，称为插入排序。


```
    // 插入算法：
    function insertionSort(arr){
        for (let i = 1, len = arr.length; i < len; i++) {
            var curr = arr[i], j = i-1;
            for (; j >= 0 && curr < arr[j]; j--) {
                arr[j+1] = arr[j];
            }
            arr[j+1] = curr;
        }
        return arr;
    }
```


### 希尔排序（又称缩小增量排序）
基本思想：首次通过增量gap=length/2进行分组，每组使用直接插入排序法进行排序，再缩小增量gap=gap/2直到增量为1，做最后一次分组插入排序算法便终止。（用于较少量元素的排序，是对直接插入排序的改良版）

平均时间复杂度也是 O(n^(1.3-2))，空间复杂度为常数阶 O(1)

```
    // 希尔排序
    function shell(arr) {
        var len = arr.length;
        let j;
        for (let gap = Math.floor(len/2); gap > 0; gap=Math.floor(gap/2)) {
            for (let i = gap; i < len; i++) {
                var curr = arr[i];
                for (j = i-gap; j >= 0 && curr < arr[j]; j-=gap) {
                    arr[j+gap] = arr[j]
                }
                arr[j+gap] = curr;
            }
        }
        return arr;
    }
```