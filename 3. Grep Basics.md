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
