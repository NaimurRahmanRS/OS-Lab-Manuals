# Bash Scripting Guide & Reference

A comprehensive, corrected, and well-structured guide to Bash scripting. This README covers fundamental concepts, syntax, control structures, and practical example scripts with their respective expected terminal outputs.

---

## Table of Contents
1. [Introduction & Fundamentals](#1-introduction--fundamentals)
2. [Variables & Data Handling](#2-variables--data-handling)
3. [Arithmetic Operations](#3-arithmetic-operations)
4. [User Input & Output](#4-user-input--output)
5. [Conditional Statements & Operators](#5-conditional-statements--operators)
6. [Loops & Control Flow](#6-loops--control-flow)
7. [Practical Script Examples](#7-practical-script-examples)

---

## 1. Introduction & Fundamentals

### What is a Shell Script?
A shell script is a plain text file containing a sequential list of shell commands executed as an automated program by a Unix-like operating system interpreter.

### The Shebang (`#!/bin/bash`)
The first line of any Bash script must be the **shebang**:
```bash
#!/bin/bash
```
* **Purpose:** Instructs the operating system which command interpreter (e.g., `/bin/bash`) to use to execute the script.
* **Importance:** Omission can lead to execution errors or unexpected behavior if run under a different default shell (such as `/bin/sh` or `/bin/zsh`).

### Creating and Running a Script
1. **Create a file:**
   ```bash
   touch script.sh
   ```
2. **Grant execution permissions (run once):**
   ```bash
   chmod +x script.sh
   ```
3. **Execute the script:**
   ```bash
   ./script.sh
   ```

---

## 2. Variables & Data Handling

### Declaring Variables
> **Note:** Linux shell scripting is case-sensitive and strictly space-sensitive. There must be **no spaces** on either side of the `=` assignment operator.

```bash
username="Alice"
age=25
```

By default, Bash treats variable values as text strings.

### Printing Variables
To access the value of a variable, prefix its name with `$`:
```bash
username="Alice"
age=25

echo "My name is $username"
echo "My age is $age"
```
**Output:**
```text
My name is Alice
My age is 25
```

### Variable Concatenation
Use curly braces `${var}` to unambiguously delimit variable names when appending text:
```bash
word="apple"
echo "I ate 3 ${word}s"
```
**Output:**
```text
I ate 3 apples
```

### String Length
To calculate the length of a string, use `${#var_name}` syntax:
```bash
text="Hello World!"
length=${#text}
echo "String Length: $length"
```
**Output:**
```text
String Length: 12
```

### Storing Command Output in Variables
Use command substitution `$(command)` to capture the output of OS commands:
```bash
dir=$(pwd)
echo "Current directory: $dir"
echo "Inline output: $(pwd)"
```
**Output:**
```text
Current directory: /home/seu/Desktop
Inline output: /home/seu/Desktop
```

---

## 3. Arithmetic Operations

Bash natively supports **integer arithmetic**. Decimal/floating-point values are truncated.

### Basic Arithmetic Syntax
```bash
num1=10
num2=3

sum=$(( num1 + num2 ))
dif=$(( num1 - num2 ))
mul=$(( num1 * num2 ))
div=$(( num1 / num2 ))
remainder=$(( num1 % num2 ))

echo "sum: $sum"
echo "dif: $dif"
echo "mul: $mul"
echo "div: $div"
echo "remainder: $remainder"
```
**Output:**
```text
sum: 13
dif: 7
mul: 30
div: 3
remainder: 1
```

### Increment and Decrement Operators
```bash
count=0

(( count++ ))
echo "count: $count"

(( count-- ))
echo "count: $count"

(( count += 5 ))
echo "count: $count"

x=$(( count++ ))
echo "count: $count"
echo "x: $x"

y=$(( ++count ))
echo "count: $count"
echo "y: $y"
```
**Output:**
```text
count: 1
count: 0
count: 5
count: 6
x: 5
count: 7
y: 7
```

---

## 4. User Input & Output

### Printing Output
Use `echo` to print text or variable values to standard output:
```bash
echo "Hello World!"
```
**Output:**
```text
Hello World!
```

### Reading Input
Use the `read` command to capture standard input from the user:
```bash
read username
echo "Hello, $username"
```
**Terminal Interaction:**
```text
Batman
Hello, Batman
```

Use the `-p` prompt flag to display a prompt message before reading input:
```bash
read -p "Enter name: " name
echo "Welcome, $name!"
```
**Terminal Interaction:**
```text
Enter name: Batman
Welcome, Batman!
```

---

## 5. Conditional Statements & Operators

### Comparison Operators

#### String Comparison
| Operator | Description | Example |
| :--- | :--- | :--- |
| `==` | Equality | `[[ "$a" == "$b" ]]` |
| `!=` | Inequality | `[[ "$a" != "$b" ]]` |
| `-z` | String is empty (zero length) | `[[ -z "$a" ]]` |
| `-n` | String is non-empty (not zero) | `[[ -n "$a" ]]` |

#### Integer Comparison
| Operator | Flag | Description | Example |
| :--- | :--- | :--- | :--- |
| `=` | `-eq` | Equal to | `[[ "$a" -eq "$b" ]]` |
| `!=` | `-ne` | Not equal to | `[[ "$a" -ne "$b" ]]` |
| `>` | `-gt` | Greater than | `[[ "$a" -gt "$b" ]]` |
| `>=` | `-ge` | Greater than or equal to | `[[ "$a" -ge "$b" ]]` |
| `<` | `-lt` | Less than | `[[ "$a" -lt "$b" ]]` |
| `<=` | `-le` | Less than or equal to | `[[ "$a" -le "$b" ]]` |

### Conditional Structure Syntax

#### If - Elif - Else
```bash
if [[ condition1 ]]
then
    # execute commands
elif [[ condition2 ]]
then
    # execute commands
else
    # default commands
fi
```

#### Logical Operators
* **AND (`&&`):** Executes if both conditions are true.
  ```bash
  if [[ condition1 ]] && [[ condition2 ]]; then ... fi
  ```
* **OR (`||`):** Executes if either condition is true.
  ```bash
  if [[ condition1 ]] || [[ condition2 ]]; then ... fi
  ```
* **NOT (`!`):** Executes if the condition is false.
  ```bash
  if [[ ! condition ]]; then ... fi
  ```

---

## 6. Loops & Control Flow

### C-Style For Loop

#### Printing 1 to 10:
```bash
for (( i=1; i<=10; i++ ))
do
    echo "$i"
done
```
**Output:**
```text
1
2
3
4
5
6
7
8
9
10
```

#### Summing 1 to 10:
```bash
sum=0
for (( i=1; i<=10; i++ ))
do
    sum=$(( sum + i ))
done
echo "sum: $sum"
```
**Output:**
```text
sum: 55
```

### While Loop

#### Printing 1 to 10 using While Loop:
```bash
i=1
while [ $i -le 10 ]
do
    echo "$i"
    (( i++ ))
done
```
**Output:**
```text
1
2
3
4
5
6
7
8
9
10
```

#### Summing 1 to 10 using While Loop:
```bash
sum=0
i=1
while [ $i -le 10 ]
do
    sum=$(( sum + i ))
    (( i++ ))
done
echo "sum: $sum"
```
**Output:**
```text
sum: 55
```

### For-In Loops & Range Expansion

#### Iterating Over Explicit Items:
```bash
for x in a b c
do
    echo "$x"
done
```
**Output:**
```text
a
b
c
```

#### Iterating Over Numerical Ranges:
```bash
for x in {1..10}
do
    echo "$x"
done
```
**Output:**
```text
1
2
3
4
5
6
7
8
9
10
```

#### Range with Step Size:
```bash
for x in {1..10..2}
do
    echo "$x"
done
```
**Output:**
```text
1
3
5
7
9
```

### Loop Control: `break` and `continue`

#### Using `break`:
```bash
for x in {1..10..2}
do
    if [[ $x -eq 7 ]]; then
        break
    fi
    echo "$x"
done
```
**Output:**
```text
1
3
5
```

#### Using `continue`:
```bash
for x in {1..10..2}
do
    if [[ $x -eq 3 ]]; then
        continue
    fi
    echo "$x"
done
```
**Output:**
```text
1
5
7
9
```

---

## 7. Practical Script Examples

### Script 1: Check Even or Odd Number
```bash
#!/bin/bash
read -p "Enter Number: " n

if [[ $(( n % 2 )) -eq 0 ]]
then
    echo "Even"
else
    echo "Odd"
fi
```
**Terminal Output (Sample 1):**
```text
Enter Number: 5
Odd
```
**Terminal Output (Sample 2):**
```text
Enter Number: 6
Even
```

### Script 2: Find Maximum of Three Numbers
```bash
#!/bin/bash
read -p "Enter Number 1: " n1
read -p "Enter Number 2: " n2
read -p "Enter Number 3: " n3

if [[ $n1 -ge $n2 ]]
then
    if [[ $n1 -ge $n3 ]]
    then
        echo "$n1 is max"
    else
        echo "$n3 is max"
    fi
else
    if [[ $n2 -ge $n3 ]]
    then
        echo "$n2 is max"
    else
        echo "$n3 is max"
    fi
fi
```
**Terminal Output:**
```text
Enter Number 1: 5
Enter Number 2: 1
Enter Number 3: 9
9 is max
```

### Script 3: Count Multiples of 5 (from 1 to 50)
```bash
#!/bin/bash
count=0
for (( i=1; i<=50; i++ ))
do
    x=$(( i % 5 ))
    if [[ $x -eq 0 ]]
    then
        (( count++ ))
    fi
done
echo "count: $count"
```
**Output:**
```text
count: 10
```

### Script 4: Triangle Validity Test
Tests if three side lengths $A, B, C$ satisfy the triangle inequality theorem ($A+B > C$, $A+C > B$, $B+C > A$).

```bash
#!/bin/bash
read -p "Enter A: " A
read -p "Enter B: " B
read -p "Enter C: " C

if [[ $(( A + B )) -gt $C ]] && [[ $(( A + C )) -gt $B ]] && [[ $(( B + C )) -gt $A ]]
then
    echo "Yes"
else
    echo "No"
fi
```
**Terminal Output (Sample 1):**
```text
Enter A: 4
Enter B: 5
Enter C: 6
Yes
```
**Terminal Output (Sample 2):**
```text
Enter A: 2
Enter B: 7
Enter C: 3
No
```

### Script 5: Count Directory Items (Folders, Files, PDFs)
```bash
#!/bin/bash
file_count=0
folder_count=0
pdf_count=0

for item in $(ls -p)
do
    if [[ "$item" == */ ]]
    then
        ((folder_count++))
    else
        ((file_count++))
        if [[ "$item" == *.pdf ]]
        then
            ((pdf_count++))
        fi
    fi
done

echo "Folders: $folder_count"
echo "Files:   $file_count"
echo "PDF Files: $pdf_count"
```
**Output (Sample Directory):**
```text
Folders: 3
Files:   8
PDF Files: 2
```
