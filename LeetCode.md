1.整数反转

给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。

注意：

假设我们的环境只能存储得下 32 位的有符号整数，则其数值范围为 [−231,  231 − 1]。请根据这个假设，如果反转后整数溢出那么就返回 0。

```java
class Solution {
    public int reverse(int x) {
        int rev = 0;
        while(x != 0){
            int pop = x % 10;
            x = x / 10;
            if(rev > Integer.MAX_VALUE / 10 || (rev == Integer.MAX_VALUE / 10 && pop > Integer.MAX_VALUE % 10)){
                rev = 0;
                break;
            }else if(rev < Integer.MIN_VALUE / 10 || (rev == Integer.MIN_VALUE / 10 && x < Integer.MIN_VALUE % 10)){
                rev = 0;
                break;
            }
            rev = rev * 10 + pop;
        }
        return rev;
        }
}
```



2.有效的括号（20）

给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。
注意空字符串可被认为是有效字符串。

```java
public boolean isValid(String str) {
    if (str.equals("")) return true;
    Stack<Character> stack = new Stack<>();
    for (char c : str.toCharArray()) {
        if (c == '{' || c == '[' || c == '(')
            stack.push(c);

        if (c == ')' || c == '}' || c == ']') {
            if (stack.isEmpty()) {
                return false;
            }
            Character pop = stack.pop();
            if (c == ')'&&pop != '(') return false;
            if (c == ']'&&pop != '[') return false;
            if (c == '}'&&pop != '{') return false;
        }
    }
    return stack.isEmpty();
}
```

