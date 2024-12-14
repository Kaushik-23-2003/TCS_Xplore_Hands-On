# TCS Xplore Java Hands-On Solutions


# 1. **Find Interest Value**

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
```plaintext
2 
2 
3 
3 
-4 
-4 
```

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

# 3. **Find the Minimum Valued Character**

### Problem Statement:

Write a program that reads a String value and prints the minimum valued character based on the alphabet and ASCII sequence.

- The program should consider the **ASCII value** of the characters.
- For example, in the string `HellO`, 'H' has a lower ASCII value than 'e', so the output should be `H`.

### Sample Input:
```plaintext
HellO
```

### Expected Output:
```plaintext
H
```


### Explanation:

- In the string `"HellO"`, the characters have the following ASCII values:
  - 'H' = 72
  - 'e' = 101
  - 'l' = 108
  - 'l' = 108
  - 'O' = 79
- The minimum ASCII value is 72, corresponding to the character 'H'.


### Solution:

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Solution {
    public static void main(String args[] ) throws Exception {
        // Read input string
        String str;
        Scanner scn = new Scanner(System.in);
        str = scn.next();

        // Create an array to store ASCII values of characters
        int[] values = new int[str.length()];

        // Store ASCII values of the string characters
        for (int i = 0; i < str.length(); i++) {
            values[i] = (int)(str.charAt(i));
        }

        // Find the minimum ASCII value
        int min = values[0];
        for (int i = 0; i < values.length; i++) {
            if (values[i] <= min) {
                min = values[i];
            }
        }

        // Convert the minimum ASCII value back to a character
        char c = (char) min;
        
        // Print the character with the minimum ASCII value
        System.out.print(c);
    }
}
```
---

# 4. **Calculate Factorial of 5 Numbers**

### Problem Statement:

Write a program to read 5 numbers from the user and print the factorial of each number.

- The factorial of a non-negative integer `n` is the product of all positive integers less than or equal to `n`. It is represented as `n!`.

- **Factorial Example:**
  - `5! = 5 * 4 * 3 * 2 * 1 = 120`
  - `4! = 4 * 3 * 2 * 1 = 24`

### Sample Input:
```plaintext
2
3 
4
6
5
```


### Expected Output:
```plaintext
2
6
24
720
120
```

### Solution:

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Solution {
    public static void main(String args[] ) throws Exception {
        // Create a Scanner object to read input
        Scanner scn = new Scanner(System.in);

        // Array to store the 5 input numbers
        int[] num = new int[5];

        // Reading 5 numbers
        for (int i = 0; i < 5; i++) {
            num[i] = scn.nextInt();
            
            // Calculate and print the factorial for each number
            String res = factorial(num[i]);
            System.out.println(res);
        }
    }

    // Method to calculate factorial of a number
    public static String factorial(int n) {
        // Use BigInteger to handle large numbers
        BigInteger fact = new BigInteger("1");

        // Calculate factorial by multiplying each number from 1 to n
        for (int i = 1; i <= n; i++) {
            fact = fact.multiply(new BigInteger(i + ""));
        }
        
        // Return the factorial result as a string
        return fact.toString();
    }
}
```
---

# 5. **Find Documents with Odd Pages**

### Problem Statement:

Create a program that reads information about multiple documents and identifies those with an odd number of pages.

- Create a `Document` class with the following attributes:
  - `id` (int)
  - `title` (String)
  - `folderName` (String)
  - `pages` (int)

- The program should filter the documents that have an odd number of pages and return a list of those documents. The filtered list should be sorted by the `id` attribute in ascending order.

- Read input for 4 `Document` objects. For each document, read the `id`, `title`, `folderName`, and `pages` attributes.

- The program will display the documents with odd pages in ascending order of `id`.

### Sample Input:

| **ID** | **Title**   | **Folder Name** | **Pages** |
|--------|-------------|-----------------|-----------|
| 1      | resume      | personal        | 50        |
| 2      | question1   | exams           | 55        |
| 3      | question2   | exams           | 45        |
| 4      | India       | misc            | 40        |

### Expected Output:

| **ID** | **Title**   | **Folder Name** | **Pages** |
|--------|-------------|-----------------|-----------|
| 2      | question1   | exams           | 55        |
| 3      | question2   | exams           | 45        |

### Solution:

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Solution {
    public static void main(String args[] ) throws Exception {
        Scanner scn = new Scanner(System.in);
        Document[] docsArray = new Document[4];
        Document[] res = new Document[4];

        // Initialize Document objects
        for (int i = 0; i < docsArray.length; i++) {
            docsArray[i] = new Document();
            res[i] = new Document();
        }

        // Read input for Document objects
        for (int i = 0; i < docsArray.length; i++) {
            docsArray[i].setId(scn.nextInt());
            docsArray[i].setTitle(scn.next());
            docsArray[i].setFolderName(scn.next());
            docsArray[i].setPages(scn.nextInt());
        }

        // Filter documents with odd pages
        res = docsWithOddPages(docsArray);

        // Print filtered documents
        for (int i = 0; i < res.length; i++) {
            if (res[i].getTitle() != null) {
                System.out.println(res[i].getId() + " " + res[i].getTitle() + " " + res[i].getFolderName() + " " + res[i].getPages());
            }
        }
    }

    // Method to return documents with odd number of pages
    public static Document[] docsWithOddPages(Document[] docsArray) {
        Document[] oddDocs = new Document[4];
        int k = 0;

        // Filter documents with odd number of pages
        for (int i = 0; i < docsArray.length; i++) {
            oddDocs[i] = new Document();
            if (docsArray[i].getPages() % 2 != 0) {
                oddDocs[k++] = docsArray[i];
            }
        }

        // Sort documents by id in ascending order
        for (int i = 0; i < k - 1; i++) {
            for (int j = 0; j < k - i - 1; j++) {
                if (oddDocs[j].getId() > oddDocs[j + 1].getId()) {
                    Document temp = oddDocs[j];
                    oddDocs[j] = oddDocs[j + 1];
                    oddDocs[j + 1] = temp;
                }
            }
        }

        // Return the sorted array of odd page documents
        return Arrays.copyOfRange(oddDocs, 0, k);
    }
}

// Document class definition
class Document {
    private int id, pages;
    private String title, folderName;

    // Setters and Getters
    public void setId(int id) {
        this.id = id;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public void setFolderName(String folderName) {
        this.folderName = folderName;
    }

    public void setPages(int pages) {
        this.pages = pages;
    }

    public int getId() {
        return this.id;
    }

    public String getTitle() {
        return this.title;
    }

    public String getFolderName() {
        return this.folderName;
    }

    public int getPages() {
        return this.pages;
    }
}
```
---

# 6. **Sort Books by Price**

Create a class `Book` with the following attributes:

- `id` (int)
- `title` (String)
- `author` (String)
- `price` (double)

Write getters, setters, and a parameterized constructor for the `Book` class.

In the `Solution` class, implement the static method `sortBooksByPrice` which accepts an array of `Book` objects and returns the array sorted by the price in ascending order.

Before calling the method, use the `Scanner` object to read values for four `Book` objects.

### Sample Input:

| **ID** | **Title**  | **Author**  | **Price** |
|--------|------------|-------------|-----------|
| 1      | hello      | writer1     | 50.0      |
| 2      | cup        | writer2     | 55.0      |
| 3      | Planet     | writer3     | 45.0      |
| 4      | India      | writer4     | 40.0      |

### Sample Output:

| **ID** | **Title**  | **Author**  | **Price** |
|--------|------------|-------------|-----------|
| 4      | India      | writer4     | 40.0      |
| 3      | Planet     | writer3     | 45.0      |
| 1      | hello      | writer1     | 50.0      |
| 2      | cup        | writer2     | 55.0      |

### Solution:

```java
import java.io.*;
import java.util.*;

public class Solution {
    public static void main(String args[]) throws Exception {
        Scanner scn = new Scanner(System.in);
        Book[] booksArray = new Book[4];
        Book[] sorted = new Book[4];

        for (int i = 0; i < booksArray.length; i++) {
            booksArray[i] = new Book();
            sorted[i] = new Book();
        }

        // Reading Book details from user
        for (int i = 0; i < booksArray.length; i++) {
            booksArray[i].id = scn.nextInt();
            booksArray[i].title = scn.next();
            booksArray[i].author = scn.next();
            booksArray[i].price = scn.nextDouble();
        }

        // Sorting books by price
        sorted = sortBooksByPrice(booksArray);

        // Displaying sorted books
        for (int i = 0; i < sorted.length; i++) {
            System.out.println(sorted[i].id + " " + sorted[i].title + " " + sorted[i].author + " " + sorted[i].price);
        }
    }

    public static Book[] sortBooksByPrice(Book[] booksArray) {
        int n = booksArray.length;
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (booksArray[j].price > booksArray[j + 1].price) {
                    Book temp = booksArray[j];
                    booksArray[j] = booksArray[j + 1];
                    booksArray[j + 1] = temp;
                }
            }
        }
        return booksArray;
    }
}

class Book {
    int id;
    String title, author;
    double price;
}
```
---

# 7. **Shirt Discount, Price**

#### Problem Statement:
You are tasked with implementing methods to compute the discounted price for shirts based on gender and retrieve shirts with prices above a certain threshold, sorted in ascending order.

Create a `Shirt` class with the following attributes:
- `tag` (int)
- `brand` (String)
- `price` (double)
- `gender` (char)

Create a constructor that takes these attributes as parameters and provide getter and setter methods.

In the `Solution` class, define two static methods as described below:

1. **`getDiscountPrice(Shirt s)`**:
   This method will return the discounted price for the given `Shirt` object. The discount is applied based on the gender:
   - For 'm' (male), the discount is 10%.
   - For 'f' (female), the discount is 20%.
   - For 'u' (unisex), the discount is 30%.

2. **`getShirtWithMoreThanSpecificPrice(Shirt[] shirts, double price)`**:
   This method takes an array of `Shirt` objects and a price value. It will return an array of `Shirt` objects with prices greater than the specified value, sorted in ascending order of price.

#### Input Format:

| Tag | Brand  | Price | Gender |
|-----|--------|-------|--------|
| 1   | arrow  | 500   | m      |
| 2   | bare   | 600   | f      |
| 3   | arrow  | 400   | m      |
| 4   | bare   | 300   | m      |
| 5   | arrow  | 1000  | u      |

Price threshold: **500**

#### Sample Output:

**Discounted Prices:**

| Discounted Price |
|------------------|
| 450.0            |
| 480.0            |
| 360.0            |
| 270.0            |
| 700.0            |

**Shirts with price greater than 500:**

| Tag | Price | Brand |
|-----|-------|-------|
| 2   | 600   | bare  |
| 5   | 1000  | arrow |

### Solution:

```java
import java.util.Scanner;

public class Solution {
    public static void main(String args[]) throws Exception {
        /* Do not alter code in main method */
        Shirt[] shirts = new Shirt[5];
        Scanner sc = new Scanner(System.in);

        for(int i = 0; i < 5; i++) {
            int tag = sc.nextInt(); sc.nextLine();
            String brand = sc.nextLine();
            double price = sc.nextDouble(); sc.nextLine();
            char g = sc.nextLine().charAt(0);
            shirts[i] = new Shirt(tag, brand, price, g);
        }

        double price = sc.nextDouble();

        for(Shirt s: shirts) {
            System.out.println(getDiscountPrice(s));
        }

        Shirt[] result = getShirtWithMoreThanSpecificPrice(shirts, price);

        for(Shirt s: result) {
            if(s.tag != 0)  // Only print non-empty shirts
                System.out.println(s.tag + " " + s.price + " " + s.brand);
        }
    }

    public static Double getDiscountPrice(Shirt s) {
        char ge = s.g;
        int f = 0;
        if(ge == 'm') f = 10;
        if(ge == 'f') f = 20;
        if(ge == 'u') f = 30;

        double p = s.price;
        return p - ((p * f) / 100);
    }

    public static Shirt[] getShirtWithMoreThanSpecificPrice(Shirt[] shirts, double price) {
        Shirt[] r = new Shirt[5];
        for(int i = 0; i < r.length; i++) {
            r[i] = new Shirt(0, "", 0.0, 'f');  // Initialize with default values
        }

        int k = 0;
        for(int i = 0; i < shirts.length; i++) {
            if(shirts[i].price > price)
                r[k++] = shirts[i];
        }

        // Sort shirts by price in ascending order
        for(int i = 0; i < r.length - 1; i++) {
            for(int j = 0; j < r.length - i - 1; j++) {
                if(r[j].price > r[j + 1].price) {
                    Shirt temp = r[j];
                    r[j] = r[j + 1];
                    r[j + 1] = temp;
                }
            }
        }

        return r;
    }
}

class Shirt {
    int tag;
    String brand;
    double price;
    char g;

    // Constructor
    Shirt(int tag, String brand, double price, char g) {
        this.tag = tag;
        this.brand = brand;
        this.price = price;
        this.g = g;
    }
}
```
---


# 8. **Search Book Title**

#### Problem Statement:
Create a class `Book` with the following attributes:
- `id` (int)
- `title` (String)
- `author` (String)
- `price` (double)

Implement the following in the `Solution` class:

1. **`searchTitle(String value, Book[] books)`**:
   This method takes a `String` (search term) and an array of `Book` objects. It will return an array of books where the title contains the search term (case-insensitive).

2. The main method will:
   - Read values for four `Book` objects.
   - Read the search parameter (title search term).
   - Call `searchTitle` and display the IDs of the matching books in ascending order.

#### Input Format:

| ID  | Title             | Author       | Price |
|-----|-------------------|--------------|-------|
| 1   | hello world       | aaa writer   | 50    |
| 2   | World cup         | bbb writer   | 55    |
| 3   | Planet earth      | ccc writer   | 45    |
| 4   | India's history   | ddd writer   | 40    |

Search parameter: **WORLD**

#### Sample Output:

| ID  |
|-----|
| 1   |
| 2   |

### Solution:

```java
import java.util.Arrays;
import java.util.Scanner;

public class Solution {
    public static void main(String args[]) throws Exception {
        /* Enter your code here. Read input from STDIN. Print output to STDOUT */
        Scanner scn = new Scanner(System.in);
        Book[] booksArray = new Book[4];
        Book[] res = new Book[4];

        for (int i = 0; i < booksArray.length; i++) {
            booksArray[i] = new Book();
            res[i] = new Book();
        }

        for (int i = 0; i < 4; i++) {
            booksArray[i].id = scn.nextInt();
            scn.nextLine(); // Consume the newline character
            booksArray[i].title = scn.nextLine();
            booksArray[i].author = scn.nextLine();
            booksArray[i].price = scn.nextDouble();
        }

        String value = scn.next();
        res = searchTitle(value, booksArray);
        int[] matchedId = new int[4];
        int j = 0;
        for (int i = 0; i < res.length; i++) {
            if (res[i].id != 0) {
                matchedId[j++] = res[i].id;
            }
        }

        Arrays.sort(matchedId);
        for (int i = 0; i < matchedId.length; i++) {
            if (matchedId[i] != 0)
                System.out.println(matchedId[i]);
        }
    }

    public static Book[] searchTitle(String value, Book[] books) {
        int k = 0;
        Book[] matching = new Book[4];
        for (int i = 0; i < matching.length; i++) {
            matching[i] = new Book();
        }

        for (int i = 0; i < books.length; i++) {
            String val = value.toLowerCase();
            String bookTitle = books[i].title.toLowerCase();
            if (bookTitle.contains(val)) {
                matching[k++] = books[i];
            }
        }

        return matching;
    }
}

class Book {
    int id;
    String title;
    String author;
    double price;

    public Book() {}

    // Parameterized constructor
    public Book(int id, String title, String author, double price) {
        this.id = id;
        this.title = title;
        this.author = author;
        this.price = price;
    }

    public int getId() {
        return this.id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getTitle() {
        return this.title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getAuthor() {
        return this.author;
    }

    public void setAuthor(String author) {
        this.author = author;
    }

    public double getPrice() {
        return this.price;
    }

    public void setPrice(double price) {
        this.price = price;
    }
}
```
---
