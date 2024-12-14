# Unix Commands and Shell Scripts

This repository contains solutions for various Unix commands and shell scripts designed to solve common tasks like counting occurrences, finding averages, and processing input. Below are the tasks and their corresponding solutions.

---

## 1. **Count Occurrence of Word ("Unix")**

### Task

Write a Unix command to count the occurrence of the word "Unix" in a given file. The search should be case-insensitive.

#### Example

**Input File:**

Unix is a multi-user, multi-tasking system. It is a command-based operating system. We will learn unix architecture and the unix commands in this module.

**Expected Output:**

3

### Solution:

```bash
grep -o -i unix $1 | wc -l
```
---

## 2. **Word Count**

### Task

Write the unix command to count the number of words in the first 3 lines of a file.

#### Example

**Input File:**

Unix is a command based operating system.
We will learn unix in this module.
This is a test file.
We are using this file to practice some commands.
We have reached the end of the file.

**Expected Output:**

19

### Solution:

```bash
head -3|wc -w
```
---

## 3. **Unix: Find sum of even numbers**

### Task

Write a Unix command to count the occurrence of the word "Unix" in a given file. The search should be case-insensitive. Write a shell script to find the sum of all even numbers from a list of given numbers. The script should first of all take the count of numbers to be added as user input followed by the numbers one by one.

#### Example

**Expected Output:**
Total = <Sum>
Console Input:
The input needs to be provided as -
The first line contains the count of numbers to be added.
The second line contains the 1st number to be added.
The third line contains the 2nd number to be added. and so on.

**Input File:**
if we want to provide 10, 20 and 30 as the numbers then provide the input as
3
10
11
30

The output for this  example will be 
Total = 40

### Solution:

```bash
 read n
 awk '
     BEGIN {
         sum=0;
         }
      { if ( $0%2==0 ){
          sum+=$0;
       }
       }
      END { print "Total","=",sum}'
```
---

## 4. **Unix: Highest Score**

### Task

Student details are stored in a file in the following order with space as the delimiter:
RollNo Name Score. Write a unix command to find the name of the Student who has the highest score.

#### Example

**Input File:**

RollNo     Name       Score
234        ABC         70
567        QWE         12
457        RTE         56
234        XYZ         80
456        ERT         45

**Expected Output:**

XYZ

### Solution:

```bash
sort -k3,3 -rn -t" " | head -n1 | awk '{print $2}'
```
---


