# TCS Xplore Java Hands-On Solutions


## 1. **Find Interest Value**

### Problem Statement:

Create a class `Account` with the following attributes:
- `int id`
- `double balance`
- `double interestRate`

The class should have getters, setters, and a constructor with parameters in the sequence of attributes above.

Create a class `Solution` with the `main` method. Read one integer and two double values using the `Scanner` object and create an object of the `Account` class. These values should be mapped to the `id`, `balance`, and `interestRate` attributes.

Read one more integer value and store it in the variable `noOfYears`.

Write a method `calculateInterest` which will take the `Account` object and `noOfYears` as input parameters and return the interest amount.

**Interest Calculation Logic:**

1. For the specified number of years, first find out the percentage value for those years based on the specified `interestRate`. 
2. Example: If the number of years is `5` and the interest rate is `10%`, then `10% of 5` is `0.5`. 
3. Add this percentage to the original interest rate. 
   - For example, the new interest rate becomes `10.5%`.

Finally, calculate the interest amount by multiplying the balance with the updated interest rate.

**Input Example:**
```plaintext
1 
1000 
10 
5
```

**Expected Output:**
```plaintext
105.000
```

### Solution:

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Solution {
    public static void main(String args[]) throws Exception {
        int a;
        double b, c;
        Scanner sc = new Scanner(System.in);
        a = sc.nextInt();
        b = sc.nextDouble();
        c = sc.nextDouble();
        Account account = new Account(a, b, c);
        int noOfYear = sc.nextInt();
        double answer = calculateInterest(account, noOfYear);
        System.out.format("%.3f", answer);
    }

    public static double calculateInterest(Account account, int noOfYear) {
        double temp = noOfYear * account.getInterestRate() / 100;
        return (account.getBalance() * (account.getInterestRate() + temp) / 100);
    }
}

class Account {
    private int id;
    private double balance;
    private double interestRate;

    Account(int id, double balance, double interestRate) {
        this.id = id;
        this.balance = balance;
        this.interestRate = interestRate;
    }

    public int getId() {
        return this.id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public double getBalance() {
        return this.balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }

    public double getInterestRate() {
        return this.interestRate;
    }

    public void setInterestRate(double interestRate) {
        this.interestRate = interestRate;
    }
}
```
---

# 2. **Compare 2D Points for Distance from Origin**

### Problem Statement:

Write a program to check the distance of 2D points from the origin and print the point with the highest distance.

- **Class Point** should have the attributes:
  - `double x`
  - `double y`

- **In Solution class**, define the `main` method to read values for three `Point` objects.

- Define the method `pointWithHighestOriginDistance(Point p1, Point p2, Point p3)` in the `Solution` class which takes three point objects as input parameters and returns the point with the highest distance from the origin.

### Sample Input:
<pre>
2 
2 
3 
3 
-4 
-4 
</pre>

### Expected Output:
```plaintext
-4.0
-4.0
```
This output indicates that the point with the highest distance from the origin is `(-4.0, -4.0)`.

### Solution:

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Solution {
    public static void main(String args[] ) throws Exception {
        // Read input for 3 points
        double x1, y1, x2, y2, x3, y3;
        Scanner scn = new Scanner(System.in);
        
        // Reading the coordinates for the three points
        x1 = scn.nextDouble();
        y1 = scn.nextDouble();
        x2 = scn.nextDouble();
        y2 = scn.nextDouble();
        x3 = scn.nextDouble();
        y3 = scn.nextDouble();
        
        // Creating Point objects
        Point p1 = new Point(x1, y1);
        Point p2 = new Point(x2, y2);
        Point p3 = new Point(x3, y3);
        
        // Find the point with the highest distance from the origin
        Point highest = pointWithHighestOriginDistance(p1, p2, p3);
        
        // Output the point with the highest distance
        System.out.format("%.1f \n", highest.x);
        System.out.format("%.1f", highest.y);
    }
    
    // Method to calculate and compare distances from the origin
    public static Point pointWithHighestOriginDistance(Point p1, Point p2, Point p3) {
        // Calculate the distance from the origin for each point
        double d1 = Math.sqrt(p1.x * p1.x + p1.y * p1.y);
        double d2 = Math.sqrt(p2.x * p2.x + p2.y * p2.y);
        double d3 = Math.sqrt(p3.x * p3.x + p3.y * p3.y);
        
        // Return the point with the highest distance
        return d1 > d2 ? (d1 > d3 ? p1 : p3) : (d2 > d3 ? p2 : p3);
    }
}

// Point class to represent a point in 2D space
class Point {
    double x, y;
    
    // Constructor to initialize point coordinates
    Point(double x, double y) {
        this.x = x;
        this.y = y;
    }
}
```
---
