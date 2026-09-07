# 🐧 Complete Linux Lab Guide: Basics, Vim Editor, & Grep

Welcome to the comprehensive Linux guide! This combined document covers essential Linux terminal commands, text editing with Vim, and pattern searching using `grep`.

---

# 🐧 Introduction to Linux Basics

Welcome to your Linux command-line guide! This document contains a comprehensive command reference followed by an interactive, step-by-step practice session to help you get hands-on experience with the terminal.

---

## 🔍 Part 1: Command Reference Guide

Use this table to look up fundamental Linux commands, their required syntax, and a description of what they do.

| 💻 Command | 📁 Syntax / Arguments | ℹ️ Description |
| :--- | :--- | :--- |
| **`hostname`** | *None* | Displays the name of the machine. Each machine on the network is given a unique name by the system administrator. |
| **`date`** | *None* | Displays the current date and time. |
| **`pwd`** | *None* | Print (on the screen) the pathname of the working directory (i.e. the directory you are presently in). |
| **`ls`** | *None* | List contents of directories. |
| **`ls -p`** | *None* | List directory and put a slash (/) after each entry that is a directory name. |
| **`cd`** | `<FolderName>` | Change working directory to FolderName. |
| **`cd ..`** | *None* | Change to the directory one level up (as specified by the use of two dots). |
| **`cd`** | *None* | Change to your home directory. |
| **`cd ../../..`** | *None* | Change to the directory three levels up (as specified by the use of two dots that is used 3 times separated by a slash (/)). |
| **`cd /`** | *None* | Change to the top most level directory (i.e. the root directory). |
| **`mkdir`** | `<FolderName>` | Make a directory named FolderName. |
| **`mkdir`** | `<FolderName1/FolderName2>` | Create a directory named FolderName2 underneath the one named FolderName1. |
| **`rmdir`** | `<FolderName>` | Remove an empty directory called FolderName. |
| **`rm -r`** | `<FolderName>` | Remove the folder named FolderName that is not empty. |
| **`mv`** | `<OldFolderName> <NewFolderName>` | Rename the directory named from OldFolderName to NewFolderName. |
| **`mv`** | `<FolderName1> <FolderName2>` | Move the directory FolderName1 to FolderName2. |
| **`cp -r`** | `<FolderName1> <FolderName2>` | Copy the directory FolderName1 into FolderName2. |
| **`cp`** | `<FileName> <FolderName>` | Copy the file FileName into FolderName. |
| **`touch`** | `<FileName>` | Create a new file named FileName. |
| **`cat`** | `<FileName>` | A way of displaying the contents of a text file named FileName. |
| **`rm`** | `<FileName>` | Remove the file named FileName. |

---
## 🛠️ Part 2: Practice Session for Students

> 💡 **Student Tip:** Try typing these commands exactly as shown into your terminal. You can track your progress by following along step-by-step.

---

### 🟢 Phase 1: Basic Navigation & Directory Creation

**Step 1:** Run `pwd`
> *Task:* Write down the pathname of your current directory. (The directory you are automatically placed in after logging on is referred to as your 'home' directory.)

**Step 2:** Run `ls`
> *Task:* List the contents of your current directory (should be empty at this stage).

**Step 3:** Run `mkdir testdir`
> *Task:* Make a subdirectory named 'testdir'.

**Step 4:** Run `cd testdir`
> *Task:* Change directory to the new directory.

**Step 5:** Run `pwd`
> *Task:* Write down the pathname of your current directory.

**Step 6:** Run `ls`
> *Task:* List the contents of your current working directory (should be empty at this stage).

---

### 🟡 Phase 2: Returning Home & Exploring the Root System

**Step 7:** Run `cd`
> *Task:* The change directory command, `cd`, on its own will move you back to your 'home directory'. Another way to return to your home directory is to use the command `cd ~`.

**Step 8:** Run `pwd`
> *Task:* Write down the pathname of your current directory (it should be your home directory).

**Step 9:** Run `ls`
> *Task:* List the contents of your current directory (this should now show the name of the subdirectory named `testdir`).

**Step 10:** Run the following sequence:
```bash
cd /
pwd
ls
ls -p
```
> *Task:* Change to the top most level directory (i.e. the root directory). Confirm where you are using the `pwd` command. List the contents of the current directory. List the contents of the current directory and put a forward slash at the end of any entry that is a directory.

**Step 11: System Check**
> *Task:* Check that the names of the directories under the root directory agree with those listed in the theory page. If not, make a note of any differences.

---

### 🔵 Phase 3: Relative Paths & File Operations

**Step 12:** Run the following sequence:
```bash
cd
pwd
ls
```
> *Task:* Change to your home directory. Confirm where you are using the `pwd` command. List the contents of the current directory.

**Step 13:** Run `cd testdir`
> *Task:* Change to the directory named `testdir`.

**Step 14:** Run the following sequence:
```bash
cd ..
pwd
ls
```
> *Task:* Change to the directory one level up (as specified by the use of two dots). Confirm where you are using the `pwd` command. List the contents of the current directory.

**Step 15: Complex Sequence Challenge**
Execute these commands step-by-step to practice active management:
```bash
pwd 
ls
mkdir testdir/play 
ls
cd testdir/play 
pwd
ls
cd .. 
pwd 
ls
mv play play2 
ls
```
> *Task Walkthrough:*
> 1. Check you are in your home directory.
> 2. List the contents of the current directory.
> 3. Create a directory named `play` underneath the one named `testdir`.
> 4. List the contents of the current directory.
> 5. Change directory into the one just created.
> 6. Confirm where you are.
> 7. List the contents of the current directory.
> 8. Change up one level (i.e. back up to the `testdir` directory) and confirm where you are.
> 9. List the contents of the current directory.
> 10. Rename the directory named `play` to `play2`.
> 11. List the contents of the current directory to check that the renaming has been done.

> 📖 **Note (Step 16):** The command `cd testdir/play` uses the name of the directory relative to the current directory. To be more precise you could have specified the command as `cd ./testdir/play` where the single dot means the current directory.

---

### 🔴 Phase 4: Cleaning Up & Resetting

**Step 17:** Run the following sequence:
```bash
cd
pwd
ls
```
> *Task:* Move back up to your home directory. Confirm where you are. List the contents of the current working directory.

**Step 18:** Run `rmdir testdir`
> *Task:* Remove directory. You will find that this command will not work since the directory contains subdirectories. Overcome this by first removing the lower level directories. (Later you will be shown a potentially dangerous command that will remove any directory and anything underneath it.)

**Step 19:** Run the following sequence:
```bash
pwd
ls
```
> *Task:* Check where you are. List the contents of the current directory.

**Step 20:** Run the following sequence:
```bash
cd
mkdir testdir
mkdir testdir/play
```
> *Task:* Recreate the directories again to restore your workspace.



---

# 📝 Vim Editor: Quick Reference Guide

Welcome to your guide for using **Vim** (and Vi) in Linux! Vim is a powerful, terminal-based text editor. This cheat sheet covers basic installation and essential commands to help you create, edit, save, and exit files efficiently.

---

## ⚙️ Installation

To install Vim on a Debian/Ubuntu-based Linux system, open your terminal and run:

```bash
sudo apt install vim
```

---

## 🔍 Command Reference Guide

Vim operates in different **modes** (mainly *Command Mode* and *Insert Mode*). Use the table below to quickly find keybindings and commands.

### 🚀 File Operations & Navigation

| 💻 Command | ℹ️ Description |
| :--- | :--- |
| **`touch <FileName>`** | Create a new empty file. |
| **`vi <FileName>`** | Open the specified file in the Vi/Vim editor. |
| **`vi`** | Open the Vi/Vim editor directly without specifying or creating a file. |

---

### 🔄 Editor Modes

| 💻 Key / Mode | ℹ️ Description |
| :--- | :--- |
| **`Esc`** | Switch to **Command mode** (used for running commands, moving around, and exiting). |
| **`i`** | Switch to **Insert mode** (used for typing text into the file). |

---

### 💾 Saving & Exiting (Command Mode)

| 💻 Command | ℹ️ Description |
| :--- | :--- |
| **`:w`** | **Write**: Save the changes to the current file. |
| **`:q`** | **Quit**: Exit the editor (fails if there are unsaved changes). |
| **`:q!`** | **Quit without saving**: Force exit and discard all unsaved changes. |
| **`:wq`** | **Write & Quit**: Save changes and exit the editor. |
| **`:x`** | **Save & Exit**: Save changes and exit the editor (same as `:wq`). |
| **`:w <FileName>`** | Save the open buffer to a specific `<FileName>` (useful if opened with `vi`). |
| **`:wq <FileName>`** | Save to `<FileName>` and exit. |
| **`:x <FileName>`** | Save to `<FileName>` and exit. |

---

### ✂️ Editing & Undoing

| 💻 Key | ℹ️ Description |
| :--- | :--- |
| **`x`** | Delete a single character under the cursor. |
| **`dw`** | **Delete Word**: Delete from the cursor to the end of the current word. |
| **`dd`** | **Delete Line**: Delete the entire current line. |
| **`u`** | **Undo**: Undo the most recent change. |
| **`U`** | **Undo Line**: Undo all recent changes made on the current line. |

---

> 💡 **Student Tip:** If you ever get stuck or lost in Vim, press the `Esc` key once or twice to make sure you are in **Command Mode**, then type `:q!` and press `Enter` to exit safely without saving unwanted changes!


---

# 🔍 Linux `grep` Command Tutorial & Hands-On Lab

The `grep` (Global Regular Expression Print) command is one of the most powerful text-searching tools in Linux. It allows you to search for specific text patterns within files.

---

## 📋 Setup: Creating the Sample File

Before running the practice examples, create a sample text file named `a_file` with the required demonstration lines.

### **Step 1:** Create the file
```bash
touch a_file
```

### **Step 2:** Populate `a_file`
Open `a_file` in `vim` or `nano` and add the following lines:
```text
boot
book
booze
machine
boots
bungie
bark
aardvark
broken$tuff
robots
```

---

## 🛠️ Interactive `grep` Practice Lab

Work through the 15 examples below to learn how different `grep` flags and Regular Expressions (Regex) modify your searches.

> 💡 **Student Tip:** Practice typing these commands directly into your terminal while viewing this file in VS Code!

---

### 1️⃣ Basic Search
Search for any line containing the substring `"boo"`. `grep` loops through every line of `a_file` and prints lines that match.

```bash
grep "boo" a_file
```
**Expected Output:**
```text
boot
book
booze
boots
```

---

### 2️⃣ Display Line Numbers (`-n`)
Show line numbers alongside matching outputs.

```bash
grep -n "boo" a_file
```
**Expected Output:**
```text
1:boot
2:book
3:booze
5:boots
```

---

### 3️⃣ Invert Match (`-v`)
Display lines that **do not** contain the word `"boo"`.

```bash
grep -v "boo" a_file
```
**Expected Output:**
```text
machine
bungie
bark
aardvark
broken$tuff
robots
```

---

### 4️⃣ Combine Inverted Search with Line Numbers (`-vn`)
Display lines that **do not** match `"boo"`, including their original line numbers.

```bash
grep -vn "boo" a_file
```
**Expected Output:**
```text
4:machine
6:bungie
7:bark
8:aardvark
9:broken$tuff
10:robots
```

---

### 5️⃣ Count Matches (`-c`)
Count and output only the total number of lines where `"boo"` was found.

```bash
grep -c "boo" a_file
```
**Expected Output:**
```text
4
```

---

### 6️⃣ List Matching File Names (`-l`)
Show only the names of files containing matches (searching across all files in the current folder using `*`).

```bash
grep -l "boo" *
```
**Expected Output:**
```text
a_file
```

---

### 7️⃣ Case-Insensitive Search (`-i`)
Turn off case sensitivity so uppercase and lowercase letters match equally.

```bash
grep -i "BOO" a_file
```
**Expected Output:**
```text
boot
book
booze
boots
```

---

### 8️⃣ Match Exact Line (`-x`)
Matches whole lines instead of substrings. Since no single line in `a_file` is strictly `"boo"` alone, this produces no output.

```bash
grep -x "boo" a_file
```
**Expected Output:** *(No output)*

---

### 9️⃣ Print Context After Match (`-A`)
Show the matching line plus `2` additional lines that appear immediately **A**fter it (`-A2`).

```bash
grep -A2 "mach" a_file
```
**Expected Output:**
```text
machine
boots
bungie
```

---

### 🔟 Match Line Endings (`$`)
Use the regex anchor `$` to match lines that end with the letter `e`.

```bash
grep "e$" a_file
```
**Expected Output:**
```text
booze
machine
bungie
```

---

### 1️⃣1️⃣ Match Line Starts (`^`)
Use the regex anchor `^` to match lines starting with the letter `m`.

```bash
grep "^m" a_file
```
**Expected Output:**
```text
machine
```

---

### 1️⃣2️⃣ Extended Regular Expressions (`-E` OR operator)
Use the `-E` flag to enable Extended Regex. The `|` symbol acts as an **OR** operator (matches `"boot"` OR `"boots"`).

```bash
grep -E "boot|boots" a_file
```
**Expected Output:**
```text
boot
boots
```

---

### 1️⃣3️⃣ Escape Special Characters (`\`)
Use a backslash `\` to escape special symbols (like `$`) so they are treated as literal characters.

```bash
grep '\$' a_file
```
**Expected Output:**
```text
broken$tuff
```

---

### 1️⃣4️⃣ Wildcard Character Matching (`.`)
The dot `.` matches any single character. Here `oo..` matches `"oo"` followed by at least two characters.

```bash
grep 'oo..' a_file
```
**Expected Output:**
```text
booze
boots
```

---

### 1️⃣5️⃣ Zero-or-More Repeats (`*`)
The `*` symbol matches zero or more occurrences of the preceding character (`o`). This matches any line containing `o` followed by zero or more `o`s.

```bash
grep 'oo*' a_file
```
**Expected Output:**
```text
boot
book
booze
boots
broken$tuff
robots
```

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

# Java Multithreading & Parallel Programming Guide

A comprehensive guide to multithreading concepts in Java, explaining operating system thread fundamentals, practical concurrent programming examples, code explanations, and expected outputs.

---

## Table of Contents
1. [Introduction to Threading](#1-introduction-to-threading)
   - [What is a Thread?](#what-is-a-thread)
   - [Why is Multithreading Needed?](#why-is-multithreading-needed)
   - [Why is Multithreading Required in Operating Systems?](#why-is-multithreading-required-in-operating-systems)
2. [Problem 1: Parallel Sum of an Array](#2-problem-1-parallel-sum-of-an-array)
   - [Code Implementation](#code-implementation-array-sum)
   - [Code Explanation](#code-explanation-array-sum)
   - [Expected Output](#expected-output-array-sum)
3. [Problem 2: Parallel Matrix Row Multiplication](#3-problem-2-parallel-matrix-row-multiplication)
   - [Code Implementation](#code-implementation-matrix-scale)
   - [Code Explanation](#code-explanation-matrix-scale)
   - [Expected Output](#expected-output-matrix-scale)

---

## 1. Introduction to Threading

### What is a Thread?
A **thread** is the smallest execution unit within a computer program that can be scheduled and managed independently by the operating system CPU scheduler. Multiple threads can exist within a single process, sharing common resources such as memory space, open files, and code segments, while maintaining their own private execution context (registers, program counter, and execution stack).

### Why is Multithreading Needed?
1. **Parallel Execution & Multi-core Utilization:** Modern computer hardware features CPUs with multiple physical cores. Single-threaded applications can only execute on one core at a time, leaving remaining processing power underutilized. Multithreading allows programs to distribute workloads across multiple cores simultaneously.
2. **Improved Responsiveness:** In interactive applications (such as desktop GUIs or web applications), running time-consuming or background operations (e.g., file downloads, database queries) on separate worker threads prevents the main UI thread from freezing.
3. **High Throughput:** Applications processing large datasets or handling simultaneous web client requests (like web servers) achieve significantly higher processing throughput by executing independent tasks concurrently.

### Why is Multithreading Required in Operating Systems?
Operating Systems depend on multithreading for efficient system kernel management and process execution:
* **Efficient Resource Management:** Creating a process requires allocating a distinct virtual memory space, file descriptor tables, and security contexts, which is computationally expensive. Threads share process memory, making thread creation and context switching far cheaper than process-level context switching.
* **Asynchronous I/O Handling:** When a thread performs an input/output operation (e.g., waiting for disk reading or network packets), the operating system can put that specific thread in a waiting state while switching execution to another ready thread, ensuring the CPU remains busy and efficient.
* **Concurrent System Services:** Operating systems use kernel threads to handle concurrent background tasks—such as memory management (garbage collection/paging), hardware interrupt servicing, and file system synchronization—without interrupting user applications.

---

## 2. Problem 1: Parallel Sum of an Array

### Problem Statement
Divide an array of numbers into two equal halves. Create two threads where **Thread 1** calculates the sum of the first half and **Thread 2** calculates the sum of the second half. The main thread then adds both partial sums together to display the total sum.

### Code Implementation (Array Sum)
```java
class SumTask implements Runnable {
    private final int[] arr;
    private final int start;
    private final int end;
    private int partialSum;

    public SumTask(int[] arr, int start, int end) {
        this.arr = arr;
        this.start = start;
        this.end = end;
    }

    public int getPartialSum() {
        return partialSum;
    }

    @Override
    public void run() {
        partialSum = 0;
        for (int i = start; i < end; i++) {
            partialSum += arr[i];
        }
    }
}

public class ArraySum {
    public static void main(String[] args) throws InterruptedException {
        int[] numbers = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}; // Total sum = 55
        int mid = numbers.length / 2;

        SumTask task1 = new SumTask(numbers, 0, mid);
        SumTask task2 = new SumTask(numbers, mid, numbers.length);

        Thread t1 = new Thread(task1);
        Thread t2 = new Thread(task2);

        // Start worker threads
        t1.start();
        t2.start();

        // Wait for worker threads to complete execution
        t1.join();
        t2.join();

        int totalSum = task1.getPartialSum() + task2.getPartialSum();

        System.out.println("Thread 1 Sum: " + task1.getPartialSum());
        System.out.println("Thread 2 Sum: " + task2.getPartialSum());
        System.out.println("Total Array Sum: " + totalSum);
    }
}
```

### Code Explanation (Array Sum)
1. **`SumTask` Implementation (`Runnable` Interface):**
   - The `SumTask` class implements Java's `Runnable` interface, allowing instances to be executed by a thread.
   - It stores references to the shared array (`arr`), processing index limits (`start` and `end`), and a variable to hold the calculated sum (`partialSum`).
   - The `run()` method loops from `start` (inclusive) to `end` (exclusive) and accumulates the values into `partialSum`.

2. **Array Division & Thread Creation (`main` method):**
   - The main thread creates an integer array of 10 elements and determines the midpoint (`mid = 5`).
   - Two task instances are created: `task1` processes indices `0` to `4` (`{1, 2, 3, 4, 5}`), and `task2` processes indices `5` to `9` (`{6, 7, 8, 9, 10}`).
   - Two `Thread` objects (`t1` and `t2`) are initialized with their respective tasks.

3. **Thread Execution and Synchronization:**
   - `t1.start()` and `t2.start()` invoke the Operating System scheduler to run both threads concurrently.
   - `t1.join()` and `t2.join()` block the execution of the main thread until `t1` and `t2` have finished processing. This prevents the main thread from reading partial sums before calculation completes.
   - Once both threads finish, the main thread reads the partial sums via `getPartialSum()`, adds them together, and prints the results.

### Expected Output
```text
Thread 1 Sum: 15
Thread 2 Sum: 40
Total Array Sum: 55
```

---

## 3. Problem 2: Parallel Matrix Row Multiplication

### Problem Statement
Given a $3 	imes 3$ matrix and a single scalar value, create 3 separate worker threads where each thread multiplies a single row of the matrix by the scalar value simultaneously.

### Code Implementation (Matrix Scale)
```java
public class MatrixScale {
    private static final int ROWS = 3;
    private static final int COLS = 3;
    private static final int[][] matrix = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    static class RowTask implements Runnable {
        private final int rowIndex;
        private final int scalar;

        public RowTask(int rowIndex, int scalar) {
            this.rowIndex = rowIndex;
            this.scalar = scalar;
        }

        @Override
        public void run() {
            for (int j = 0; j < COLS; j++) {
                matrix[rowIndex][j] *= scalar;
            }
        }
    }

    public static void main(String[] args) throws InterruptedException {
        Thread[] threads = new Thread[ROWS];
        int scalar = 5;

        // Create and start a thread for each row
        for (int i = 0; i < ROWS; i++) {
            threads[i] = new Thread(new RowTask(i, scalar));
            threads[i].start();
        }

        // Wait for all threads to complete
        for (int i = 0; i < ROWS; i++) {
            threads[i].join();
        }

        // Display the modified matrix result
        System.out.println("Matrix after scalar multiplication (" + scalar + "x):");
        for (int i = 0; i < ROWS; i++) {
            for (int j = 0; j < COLS; j++) {
                System.out.print(matrix[i][j] + "	");
            }
            System.out.println();
        }
    }
}
```

### Code Explanation (Matrix Scale)
1. **Shared Memory Structure:**
   - The matrix `matrix` is defined as a `private static final` 2D array accessible to all inner static classes within `MatrixScale`.
   - Because each thread accesses and modifies a completely distinct row index (`matrix[rowIndex]`), no data races or thread contention occur during parallel write operations.

2. **Row Multiplier Task (`RowTask`):**
   - Each `RowTask` instance is instantiated with a specific `rowIndex` and target `scalar` value.
   - Inside `run()`, a single `for` loop iterates across all columns `j` of that assigned row and multiplies each element by `scalar` in-place.

3. **Parallel Dispatch and Synchronization Loop:**
   - An array of `Thread` objects (`threads`) of length equal to `ROWS` (3) is instantiated.
   - A `for` loop instantiates and starts each worker thread (`threads[i].start()`), assigning Thread 0 to Row 0, Thread 1 to Row 1, and Thread 2 to Row 2.
   - A second `for` loop calls `join()` on each thread element to ensure all 3 rows have finished scalar multiplication before the main thread attempts to display the matrix.
   - Finally, the main thread iterates over the matrix and prints the scaled values in tabular format.

### Expected Output
```text
Matrix after scalar multiplication (5x):
5	10	15	
20	25	30	
35	40	45	
```
