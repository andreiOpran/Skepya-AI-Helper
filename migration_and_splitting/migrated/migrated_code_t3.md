```java
import java.util.ArrayList;
import java.util.List;

public class CombinationGenerator {

    // Part number 1 of the code: Backtracking method
    private void backtrack(List<Integer> nums, List<Integer> current, int start, List<List<Integer>> result) {
        result.add(new ArrayList<>(current)); // Add the current combination to the result

        for (int i = start; i < nums.size(); i++) {
            current.add(nums.get(i)); // Add current element to the combination
            backtrack(nums, current, i + 1, result); // Explore further with the next elements
            current.remove(current.size() - 1); // Backtrack: Remove the last element to explore other combinations
        }
    }

    // Part number 2 of the code: Combine method
    public List<List<Integer>> combine(List<Integer> nums) {
        List<List<Integer>> result = new ArrayList<>();
        List<Integer> current = new ArrayList<>();
        backtrack(nums, current, 0, result); // Start backtracking from index 0
        return result;
    }

    // Part number 3 of the code: Main method to execute the code
    public static void main(String[] args) {
        CombinationGenerator generator = new CombinationGenerator();
        List<Integer> nums = List.of(1, 2, 3); // Example input
        List<List<Integer>> combinations = generator.combine(nums);

        // Print all combinations
        System.out.println("Combinations: ");
        for (List<Integer> combo : combinations) {
            System.out.print("[ ");
            for (int num : combo) {
                System.out.print(num + " ");
            }
            System.out.println("]");
        }
    }
}
```

This Java code migrates the functionality from the original C++ code, respecting the implementation of backtracking to generate combinations. The `backtrack` method is used to explore all possible combinations recursively, and the `combine` method initiates this process. The `main` method demonstrates how to use these methods to generate and print all combinations of a given list of numbers.