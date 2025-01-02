
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


