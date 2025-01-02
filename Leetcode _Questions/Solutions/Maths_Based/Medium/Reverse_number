
class Solution {
    public int reverse(int x) {
        // Step 1: Initialize the reversed number to 0
        int revNum = 0;

        // Step 2: Loop to reverse digits until the number becomes 0
        while (x != 0) {
            // Extract the last digit of the current number
            int lastDigit = x % 10;

            // Step 3: Check for overflow condition
            if (revNum > Integer.MAX_VALUE / 10 || 
                (revNum == Integer.MAX_VALUE / 10 && lastDigit > 7)) {
                return 0; // Return 0 if the number overflows
            }

            // Step 4: Check for underflow condition
            if (revNum < Integer.MIN_VALUE / 10 || 
                (revNum == Integer.MIN_VALUE / 10 && lastDigit < -8)) {
                return 0; // Return 0 if the number underflows
            }

            // Step 5: Append the last digit to the reversed number
            revNum = revNum * 10 + lastDigit;

            // Remove the last digit from the original number
            x = x / 10;
        }

        // Step 6: Return the reversed number
        return revNum;
    }
}