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

> 💡 **Student Tip:** Try typing these commands exactly as shown into your terminal. You can track your progress by checking off the boxes`[ ].`

### 🟢 Phase 1: Basic Navigation & Directory Creation

- [ ] **Step 1:** Run `pwd`
  * *Task:* Write down the pathname of your current directory. (The directory you are automatically placed in after logging on is referred to as your 'home' directory.)
- [ ] **Step 2:** Run `ls`
  * *Task:* List the contents of your current directory (should be empty at this stage).
- [ ] **Step 3:** Run `mkdir testdir`
  * *Task:* Make a subdirectory named 'testdir'.
- [ ] **Step 4:** Run `cd testdir`
  * *Task:* Change directory to the new directory.
- [ ] **Step 5:** Run `pwd`
  * *Task:* Write down the pathname of your current directory.
- [ ] **Step 6:** Run `ls`
  * *Task:* List the contents of your current working directory (should be empty at this stage).

### 🟡 Phase 2: Returning Home & Exploring the Root System

- [ ] **Step 7:** Run `cd`
  * *Task:* The change directory command, `cd`, on its own will move you back to your 'home directory'. Another way to return to your home directory is to use the command `cd ~`.
- [ ] **Step 8:** Run `pwd`
  * *Task:* Write down the pathname of your current directory (it should be your home directory).
- [ ] **Step 9:** Run `ls`
  * *Task:* List the contents of your current directory (this should now show the name of the subdirectory named testdir).
- [ ] **Step 10:** Run the following sequence:
  ```bash
  cd /
  pwd
  ls
  ls -p
  ```
  * *Task:* Change to the top most level directory (i.e. the root directory). Confirm where you are using the `pwd` command. List the contents of the current directory. List the contents of the current directory and put a forward slash at the end of any entry that is a directory.
- [ ] **Step 11:** **System Check (Task)**
  * *Task:* Check that the names of the directories under the root directory agree with those listed in the theory page. If not, make a note of any differences.

### 🔵 Phase 3: Relative Paths & File Operations

- [ ] **Step 12:** Run the following sequence:
  ```bash
  cd
  pwd
  ls
  ```
  * *Task:* Change to your home directory. Confirm where you are using the `pwd` command. List the contents of the current directory.
- [ ] **Step 13:** Run `cd testdir`
  * *Task:* Change to the directory named testdir.
- [ ] **Step 14:** Run the following sequence:
  ```bash
  cd ..
  pwd
  ls
  ```
  * *Task:* Change to the directory one level up (as specified by the use of two dots). Confirm where you are using the `pwd` command. List the contents of the current directory.
- [ ] **Step 15:** **Complex Sequence Challenge**
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
  * *Task Walkthrough:*
    1. Check you are in your home directory.
    2. List the contents of the current directory.
    3. Create a directory named play underneath the one named testdir.
    4. List the contents of the current directory.
    5. Change directory into the one just created.
    6. Confirm where you are.
    7. List the contents of the current directory.
    8. Change up one level (i.e. back up to the testdir directory) and confirm where you are.
    9. List the contents of the current directory.
    10. Rename the directory named play to play2.
    11. List the contents of the current directory to check that the renaming has been done.

> 📖 **Note (Step 16):** The command `cd testdir/play` uses the name of the directory relative to the current directory. To be more precise you could have specified the command as `cd ./testdir/play` where the single dot means the current directory.

### 🔴 Phase 4: Cleaning Up & Resetting

- [ ] **Step 17:** Run the following sequence:
  ```bash
  cd
  pwd
  ls
  ```
  * *Task:* Move back up to your home directory. Confirm where you are. List the contents of the current working directory.
- [ ] **Step 18:** Run `rmdir testdir`
  * *Task:* Remove directory. You will find that this command will not work since the directory contains subdirectories. Overcome this by first removing the lower level directories. (Later you will be shown a potentially dangerous command that will remove any directory and anything underneath it.)
- [ ] **Step 19:** Run the following sequence:
  ```bash
  pwd
  ls
  ```
  * *Task:* Check where you are. List the contents of the current directory.
- [ ] **Step 20:** Run the following sequence:
  ```bash
  cd
  mkdir testdir
  mkdir testdir/play
  ```
  * *Task:* Recreate the directories again to restore your workspace.
