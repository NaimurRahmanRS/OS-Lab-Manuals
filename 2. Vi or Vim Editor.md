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
