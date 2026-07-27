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
