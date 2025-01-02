//Question - Palindrome Number

// Intuition

/*

1.Negative Numbers:
A negative number can never be a palindrome because the negative sign (-) is not mirrored in the reversed number. For example, -121 reversed becomes 121-.

if (x < 0) {
    return false;
}

2.Reversing the Number:
To determine if a number is a palindrome, reverse its digits. If the reversed number is the same as the original number, it is a palindrome.

while (x != 0) {
    int lastDigit = x % 10;
    x = x / 10;
    revNum = revNum * 10 + lastDigit;
}


3. Preserve the Original Value:
The number x is modified during the reversal process. To compare the reversed number with the original, store the original number in a temporary variable (temp).
    
int temp = x;

4.Comparison:
After reversing, compare the reversed number (revNum) with the original number (temp). If they are equal, return true.

return revNum == temp;

*/

// Solution

class Solution {
    public boolean isPalindrome(int x) {
        // Step 1: Negative numbers cannot be palindromes
        if (x < 0) {
            return false; // Negative numbers fail the palindrome condition
        }

        // Step 2: Store the original number in a temporary variable
        int temp = x;

        // Step 3: Initialize a variable to hold the reversed number
        int revNum = 0;

        // Step 4: Reverse the number
        while (x != 0) {
            // Extract the last digit of the current number
            int lastDigit = x % 10;

            // Remove the last digit from the original number
            x = x / 10;

            // Add the last digit to the reversed number
            revNum = revNum * 10 + lastDigit;
        }

        // Step 5: Compare the reversed number with the original number
        return revNum == temp; // Return true if they are the same, otherwise false
    }
}


