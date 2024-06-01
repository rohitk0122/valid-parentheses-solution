class Solution {
    public boolean isValid(String s) {
        if (s == null || s.length() % 2 != 0) {
            return false;
        }

        Stack<Character> stack = new Stack<>();
        char[] arr = s.toCharArray();

        for (char ch : arr) {
            if (stack.isEmpty()) {
                stack.push(ch);
            } else {
                char top = stack.peek();
                if ((ch == ')' && top == '(') || 
                    (ch == ']' && top == '[') || 
                    (ch == '}' && top == '{')) {
                    stack.pop();
                } else {
                    stack.push(ch);
                }
            }
        }

        return stack.isEmpty();
    }
}
