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

## 2.2 Total Cost of Loan

Write a program to compute the total “cost” C of a loan. That is, the
total amount of interest paid over the life of a loan. To compute this value, use the
following formula.

```
  p·i·(1+i)^12n
C=_____________∗12n−p
  (1+i)^12n − 1
```

- p is the starting principle amount
- i = r/12 where r is the APR on the interval [0,1]
- n is the number of years the loan is to be paid back

### Solution in C

```c
#include <stdio.h>
#include <math.h>

int main()
{
    double totalCost(int p,float APR, int n)
    {
        double i = APR / 12;
        double exponent = pow((1+i), (12 * n));
        
        double dividend = p * i * exponent;
        double divisor = exponent - 1;

        double result = (dividend / divisor * ( (12 * n))) - p;
        
        return result;
    }

    printf("%f", totalCost(1000, 0.1, 1));

    return 0;
}
```

## 2.3 Annualized Appreciation of An Asset

Write a program to compute the annualized appreciation of an asset (say a house). The program should read in a purchase price *p*, a sale price *s* and
compute their difference *d* = *s* - *p* (it should support a loss or gain). Then, it should compute an appreciation rate: *r* = *d* / *p* along with an (average)
annualized appreciation rate (that is what was the appreciation rate in each year that the asset was held that compunded):

```
(1 + r)^1/y - 1
```

Where y is the number of years (possibly fractional) the asset was held (and r is on the scale [0, 1]).

### Solution in C

```c
#include <stdio.h>
#include <math.h>

int main()
{
    
    float purchase_price;
    float sale_price;
    float months;
    float years;
    
    float price_diff;
    float appreciation_rate;
    
    float calc_price_diff(float p, float s)
    {
        float d;
        d = s - p;
        return d;
    }
    
    float calc_appreciation_rate(float d, float p)
    {
        float r;
        r = (d / p);
        return r;
    }
    
    float calc_ann_appreciation_rate(float r, float y) 
    {
        return (pow((1 + r), (1 / y))) - 1;
    }
    
    printf("Type the purchase price: \n");
    scanf("%f", &purchase_price);
    
    printf("Type the sale price: \n");
    scanf("%f", &sale_price);
    
    printf("Type months that you held the asset: \n");
    scanf("%f", &months);
    
    years = months / 12 ;
    price_diff = calc_price_diff(purchase_price, sale_price);
    appreciation_rate = calc_appreciation_rate(price_diff, purchase_price);
    

    printf("==============\n");
    printf("You bought your asset at $%.2f and you sold it at $%.2f. The price difference was to $%.2f in %.0f months.\n", purchase_price, sale_price, price_diff, months);
    printf("==============\n");
    printf("Appreciation Rate: %.2f.\n", appreciation_rate);
    printf("==============\n");
    printf("Annual appreciation rate: %.2f\n", calc_ann_appreciation_rate(appreciation_rate, years));

    return 0;
}
```
