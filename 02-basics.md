# Excercises

## 2.1 Mileage Calculator

Write a program that calculates mileage deduction for income tax using the standar rate of $0.575 per mile. Your program will read in a beginning and ending odometer reading an calculate the diference and total deduction. Take care that your output is in whole cents. An example run of the program may look like the following.

```
INCOME TAX MILEAGE CALCULATOR

Enter beginning odometer reading--> 13505.2
Enter endingeter reading--> 13810.6
You traveled 305.4 miles. At $.575 per mile,
your reimbursement is $175.61
```

### Solution in C

```c
#include <stdio.h>

int main()
{
    float rate = 0.575;
    float miles;
    float reim;
    float initial;
    float end;
    
    printf("Enter beginning odometer reading:\n");
    scanf("%f", &initial);

    printf("Enter ending odometer reading:\n");
    scanf("%f", &end);
    
    miles = end - initial;
    reim = miles * rate;
    
    printf("You traveled %.1f miles. At $%.3f per mile,\n your reimbursement is $%.2f", miles, rate, reim);
    return 0;
}
```

