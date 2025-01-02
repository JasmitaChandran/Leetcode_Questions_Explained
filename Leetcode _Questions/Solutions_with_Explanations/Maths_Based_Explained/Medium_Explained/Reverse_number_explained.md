# Question

<img width="1339" alt="image" src="https://github.com/user-attachments/assets/e886989f-1227-4282-a3bd-cbca10be7a00" />


# Intuition

The logic:

Ideally,to reverse a no, this code is enough :

```java
class Solution {
    public int reverse(int x) {
        int revNum = 0;
        while(x>0)
        {
            int lastdigit = x % 10;
            x = x / 10;
            revNum = revNum * 10 + lastdigit;
        }
        return revNum;
    }
}

```


But we need to add 2 more conditions:

- Handle Negative nos
- Handle overflow / underflow conditions 

```java
while(x!=0) 
```
--> to include negative digits as well while reversing the no.

the question says, 

to include a 32 bit integer, if it is bigger then a 32 bit integer, then return 0.

Range [ -2 ^ 31 to 2 ^ 31 - 1] , ie, 


Range [-2147483648, 2147483647 ]

So the reverse no should lie in this range [-2147483648, 2147483647 ], othewise it should return 0.

Now moving further, 

we have 2 conditions, first is overflow condition and second one is to manage underflow condition.

```java
//overflow
 if(revNum > Integer.MAX_VALUE/10 || (revNum == Integer.MAX_VALUE/10 && lastdigit > 7))
return 0;
```
It says to first compare the revNum is more than integer max value (214748364) deleted 7 bcoz of Integer.MAX_VALUE/10.

Or revNum is equal to integer max value (214748364) deleted 7 bcoz of Integer.MAX_VALUE/10.

Last digit should be more than 7 -> bcoz if it is more than 7, it is out of range

```java
//underflow
 if(revNum < Integer.MIN_VALUE/10 || (revNum == Integer.MIN_VALUE/10 && lastdigit < -8))
 return 0;
```

It says to first compare the revNum is less than integer min value (-214748364) deleted 8 bcoz of Integer.MIN_VALUE/10.

Or revNum is equal to integer min value (-214748364) deleted 8 bcoz of Integer.MAX_VALUE/10.

Last digit should be less than 8 -> bcoz if it is less than 8, it is out of range


Reverse no logic ->

```java
 revNum = revNum * 10 + lastdigit;
```

Suppose the number is `7789`, the steps for reversing it are as follows:

- `0 * 10 + 9 = 9`
- `9 * 10 + 8 = 98`
- `98 * 10 + 7 = 987`
- `987 * 10 + 7 = 9877`

### Breakdown:
- Initially, `revNum = 0`, so `0 * 10 + 9 = 9`
- Then, `revNum = 9`, so `9 * 10 + 8 = 98`
- Next, `revNum = 98`, so `98 * 10 + 7 = 987`
- Finally, `revNum = 987`, so `987 * 10 + 7 = 9877`

### Visual Representation:
<img width="83" alt="image" src="https://github.com/user-attachments/assets/8fca545f-25c5-4fb4-8120-db62fba80cff" />


Code Explanation Step by Step:

<img width="853" alt="image" src="https://github.com/user-attachments/assets/2fb9920f-2665-4727-bf29-11384a27604d" />
<img width="931" alt="image" src="https://github.com/user-attachments/assets/b2f45e53-5cae-4b70-b790-68d71643ef1c" />


```java
//Solution

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
