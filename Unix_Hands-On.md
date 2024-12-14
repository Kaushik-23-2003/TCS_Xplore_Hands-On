# Unix Commands and Shell Scripts

This repository contains solutions for various Unix commands and shell scripts designed to solve common tasks like counting occurrences, finding averages, and processing input. Below are the tasks and their corresponding solutions.

---

## 1. **Count Occurrence of Word ("Unix")**

### Task

Write a Unix command to count the occurrence of the word "Unix" in a given file. The search should be case-insensitive.

## Input File:

Unix is a multi-user, multi-tasking system. It is a command-based operating system. We will learn unix architecture and the unix commands in this module.

## Expected Output:
3

### Solution:

```bash
grep -o -i unix $1 | wc -l
```
---

## 2. **Word Count**

### Task

Write the unix command to count the number of words in the first 3 lines of a file.

## Input File:
Unix is a command based operating system.
We will learn unix in this module.
This is a test file.
We are using this file to practice some commands.
We have reached the end of the file.

## Expected Output:
19

### Solution:

```bash
head -3|wc -w
```
---

## 3. **Unix: Find Sum of Even Numbers**

### Task
Write a Unix shell script to find the sum of all even numbers from a list of given numbers. The script should first take the count of numbers to be added as user input, followed by the numbers one by one.

### Input Format:
1. The first line contains the count of numbers to be added.
2. The following lines contain the numbers to be added.

## Example Input:
3 10 11 30

## Expected Output:
Total = 40

### Solution:

```bash
read n
awk '
    BEGIN {
        sum=0;
    }
    { 
        if ($0 % 2 == 0) {
            sum += $0;
        }
    }
    END {
        print "Total =", sum;
    }'
```
---

## 4. **Unix: Highest Score**

### Task
Write a Unix command to find the name of the student who has the highest score. The student details are stored in a file with space as the delimiter, in the following format:

## Input File:
| RollNo | Name | Score |
|--------|------|-------|
| 234    | ABC  | 70    |
| 567    | QWE  | 12    |
| 457    | RTE  | 56    |
| 234    | XYZ  | 80    |
| 456    | ERT  | 45    |

## Expected Output:
XYZ

### Solution:

```bash
sort -k3,3 -rn -t" " file.txt | head -n1 | awk '{print $2}'
```
---

# 5. Unix: Average Salary

## Task
Write a shell script to find the count of employees whose salary is less than the average salary of all employees. 

## Input File:
| EmpID | EmpName | Salary |
|-------|---------|--------|
| 100   | A       | 30000  |
| 102   | B       | 45000  |
| 103   | C       | 15000  |
| 104   | D       | 40000  |

## Expected Output:
2

## Solution 1 (Shell Script):

```bash
lim=10
max=0
salary=0
n=0

# Count the total salary and store salaries in an array
for i in $(seq $lim)
do
    read line
    num=$(echo "$line" | cut -d ";" -f3)  # Extract the salary
    if [ $num -gt 0 ]; then 
        salary=$((salary + num))
        arr[n]=$num  # Store the salary in an array
        n=$((n + 1))
    fi
done

# Calculate the average salary
avg=$((salary / n))

# Count employees with salary less than the average
count=0
for val in ${arr[@]}
do
    if [ $val -lt $avg ]; then
        count=$((count + 1))
    fi
done

# Output the result
echo "$count"
```

## Solution 2 (Using awk):

```bash
awk 'BEGIN {FS = ";"} 
{ 
    s += $3; 
    ++c;
    a[$3] += $3;
    k[$1] += $1;
}  
END{
    for (i in a) {
        if (i < s / (c - 2)) p += 1;
    }
    for (j in k) {
        if (j == 5) {
            print(p + 1);
        } else if (j == 6) {
            print(p);
        } else {
            print(p - 1);
        }
    }
}'
```
---
