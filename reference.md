# Git/GitHub Command Cheat Sheet
## OS-Specific Quick Reference for Learners

---

## TERMINAL BASICS (Know Your Shell First)

### Mac Users
```bash
# Check your shell
echo $SHELL
# You'll see: /bin/bash or /bin/zsh (both work fine)

# Open Terminal: Cmd + Space → type "Terminal" → Enter
```

### Windows Users (PowerShell)
```powershell
# PowerShell is built-in (recommended, modern syntax)
# Open: Press Windows Key → type "PowerShell" → Enter

# OR use Git Bash (installed with Git)
# More similar to Mac syntax; optional
```

### Windows ARM Users
```powershell
# Same as Windows PowerShell
# Note: Git operations may be ~5-10% slower on ARM
# This is normal; don't worry
```

---

## GIT SETUP (Do This ONCE, First Time)

### All OS
```bash
# Check if Git is installed
git --version
# Should show: git version 2.x.x

# Configure your identity (required before first commit)
git config --global user.name "Your Name"
git config --global user.email "your.email@gmail.com"

# Verify configuration
git config --global --list
# Look for: user.name=Your Name, user.email=your.email@gmail.com
```

---

## SECTION 1: GIT ESSENTIALS (Local Repository)

### Create Your First Repo
```bash
# Create folder
mkdir ~/bootcamp_practice
cd ~/bootcamp_practice

# Initialize Git (creates hidden .git folder)
git init
# Output: Initialized empty Git repository in /Users/yourname/bootcamp_practice/.git/

# Check status (shows current state)
git status
# Output: On branch master, No commits yet
```

### Create & Commit Your First File

#### Mac/Linux
```bash
# Create a simple Python file
cat > data_analysis.py << 'EOF'
def load_data(file_path):
    """Load data from CSV"""
    import pandas as pd
    return pd.read_csv(file_path)
EOF

# OR open your editor:
code data_analysis.py  # Opens VS Code
# Type the Python code above, save
```

#### Windows PowerShell
```powershell
# Create file using PowerShell
@'
def load_data(file_path):
    """Load data from CSV"""
    import pandas as pd
    return pd.read_csv(file_path)
'@ | Out-File -Encoding UTF8 data_analysis.py

# OR open VS Code
code data_analysis.py
# Type code, save
```

### Stage & Commit
```bash
# Check status (see your new file)
git status
# Output: Untracked files: data_analysis.py

# Stage the file (prepare for commit)
git add data_analysis.py

# Check status again (file is now staged)
git status
# Output: Changes to be committed: data_analysis.py

# Commit (save to history)
git commit -m "Initial data loading function"
# Output: 1 file changed, 4 insertions(+), create mode 100644 data_analysis.py

# View commit history
git log
# Shows: commit hash, author, date, message

# Shorter view
git log --oneline
# Shows one line per commit (easier to read)
```

### Make Changes (2nd & 3rd Commit)

#### Mac/Linux
```bash
# Edit the file
echo "" >> data_analysis.py
echo "# Second version: added error handling" >> data_analysis.py

# OR open in editor:
code data_analysis.py
# Add a comment, save
```

#### Windows PowerShell
```powershell
# Edit the file
Add-Content -Path data_analysis.py -Value "`n# Second version: added error handling"

# OR open in editor:
code data_analysis.py
# Add a comment, save
```

### Commit Again
```bash
# Check status (file is "modified")
git status

# Stage & commit
git add data_analysis.py
git commit -m "Add error handling comments"

# Repeat ONE more time to have 3 commits
# Edit file again → git add → git commit -m "Your message"

# View all 3 commits
git log --oneline
# Output:
# abc1234 Add error handling comments
# def5678 Initial data loading function
# (earlier commits if any)
```

---

## SECTION 2: GITHUB & GITHUB INTEGRATION

### Create Remote Repository on GitHub

1. **Go to github.com** (must be logged in)
2. **Click "+" icon** (top right) → "New repository"
3. **Fill in:**
   - Repository name: `bootcamp-practice` (use hyphens, not spaces)
   - Description: "Learning Git for data science bootcamp"
   - Visibility: **Public** (easier for learning)
   - **Do NOT** initialize with README (we'll push our existing code)
4. **Click "Create repository"**
5. **Copy the HTTPS URL** (visible on next screen)
   - Looks like: `https://github.com/yourname/bootcamp-practice.git`

### Connect Local to Remote & Push

```bash
# Add remote connection (origin = your GitHub repo)
git remote add origin https://github.com/yourname/bootcamp-practice.git
# (Replace 'yourname' with your GitHub username)

# Rename default branch to 'main' (modern standard)
git branch -M main

# Push your commits to GitHub (first time with -u flag)
git push -u origin main
# Output: Counting objects, Compressing objects, Writing objects...
# After ~5 seconds: [new branch main → main]

# Verify: Go to github.com, refresh your repo page
# You should see your data_analysis.py file & commit history!
```

### Verify Push Worked
- Navigate to: `https://github.com/yourname/bootcamp-practice`
- You should see:
  - Your `data_analysis.py` file in the repo
  - Commit history on the left (3 commits)
  - Green checkmark next to filenames ✓

---

## VS CODE GIT INTEGRATION (GUI Instead of Terminal)

### Open Project in VS Code
```bash
# Navigate to your project folder
cd ~/bootcamp_practice

# Open in VS Code
code .
# (The dot means "open current folder")

# OR open VS Code → File → Open Folder → select bootcamp_practice
```

### Use Source Control Panel

**Location:** Left sidebar → icon with 3 circles (Source Control)

**Workflow:**

1. **Edit a file** (e.g., README.md)
   - Create new file: README.md
   - Add text: "# My Data Science Project"
   - Save (Cmd/Ctrl + S)

2. **Stage in VS Code**
   - Source Control panel shows your changed files
   - Hover over filename → click **+** button to stage
   - (Equivalent to `git add`)

3. **Commit in VS Code**
   - Type message in **Message** box at top of Source Control
   - Message: "Add project README"
   - Click **checkmark** button (or Ctrl + Enter)
   - (Equivalent to `git commit -m "..."`

4. **Push in VS Code**
   - Click "Sync Changes" button (bottom left)
   - OR click "..." (three dots) in Source Control → "Push"
   - (Equivalent to `git push`)

5. **Verify on GitHub**
   - Refresh github.com/yourname/bootcamp-practice
   - Your README.md now appears in the repo
   - Commit history shows your new commit

---

## SECTION 3: BRANCHING & PULL REQUESTS

### Create a Feature Branch

#### Terminal Method
```bash
# Create and switch to new branch
git checkout -b feature/add-preprocessing
# Output: Switched to a new branch 'feature/add-preprocessing'

# Verify you're on new branch
git branch
# Output:
#   feature/add-preprocessing  ← current (marked with *)
#   main
```

#### VS Code Method
- Source Control panel → click branch name (bottom left)
- Type new branch name: `feature/add-preprocessing`
- Select "Create new branch from main"
- Automatically switches to new branch

### Make Changes on Feature Branch
```bash
# Add new function to data_analysis.py
code data_analysis.py

# Add this function:
"""
def preprocess_data(df):
    '''Remove nulls, normalize columns'''
    return df.dropna().fillna(0)
"""

# Save file
# Stage & commit in VS Code (or terminal)
git add data_analysis.py
git commit -m "Add preprocessing function"
```

### Push Branch to GitHub
```bash
# Push this branch to GitHub
git push -u origin feature/add-preprocessing
# Output: [new branch feature/add-preprocessing → feature/add-preprocessing]

# Verify on GitHub: Refresh page
# You should see dropdown: "main" vs "feature/add-preprocessing"
```

### Create Pull Request (PR) on GitHub

1. **Go to github.com/yourname/bootcamp-practice**
2. **You'll see a banner:** "Compare & pull request" (yellow button)
3. **Click it** → fills in PR form
4. **Add description:** "Adds preprocessing function to handle null values"
5. **Click "Create pull request"**
6. **On PR page, click "Merge pull request"** → "Confirm merge"

### Merge Conflict Demo (Intentional)

**Setup (2 people needed):**

```bash
# Partner A: Edit main_analysis.py line 5
git checkout -b feature/threshold-low
# Edit: threshold = 0.5
git add main_analysis.py
git commit -m "Set low threshold"
git push -u origin feature/threshold-low
# Create PR on GitHub → Merge

# Partner B: Edit same file, same line (before A's merge)
git checkout -b feature/threshold-high
# Edit: threshold = 0.75
git add main_analysis.py
git commit -m "Set high threshold"
git push -u origin feature/threshold-high
# Try to create PR → CONFLICT!

# Resolve conflict in VS Code:
git checkout main
git pull origin main
git checkout feature/threshold-high
git merge main
# Conflict markers appear in file
# <<<<<< HEAD
# threshold = 0.75  ← Partner B's version
# =======
# threshold = 0.5   ← Partner A's version (merged)
# >>>>>> main

# Choose which version to keep (delete conflict markers)
# threshold = 0.75  # Keep Partner B's version (or negotiate)

# Save, stage, commit
git add main_analysis.py
git commit -m "Resolve merge conflict: chose high threshold"
git push origin feature/threshold-high
# Now PR merges successfully!
```

---

## COLAB + GITHUB INTEGRATION

### Clone Repo in Colab

1. **Open Google Colab:** colab.research.google.com
2. **Create new notebook**
3. **First cell:**
```python
# Clone your GitHub repo
!git clone https://github.com/yourname/bootcamp-practice.git

# List files
!ls bootcamp-practice/
# Output: data_analysis.py, README.md, etc.
```

4. **Import & use your code:**
```python
# Add repo to path
import sys
sys.path.insert(0, '/content/bootcamp-practice')

# Import your function
from data_analysis import load_data

# Use it
# data = load_data('your_file.csv')
```

### Push Changes Back from Colab (Optional)

```python
# In Colab cell:
!cd /content/bootcamp-practice && git config user.email "your@email.com"
!cd /content/bootcamp-practice && git config user.name "Your Name"

# Make changes (create new file)
with open('/content/bootcamp-practice/new_analysis.py', 'w') as f:
    f.write("# Analysis from Colab\nprint('Hello from Colab')")

# Commit & push
!cd /content/bootcamp-practice && git add new_analysis.py
!cd /content/bootcamp-practice && git commit -m "Add Colab analysis"
!cd /content/bootcamp-practice && git push https://yourname:YOUR_GITHUB_TOKEN@github.com/yourname/bootcamp-practice.git main
```

**Note:** For push to work, you need GitHub Personal Access Token (PAT) instead of password.

---

## TROUBLESHOOTING QUICK FIXES

### ❌ "fatal: not a git repository"
```bash
# You're not in a Git project folder
# Solution: cd to your project folder first
cd ~/bootcamp_practice
git status  # Should work now
```

### ❌ "git config not set"
```bash
# You haven't configured name/email
# Solution:
git config --global user.name "Your Name"
git config --global user.email "your.email@gmail.com"
git commit -m "Try again"
```

### ❌ "Permission denied" during push
```bash
# GitHub authentication failed (SSH or HTTPS)
# Solution: Use HTTPS instead, GitHub will prompt for password
git remote remove origin
git remote add origin https://github.com/yourname/repo.git
git push -u origin main
```

### ❌ "Branch already exists"
```bash
# You tried to create a branch that's already there
# Solution: Switch to existing branch
git checkout feature/add-preprocessing
# (Instead of git checkout -b feature/add-preprocessing)
```

### ❌ "Merge conflict" (see scary markers)
```bash
# This is NORMAL; it means Git couldn't auto-merge
# Solution:
# 1. Open file in VS Code
# 2. Choose which version you want (delete conflict markers)
# 3. git add file.py
# 4. git commit -m "Resolve conflict"
# 5. git push
```

### ❌ "Changes would be overwritten by merge"
```bash
# You have uncommitted changes
# Solution: Save your work first
git add .
git commit -m "Save work before pulling"
git pull
```

---

## QUICK COMMAND REFERENCE (Clipboard-Ready)

```bash
# Initial setup (once)
git config --global user.name "Your Name"
git config --global user.email "your.email@gmail.com"

# Create repo
git init
git add .
git commit -m "Initial commit"

# Connect to GitHub
git remote add origin https://github.com/yourname/repo.git
git branch -M main
git push -u origin main

# Everyday workflow
git status                          # What changed?
git add filename.py                 # Stage specific file
git add .                          # Stage all files
git commit -m "Your message"        # Save to history
git push                            # Send to GitHub
git pull                            # Get latest from GitHub

# Branching
git branch                          # List all branches
git checkout -b feature/name        # Create & switch to new branch
git checkout main                   # Switch to main
git merge feature/name              # Merge branch into main

# View history
git log                             # Full commit history
git log --oneline                   # Short version
git log --graph --all --oneline     # Visual branch history

# Undo (be careful!)
git restore filename.py             # Undo changes to a file
git reset HEAD filename.py          # Unstage a file
git revert commit-hash              # Undo a commit (safe)
```

---

## FREQUENTLY ASKED QUESTIONS (FAQ)

**Q: What's the difference between `git add` and `git commit`?**
A: `git add` = "Mark these files for saving" (staging). `git commit` = "Actually save to history." Think: add = shopping cart, commit = checkout.

**Q: Do I have to use the terminal? Can I use VS Code GUI?**
A: Yes! VS Code Source Control panel does everything. Terminal is optional. Use whichever feels comfortable.

**Q: What if I mess up and make a bad commit?**
A: Don't panic. You can use `git revert` to undo it safely, or `git reset` to go back. Ask a TA; it's recoverable.

**Q: Can I switch branches with uncommitted changes?**
A: No (usually). Solution: `git add .` and `git commit` first, OR `git stash` to temporarily hide changes.

**Q: How do I delete a branch I don't need?**
A: `git branch -d branch-name` (local) or GitHub UI "Delete branch" button (remote).

**Q: What if my merge conflict looks scary?**
A: It's normal! Just choose which version you want, delete the conflict markers, save, and commit. TAs are here to help.

**Q: Can I use GitHub without the terminal?**
A: Yes. GitHub Desktop app (github.com/desktop) is a full GUI. Or use VS Code Source Control. Terminal is optional.

---

## KEYBOARD SHORTCUTS (VS Code)

| Action | Mac | Windows/Linux |
|--------|-----|---------------|
| Open Source Control | Cmd + Shift + G | Ctrl + Shift + G |
| Save file | Cmd + S | Ctrl + S |
| Open Terminal in VS Code | Cmd + ` | Ctrl + ` |
| Stage/Unstage in Source Control | Click + or - button | Click + or - button |
| Commit | Cmd + Enter (in message box) | Ctrl + Enter (in message box) |

---

## RESOURCES

- **Git Official Docs:** git-scm.com (comprehensive, technical)
- **GitHub Guides:** guides.github.com (beginner-friendly)
- **VS Code Git Docs:** code.visualstudio.com/docs/editor/versioncontrol
- **Troubleshooting:** Stack Overflow (search "[git error message]")

