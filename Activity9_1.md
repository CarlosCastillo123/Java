# 9.1 Insertion Sort
``` java 
import java.util.*;

void insertionSort(int[] arr) {
    int j;
    int temp;
    int comparisons = 0;
    int swaps = 0;
    for (int i = 1; i < arr.length; ++i) {
        j = i;

        while (j > 0) {
            comparisons++;
            if (arr[j] < arr[j - 1]) {
                swaps++;
                temp = arr[j];
                arr[j] = arr[j - 1];
                arr[j - 1] = temp;
                --j;
            }
            else {
              break;
            }
        }
    }
    System.out.println("Comparisons made " + comparisons);
    System.out.println("Swaps " + swaps);
}

;

void main() {
    int[] array = {3, 2, 1, 5, 9, 8};

    insertionSort(array);


    System.out.println("Sorted: ");
    for (int i = 0; i < array.length; i++) {
        System.out.print(array[i] + " ");
    }
    System.out.println();
}
```
## Challanges
Making the condition for if the element is swaped increment the swap counter was difficult.
