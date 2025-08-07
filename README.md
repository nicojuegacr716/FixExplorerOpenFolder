# Fix for Windows 10 Opening Folders in New Windows

This repository provides a simple fix for the issue in Windows 10 where opening folders launches new File Explorer windows instead of reusing the current one.

---

## The Problem

Sometimes Windows opens a new File Explorer window each time you open a folder, cluttering your desktop and making navigation difficult.

---

## The Fix

Run the following commands in an **elevated Command Prompt (Admin)** to fix the issue:

### Step 1: (Optional) Force folders to open in a new window

This command resets the folder open behavior to always open in a new window (useful to revert or test):


```bash
reg add HKCR\Folder\shell\open\command /ve /d "\"%SystemRoot%\\explorer.exe\" \"%1\"" /f
```

### Step 2: Fix — make folders open in the same window

This command restores the default delegate that allows Windows to reuse the current window when opening folders:



```bash
reg add HKCR\Folder\shell\open\command /v "DelegateExecute" /d "{11dbb47c-a525-400b-9e80-a54615a090c0}" /f
```

---

## How to Use

1. Open Command Prompt as administrator:  
   - Press `Windows + X` and select **Command Prompt (Admin)** or **Windows PowerShell (Admin)**.  
2. Copy and paste each command, pressing Enter after each.  
3. Restart Windows Explorer or reboot your PC for the changes to take effect.

---

## Result

After applying the fix, folders will open in the same File Explorer window, avoiding multiple windows opening unnecessarily.

---

## Notes

- These commands modify Windows Registry entries. It’s recommended to create a system restore point before applying.  
- Only tested in Windows 10 22H2 Build 19045.6093

---

Contributions and improvements are welcome!

---

**Author:** nicojuegacr716 / Nickname : Rynox 
