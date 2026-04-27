# Tutorial: Fixing Debian Buster Environment and Compiling with Nuitka

## Objective

Resolve issues related to:

* Broken `apt update` (Debian Buster EOL)
* Nuitka compilation errors (`-lz`)
* `--onefile` not working properly
* Errors installing `requests_pkcs12` / `cryptography` on Python 3.7

---

# 1. Fix Debian Buster repositories

## Problem

Error:

```
404 Not Found
repository no longer has a Release file
```

## Solution

Edit:

```bash
sudo nano /etc/apt/sources.list
```

Replace with:

```bash
deb http://archive.debian.org/debian buster main contrib non-free
deb http://archive.debian.org/debian-security buster/updates main contrib non-free
```

Disable date validation:

```bash
echo 'Acquire::Check-Valid-Until "false";' | sudo tee /etc/apt/apt.conf.d/99ignore-release-date
```

Update:

```bash
sudo apt update
```

---

# 2. Install compilation dependencies (Nuitka)

## Problem

Error:

```
/usr/bin/ld: cannot find -lz
```

## Solution

Install required packages:

```bash
sudo apt-get install -y \
    build-essential \
    zlib1g-dev \
    libffi-dev \
    libssl-dev \
    python3-dev \
    python3-pip \
    patchelf \
    pkg-config
```

---

# 3. Prepare Python environment (venv)

Create virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate
```

Upgrade tools:

```bash
pip install --upgrade pip setuptools wheel
```

---

# 4. Fix `cryptography` issue on Python 3.7

## Problem

Error:

```
TomlError: heterogenous_array
```

## Cause

* Modern `cryptography` versions do not support Python 3.7
* Old pip uses an outdated TOML parser

## Solution

Install a compatible version:

```bash
pip install "cryptography==41.0.7"
```

Then:

```bash
pip install requests_pkcs12
```

---

# 5. Install and update Nuitka properly

```bash
pip install --upgrade nuitka scons
```

---

# 6. Compile with Nuitka (correct usage)

Recommended command:

```bash
python3 -m nuitka --onefile app_name.py
```

---

## Expected output

After compilation:

Final executable:

```
app_name.bin
```

Temporary folder (normal behavior):

```
app_name.dist/
```

This folder is used internally. The `.bin` file is the final output.

---

# Common issues and solutions

## Only `.dist/` folder generated, no `.bin`

Causes:

* Missing dependencies (e.g. zlib)
* Silent failure during packaging
* Outdated system (Debian Buster)

Solution:

* Reinstall dependencies (Step 2)
* Ensure `patchelf` is installed
* Upgrade Nuitka via pip

---

## Nuitka warning about Debian packages

```
Standalone with Python package from Debian installation may not be working
```

Meaning:

* System packages installed via apt may not work properly in standalone mode

Best practice:

* Always use virtual environments with pip

---

# Advanced recommendation

Current environment:

* Debian Buster
* Python 3.7 (end-of-life)

This setup is no longer supported by modern libraries.

## Recommended upgrade paths:

* Debian 11 (Bullseye) → Python 3.9
* Debian 12 (Bookworm) → Python 3.11

Benefits:

* Better compatibility with modern libraries
* Fewer build errors
* Improved Nuitka support

---

# Final checklist

```bash
# Fix repositories
nano /etc/apt/sources.list

# Update apt
apt update

# Install dependencies
apt install build-essential zlib1g-dev libffi-dev libssl-dev python3-dev patchelf

# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Upgrade pip tools
pip install --upgrade pip setuptools wheel

# Fix cryptography
pip install cryptography==41.0.7

# Install libraries
pip install requests_pkcs12 nuitka scons

# Compile
python3 -m nuitka --onefile app_name.py
```
