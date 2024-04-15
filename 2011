import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.util.Stack;

public class GroupingSymbolChecker {
    public static void main(String[] args) {
        if (args.length != 1) {
            System.out.println("Usage: java GroupingSymbolChecker <filename>");
            return;
        }
        
        String filename = args[0];
        try (BufferedReader reader = new BufferedReader(new FileReader(filename))) {
            String line;
            int lineNumber = 0;
            Stack<Character> stack = new Stack<>();
            while ((line = reader.readLine()) != null) {
                lineNumber++;
                for (char c : line.toCharArray()) {
                    if (c == '(' || c == '{' || c == '[') {
                        stack.push(c);
                    } else if (c == ')' || c == '}' || c == ']') {
                        if (stack.isEmpty() || !isMatchingPair(stack.pop(), c)) {
                            System.out.println("Error" + lineNumber);
                            return;
                        }
                    }
                }
            }
            if (!stack.isEmpty()) {
                System.out.println("Error");
            } else {
                System.out.println("All grouping symbols are correct.");
            }
        } catch (IOException e) {
            System.out.println("Error reading file: " + e.getMessage());
        }
    }

    private static boolean isMatchingPair(char left, char right) {
        return (left == '(' && right == ')') ||
               (left == '{' && right == '}') ||
               (left == '[' && right == ']');
    }
}
