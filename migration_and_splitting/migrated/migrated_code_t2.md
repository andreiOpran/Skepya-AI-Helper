```java
import java.util.ArrayList;
import java.util.List;

public class Main {

    public static void main(String[] args) {
        performOperations();
    }

    public static int binarySearch(List<Integer> list, int target) {
        int left = 0, right = list.size() - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (list.get(mid) == target) {
                return mid;
            }
            if (list.get(mid) < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return -1;
    }

    public static List<Integer> mergeSort(List<Integer> list) {
        if (list.size() <= 1) return list;
        int mid = list.size() / 2;
        List<Integer> left = new ArrayList<>(list.subList(0, mid));
        List<Integer> right = new ArrayList<>(list.subList(mid, list.size()));

        left = mergeSort(left);
        right = mergeSort(right);

        return merge(left, right);
    }

    private static List<Integer> merge(List<Integer> left, List<Integer> right) {
        List<Integer> result = new ArrayList<>();
        int i = 0, j = 0;
        while (i < left.size() && j < right.size()) {
            if (left.get(i) <= right.get(j)) {
                result.add(left.get(i++));
            } else {
                result.add(right.get(j++));
            }
        }
        result.addAll(left.subList(i, left.size()));
        result.addAll(right.subList(j, right.size()));
        return result;
    }

    public static List<Integer> bubbleSort(List<Integer> list) {
        List<Integer> arr = new ArrayList<>(list);
        for (int i = 0; i < arr.size(); i++) {
            for (int j = 0; j < arr.size() - i - 1; j++) {
                if (arr.get(j) > arr.get(j + 1)) {
                    int temp = arr.get(j);
                    arr.set(j, arr.get(j + 1));
                    arr.set(j + 1, temp);
                }
            }
        }
        return arr;
    }

    public static double toDecimal(int binary) {
        double decimal = 0;
        int base = 1;
        while (binary > 0) {
            int lastDigit = binary % 10;
            decimal += lastDigit * base;
            base *= 2;
            binary /= 10;
        }
        return decimal;
    }

    public static int toBinary(double decimal) {
        int binary = 0, remainder, i = 1;
        while (decimal != 0) {
            remainder = (int) decimal % 2;
            binary += remainder * i;
            decimal /= 2;
            i *= 10;
        }
        return binary;
    }

    public static long factorial(int n) {
        return (n == 0) ? 1 : n * factorial(n - 1);
    }

    public static void performOperations() {
        int num1 = 10, num2 = 5;

        List<Integer> sortedList1 = mergeSort(List.of(num1, num2));
        List<Integer> sortedList2 = bubbleSort(List.of(num1, num2));

        double decimal1 = toDecimal(num1);
        double decimal2 = toDecimal(num2);

        int binary1 = toBinary(decimal1);
        int binary2 = toBinary(decimal2);

        int sum = binary1 + binary2;

        long factorialResult = factorial(binary1) + factorial(binary2);

        System.out.println("Binary Search Result (find 5 in sorted list): " + binarySearch(sortedList1, 5));
        System.out.print("Sorted List (Merge Sort): ");
        sortedList1.forEach(n -> System.out.print(n + " "));
        System.out.println();

        System.out.print("Sorted List (Bubble Sort): ");
        sortedList2.forEach(n -> System.out.print(n + " "));
        System.out.println();

        System.out.println("Decimal of " + num1 + ": " + decimal1);
        System.out.println("Decimal of " + num2 + ": " + decimal2);
        System.out.println("Binary of " + num1 + ": " + binary1);
        System.out.println("Binary of " + num2 + ": " + binary2);
        System.out.println("Sum of binary numbers: " + sum);
        System.out.println("Factorial of binary 1: " + factorial(binary1));
        System.out.println("Factorial of binary 2: " + factorial(binary2));
        System.out.println("Sum of factorials: " + factorialResult);
    }
}
```