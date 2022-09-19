# Shell Sort

### Code
```c++
int shell_sort(int *data, int length)
{

    int gap = 0;
    int i = 0, j = 0;

    for (gap = length / 2; gap >= 1; gap /= 2)
    {
        for (i = gap; i < length; i++)
        {

            int temp = data[i];

            for (j = i - gap; j >= 0 && temp < data[j]; j = j - gap)
            {
                data[j + gap] = data[j];
            }

            data[j + gap] = temp;
        }
    }
}
```

### Three loops

Shell sort contains three nested loops.
The outermost loop determines the number of grouping, essentially determined by step size.
```c
for (gap = length / 2; gap >= 1; gap /= 2)
```

The middle loop is used to find each group. Essentially, it is a traversal search.
```c
for (i = gap; i < length; i++)
```

The innermost loop is used to exchange sort within each group, and the exchange condition ```temp < data[j]``` is built into the circular judgment condition.
```c 
for (j = i - gap; j >= 0 && temp < data[j]; j = j - gap)
```

### Variables
+ `gap` to record step length. Initial step length is determined by `length` 
*Note that the judgment condition of `gap` cannot be ">0", must ">=1"*
  
+ `i` Traverse through "+=1" to each group

+ `j` Traverse forward through "-=gap" to each element in the group

+ `temp`  Store temporary data

### Test
#### Input
```c
int arr[12] = {11, 8, 4, 6, 2, 5, 12, 1, 7, 9, 3, 10};

shell_sort(arr, 12);

std::cout << arr << std::endl;
```
#### Output
```c
1 2 3 4 5 6 7 8 9 10 11 12
```
