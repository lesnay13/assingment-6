# assingment-6

A menu-driven Java program that sorts a list of integers using one of four classic sorting algorithms: **Merge Sort**, **Insertion Sort**, **Shell Sort**, and **Quick Sort**. It also includes a routine that collapses duplicate values in the sorted array.

## Features

- Interactive console menu, repeating until the user quits
- Four sorting algorithms implemented from scratch (no `Arrays.sort`)
- Sorted output with duplicate removal
- Plain Java using only `java.util.Scanner`; no external dependencies

## Repository Structure

| File | Description |
| --- | --- |
| `Driver` | The whole program: `main` menu loop plus all sorting and helper methods (`public class Driver`). |

## Requirements

- Java Development Kit (JDK) 8 or newer

## Build and Run

The source file is named `Driver` with no extension. Java requires the file name to match the public class and end in `.java`, so rename it first:

```bash
mv Driver Driver.java
javac Driver.java
java Driver
```

## Usage

The program shows this menu:

```
===================================================
0. Quit 1.Merge Sort 2.Insertion Sort 3.Shell Sort 4.Quick Sort
===================================================
Select an option:
```

1. Pick a sorting algorithm (`1` to `4`).
2. Enter how many integers you want to sort.
3. Enter each integer when prompted.
4. The program sorts the numbers, removes duplicates, and prints the result.
5. The menu appears again. Enter `0` to quit.

## Algorithms

| Option | Algorithm | Method | Average time | Worst time |
| --- | --- | --- | --- | --- |
| 1 | Merge Sort | `mergeSort`, `merge` | O(n log n) | O(n log n) |
| 2 | Insertion Sort | `insertionsort` | O(n²) | O(n²) |
| 3 | Shell Sort | `shellsort` (gap starts at n/2, halves each pass) | depends on gaps | O(n²) |
| 4 | Quick Sort | `quicksort`, `Part` (last element as pivot) | O(n log n) | O(n²) |

### Helper Methods

| Method | Purpose |
| --- | --- |
| `duplicates(int[] a, int n)` | Compacts a sorted array so repeated values appear once and returns the new size. |
| `print(int[] arr, int initial, int end)` | Prints the array elements from index `initial` up to (not including) `end`. |
| `swap(int[] a, int low, int high)` | Swaps two array elements (used by Quick Sort). |

## Known Issues / Work in Progress

- **Merge Sort:** the last loop in `merge` copies indices `left` to `right - 1`, so the element at `right` is never copied back. It should loop while `i <= right`.
- **Duplicate removal:** `duplicates` is called with `num - 1` instead of the array length, and it always stores `a[n-1]` as the final element. The last element can be lost and an extra copy of another value added. The "duplicates" list printed afterward also just shows leftover array contents.
- **Input prompts:** the `count` variable that numbers the prompts is never reset between runs, so numbering keeps climbing, and the prompt has no colon or newline.
- **Invalid menu choice:** the program reads an extra integer after printing the error, which swallows the next input.
- **File name:** the source file needs to be renamed to `Driver.java` to compile.

## License

No license file is included in this repository.
