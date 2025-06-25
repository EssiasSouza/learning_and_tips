# Git tips

The warning you're seeing:

warning: in the working copy of 'venv/Lib/site-packages/pycparser/yacctab.py', LF will be replaced by CRLF the next time Git touches it
...means that Git has detected a line ending difference. The file currently uses LF (Unix-style line endings), but your Git configuration will convert it to CRLF (Windows-style) the next time Git writes to the file, possibly causing unnecessary changes or issues with code that is sensitive to line endings.

This usually happens on Windows systems due to the default Git configuration.

**Option 1**: Make Git preserve LF line endings (recommended for consistency)
Run this in your repository (or globally if preferred):

```
git config core.autocrlf input
```

This will:

Keep LF line endings in the repository.

Convert CRLF → LF on commit (input).

Not convert LF → CRLF on checkout.

🔧 Option 2: Tell Git to always use CRLF on checkout (Windows default)

```
git config core.autocrlf true
```
This will:

Convert LF → CRLF when checking out.

Convert CRLF → LF when committing.

Use this only if all contributors are on Windows and CRLF doesn’t break the code.

### Git Default Line Ending Settings (Platform Dependent)

Git’s default behavior for handling line endings depends on **your operating system** and the **initial configuration** when Git was installed.

Here’s a breakdown:

---

### 🪟 **On Windows**

**Default setting:**

```bash
core.autocrlf = true
```

**Behavior:**

* On **checkout**: Git converts LF → CRLF (so files in your working directory use Windows-style endings).
* On **commit**: Git converts CRLF → LF (so the repository stores Unix-style endings).

✅ This works well **for text editors on Windows** that expect CRLF
❌ But it can cause noisy diffs and break things in scripts that are sensitive to CRLF (like shell scripts or some Python tools).

---

### 🐧 **On Linux/macOS**

**Default setting:**

```bash
core.autocrlf = input
```

**Behavior:**

* On **checkout**: Git leaves line endings as-is (LF).
* On **commit**: Git converts CRLF → LF (ensures only LF is stored in the repo).

✅ Recommended for **cross-platform compatibility and development environments**.

---

### 🔍 Check Your Current Setting

To see what your Git is currently set to:

```bash
git config --get core.autocrlf
```

Or for the global setting:

```bash
git config --global --get core.autocrlf
```

---

### 📌 Summary Table

| Platform    | Default `core.autocrlf` | Working Directory Line Endings | Repo Line Endings |
| ----------- | ----------------------- | ------------------------------ | ----------------- |
| Windows     | `true`                  | CRLF                           | LF                |
| Linux/macOS | `input`                 | LF                             | LF                |


