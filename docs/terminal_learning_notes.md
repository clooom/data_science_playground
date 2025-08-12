## Terminal Learning Notes

### Command: echo
**Purpose:** Print text to the terminal or redirect it into a file.  
**Key variations:**  
- `echo "text"` → prints to screen  
- `echo "text" >> file.txt` → appends to file  
- `echo "text" > file.txt` → overwrites file  
**Conditionally running:** use `&&` to only run after success of previous command.  
**Exit status:** Almost always returns success itself (unless write to file fails).



### Command: Quick Homebrew package verification loop
**Purpose:** Check a list of Homebrew packages to see if each is installed, showing ✅ or ❌.
**Code:**
for pkg in openssl readline sqlite3 xz zlib tcl-tk; do
  if brew list --versions "$pkg" >/dev/null 2>&1; then
    echo "✅ $pkg installed: $(brew list --versions "$pkg")"
  else
    echo "❌ $pkg not installed"
  fi
done
**Key points:**
- Uses 'for' loop to iterate over package names.
- 'brew list --versions' returns version info if installed.
- Output is conditionally printed with success/fail symbols.
- Pattern is reusable for checking any list of packages.



Monitoring a Long-Running Command in Another Terminal Tab
Purpose: Check if a process (like compiling Python with pyenv) is still active without interrupting it.

Steps:
Open a second Terminal tab — ⌘T in macOS Terminal.

Monitor CPU usage:

top -o cpu

Shows active processes sorted by CPU usage.
Quit with q.

Optional: Monitor file writes (install progress):

sudo fs_usage | grep Python-3.12

Tracks disk writes related to the Python build.
Stop with Ctrl+C.

When to use:
Any time you run a long compile or data processing command and want reassurance it’s still progressing.