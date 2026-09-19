

# Python Virtual Environment in VS Code

A **Python virtual environment** is an isolated environment for a project.

It allows each project to have its own Python packages and package versions without affecting other projects.

---

## Why Use a Virtual Environment?

Suppose you have two Python projects.

```text
Project A
└── requests 2.31

Project B
└── requests 2.25
```

Without virtual environments, different package versions can cause conflicts.

With virtual environments, each project keeps its own dependencies.

```text
Project A
└── .venv
    └── requests 2.31

Project B
└── .venv
    └── requests 2.25
```

---

# Creating a Python Virtual Environment in VS Code

## 1. Create or Open a Project Folder

Example:

```text
python-api-practice
```

In VS Code:

```text
File → Open Folder
```

Select your project folder.

---

## 2. Open the VS Code Terminal

Go to:

```text
Terminal → New Terminal
```

Example terminal:

```powershell
PS C:\Users\YourName\python-api-practice>
```

---

## 3. Create the Virtual Environment

Run:

```powershell
python -m venv .venv
```

Explanation:

```text
python   → runs Python

-m       → runs a Python module

venv     → Python's virtual environment module

.venv    → name of the virtual environment folder
```

Your project should now look like:

```text
python-api-practice/
│
├── .venv/
│
└── main.py
```

`.venv` is a common name for a Python virtual environment.

---

## 4. Activate the Virtual Environment

### Windows PowerShell

```powershell
.venv\Scripts\Activate.ps1
```

### Windows Command Prompt

```cmd
.venv\Scripts\activate
```

### macOS/Linux

```bash
source .venv/bin/activate
```

After activation, the terminal should show something like:

```text
(.venv) PS C:\Users\YourName\python-api-practice>
```

The `(.venv)` means the virtual environment is active.

---

# Select the Python Interpreter in VS Code

Press:

```text
Ctrl + Shift + P
```

Search for:

```text
Python: Select Interpreter
```

Choose the Python interpreter inside:

```text
.venv
```

If you do not see the Python interpreter option, install the Microsoft Python extension for VS Code.

---

# Installing Python Packages

Python packages are installed using `pip`.

For example:

```powershell
python -m pip install requests
```

Or:

```powershell
python -m pip install openai
```

Using:

```powershell
python -m pip
```

is helpful because it makes sure `pip` belongs to the Python interpreter you are currently using.

---

# What is pip?

`pip` is Python's package installer.

It installs packages from the Python Package Index, commonly called **PyPI**.

Example:

```powershell
python -m pip install requests
```

This installs the `requests` package.

Then you can use it in Python:

```python
import requests
```

Another example:

```powershell
python -m pip install openai
```

Then:

```python
from openai import OpenAI
```

---

# Checking Installed Packages

To see all installed packages:

```powershell
python -m pip list
```

To check a specific package:

```powershell
python -m pip show openai
```

---

# Simple Test

Create:

```text
main.py
```

Add:

```python
from openai import OpenAI

print("OpenAI package imported successfully!")
```

Run:

```powershell
python main.py
```

Output:

```text
OpenAI package imported successfully!
```

---

# Understanding the Workflow

The complete workflow looks like this:

```text
Create project folder
        ↓
Open project in VS Code
        ↓
Create virtual environment
        ↓
python -m venv .venv
        ↓
Activate virtual environment
        ↓
Select .venv Python interpreter
        ↓
Install packages using pip
        ↓
python -m pip install package-name
        ↓
Write Python code
        ↓
Run Python program
```

---

# Example Project Setup

```powershell
mkdir python-api-practice

cd python-api-practice

python -m venv .venv
```

Activate the environment:

```powershell
.venv\Scripts\Activate.ps1
```

Install packages:

```powershell
python -m pip install openai
```

Create:

```text
main.py
```

Then run:

```powershell
python main.py
```

---

# `venv` vs `pip`

These two tools do different jobs.

```text
venv
 ↓
Creates an isolated Python environment

pip
 ↓
Installs Python packages

Python Program
 ↓
Imports and uses those packages
```

Example:

```powershell
python -m venv .venv
```

creates the environment.

Then:

```powershell
python -m pip install openai
```

installs the OpenAI package inside that environment.

Then Python can use it:

```python
from openai import OpenAI
```

---

# Important: Do Not Upload `.venv` to GitHub

The `.venv` folder can contain thousands of files and should normally not be committed to GitHub.

Create a file named:

```text
.gitignore
```

Add:

```gitignore
.venv/
```

Your project might look like:

```text
python-api-practice/
│
├── .gitignore
├── main.py
└── .venv/
```

Git will ignore `.venv`.

---

# Saving Dependencies with `requirements.txt`

Instead of uploading your virtual environment, save the packages your project uses.

Run:

```powershell
python -m pip freeze > requirements.txt
```

This creates:

```text
requirements.txt
```

Example:

```text
openai==x.x.x
requests==x.x.x
```

Your GitHub project can then contain:

```text
python-api-practice/
│
├── .gitignore
├── main.py
├── README.md
└── requirements.txt
```

Someone who downloads your project can install all dependencies with:

```powershell
python -m pip install -r requirements.txt
```

---

# Deactivating a Virtual Environment

When you are finished working, run:

```powershell
deactivate
```

The `(.venv)` indicator will disappear from the terminal.

---

# Quick Command Reference

```powershell
# Create virtual environment
python -m venv .venv

# Activate on Windows PowerShell
.venv\Scripts\Activate.ps1

# Install a package
python -m pip install openai

# Show installed packages
python -m pip list

# Save dependencies
python -m pip freeze > requirements.txt

# Install dependencies from requirements.txt
python -m pip install -r requirements.txt

# Run Python program
python main.py

# Deactivate virtual environment
deactivate
```

---

# Key Concepts

* **Python** is the programming language.
* **venv** creates an isolated Python environment.
* **pip** installs Python packages.
* **PyPI** is the repository where most Python packages are published.
* **`.venv`** commonly stores the virtual environment.
* **`requirements.txt`** records project dependencies.
* **`.gitignore`** prevents files such as `.venv` from being uploaded to GitHub.

A good Python project workflow is:

```text
Project
   ↓
Virtual Environment
   ↓
Install Packages
   ↓
Write Code
   ↓
Save Dependencies
   ↓
Push Source Code to GitHub
```


