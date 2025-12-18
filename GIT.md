# Git tips

# Git Authentication on Windows Using Git Bash

This guide explains how to authenticate Git on **Windows** after installing Git and opening **Git Bash**. Modern Git authentication is done using **Personal Access Tokens (HTTPS)** or **SSH keys**.

---

## Option 1 — HTTPS Authentication Using a Personal Access Token (Easiest)

### 1. Verify Git Installation

```bash
git --version
```

---

### 2. Configure Your Name and Email (Required)

```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@email.com"
```

Check the configuration:

```bash
git config --global --list
```

---

### 3. Generate a Personal Access Token (PAT)

**GitHub steps:**

1. Go to **Settings → Developer settings → Personal access tokens**
2. Click **Generate new token**
3. Select at least the following scope:

   * `repo`
4. Generate the token and **copy it** (you will only see it once)

---

### 4. Use the Token on First Push

Clone the repository:

```bash
git clone https://github.com/your-username/your-repository.git
```

When running:

```bash
git push
```

Git will ask for credentials:

* **Username** → your GitHub username
* **Password** → paste the **Personal Access Token** (not your GitHub password)

✔️ Windows stores the credentials in **Credential Manager**, so you won’t be prompted again.

---

### 5. Remove Stored Credentials (Optional)

```bash
git config --global --unset credential.helper
```

Or via Windows:

> Control Panel → Credential Manager → Windows Credentials

---

## Option 2 — SSH Authentication (Recommended for Professional Use)

SSH is the preferred method for DevOps, automation, and corporate environments.

---

### 1. Generate an SSH Key

```bash
ssh-keygen -t ed25519 -C "youremail@email.com"
```

Press **Enter** for all prompts (or set a passphrase if desired).

---

### 2. Start the SSH Agent and Add the Key

```bash
eval $(ssh-agent -s)
ssh-add ~/.ssh/id_ed25519
```

---

### 3. Copy the Public Key

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the entire output (starts with `ssh-ed25519`).

---

### 4. Add the SSH Key to GitHub

GitHub:

> Settings → SSH and GPG Keys → New SSH Key

Paste the public key and save.

---

### 5. Test the SSH Connection

```bash
ssh -T git@github.com
```

Expected response:

```text
Hi your-username! You've successfully authenticated.
```

---

### 6. Clone the Repository Using SSH

```bash
git clone git@github.com:your-username/your-repository.git
```

✔️ Git will no longer request passwords or tokens.

---

## Which Method Should You Choose?

| Scenario                | Recommended Method |
| ----------------------- | ------------------ |
| Quick personal projects | HTTPS + Token      |
| Work, automation, CI/CD | SSH                |
| Multiple repositories   | SSH                |
| Higher security         | SSH                |

---

## Common Mistakes

* ❌ Trying to use your GitHub account password
* ❌ Mixing HTTPS and SSH URLs for the same repository
* ❌ Forgetting to configure `user.name` and `user.email`

---

**End of document**


## COMMANDS

A list of commands to help in a routine.

### See the commits
```
git log
```
### List modified files on the latest commit
```
git show --name-only
```
### Reseting the first commit 
```
git reset --soft HEAD 
```
### Show a historical with graphics of branches
```
git log --oneline --graph --all
```
### Remove a commit. (The number should be used in order to inform the commit. Run: `git log --oneline` to see a list of commits in one line.)
```
git rebase -i HEAD~5
```
### Reset as repository.
```
git fetch --all
git reset --hard origin/main
git clean -fd
```

### WARNING CRLF TO LF
---

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


## How to Use `.gitignore`: Subfolders and Wildcards Explained

The `.gitignore` file tells Git which files and directories should not be tracked in a repository. This is especially useful for ignoring build artifacts, temporary files, local configuration, logs, and other files that should not be versioned.

The `.gitignore` file must be placed at the root of the repository (or inside subdirectories if you want rules scoped to those paths). Git evaluates the rules from top to bottom, and more specific rules override generic ones.

---

### Basic Rules

Each line in a `.gitignore` file represents a pattern:

* A blank line is ignored.
* Lines starting with `#` are comments.
* Patterns can match files or directories.
* A trailing `/` indicates a directory.
* Rules apply recursively unless scoped to a specific path.
* An exclamation mark `!` negates a rule (re-includes a previously ignored file).

---

### Using Subfolders

You can target specific folders by prefixing the path:

* `logs/` ignores the `logs` directory everywhere.
* `/logs/` ignores only the `logs` directory at the repository root.
* `src/logs/` ignores `logs` only inside `src`.

Paths are always relative to the location of the `.gitignore` file.

---

### Using Wildcards

Git supports several wildcard patterns:

* `*` matches any number of characters except `/`
* `**` matches any number of directories
* `?` matches a single character
* `[a-z]` matches a range of characters

These allow you to ignore files by extension, name pattern, or directory depth.

---

### Complete Example Covering All Ignore Patterns

Below is a single `.gitignore` example that demonstrates all common ways to ignore files and directories, including root rules, subfolders, wildcards, ranges, and negation:

```
# Ignore all log files anywhere
*.log

# Ignore all temporary files ending with ~
*~

# Ignore all files starting with "temp"
temp*

# Ignore all .env files in any directory
**/.env

# Ignore node_modules in any location
node_modules/

# Ignore build directories only at the root
/build/

# Ignore dist directories in any subfolder
**/dist/

# Ignore all .txt files in docs
docs/*.txt

# Ignore all .txt files recursively inside docs
docs/**/*.txt

# Ignore files with a single-character extension like .a, .b, .c
*.[a-z]

# Ignore cache directories inside any module
modules/**/cache/

# Ignore everything inside logs
logs/**

# But keep a specific log file
!logs/important.log
```

---

### Important Notes

* Files already tracked by Git will not be ignored until they are removed from the index.
* To stop tracking a file that is already committed, you must remove it explicitly using Git commands.
* Always review `.gitignore` rules carefully, as overly broad patterns may hide important files.

Using `.gitignore` correctly helps keep your repository clean, portable, and focused only on what truly matters for version control.


