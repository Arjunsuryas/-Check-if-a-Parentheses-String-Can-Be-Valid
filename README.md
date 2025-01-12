# -Check-if-a-Parentheses-String-Can-Be-Valid
in_java
public class Solution {
    public boolean canBeValid(String s, String locked) {
        int n = s.length();
        if (n % 2 != 0) return false;
        int balance = 0;
        for (int i = 0; i < n; i++) {
            if (locked.charAt(i) == '1') {
                if (s.charAt(i) == '(') {
                    balance++;
                } else {
                    balance--;
                }
            } else {
                if (balance > 0) {
                    balance--;
                } else {
                    balance++; 
                }
            }
            if (balance < 0) {
                return false;
            }
        }
        balance = 0;
        for (int i = n - 1; i >= 0; i--) {
            if (locked.charAt(i) == '1') {
                if (s.charAt(i) == ')') {
                    balance++;
                } else {
                    balance--;
                }
            } else {
                if (balance > 0) {
                    balance--; 
                } else {
                    balance++; 
                }
            }
            if (balance < 0) {
                return false;
            }
        }

        return balance == 0;
    }
}
