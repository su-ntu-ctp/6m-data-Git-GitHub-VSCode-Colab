# **Version Control for Everyone: From Zero to Hero**

**Duration:** 3 Hours

**Format:** 20% Theory / 80% Hands-on

**Goal:** Empower non-technical learners to manage versions, sync work across devices, and collaborate using Git, GitHub, VS Code, and Google Colab.

Watch this intro video: [[Git & GitHub Zero to Hero]](https://youtu.be/1I79WAZ4uSU)

## **🎯 Learning Objectives**

By the end of this session, you will be able to:

1. **Explain** the difference between Git (the engine) and GitHub (the cloud).  
2. **Create** your first repository (project folder) on GitHub.  
3. **Connect** Google Colab to GitHub to save your work in the cloud.  
4. **Clone** a repository to your local computer using VS Code.  
5. **Execute** the "Golden Loop": Stage \-\> Commit \-\> Push.  
6. **Collaborate** using Branches and Pull Requests (Simulated Teamwork).

## **🛠 Prerequisites (Please complete before session)**

* **Accounts:** A free GitHub account (github.com) and a Google account.  
* **Software:**  
  * [Visual Studio Code (VS Code)](https://code.visualstudio.com/) installed.  
  * [Git](https://www.google.com/search?q=https://git-scm.com/downloads) installed on your machine.
  * If you have not done so, please revisit [First time installation](https://github.com/su-ntu-ctp/6m-data-1.0-Welcome-Onboarding/blob/main/installation.md) 
* **Mindset:** Don't worry if you break something. In Git, it is actually very hard to lose work permanently\!

## **🕒 Workshop Agenda**

| Time | Activity | Type |
| ----- | ----- | ----- |
| **0:00 \- 0:20** | **Module 1: The "Why" & The Cloud** | Theory (20m) |
| **0:20 \- 0:50** | **Exercise A: The Cloud Connection (Colab \+ GitHub)** | Hands-on (30m) |
| **0:50 \- 1:00** | **Module 2: The Mental Model (Local vs. Remote)** | Theory (10m) |
| **1:00 \- 1:45** | **Exercise B: The Workbench (VS Code Sync)** | Hands-on (45m) |
| **1:45 \- 2:00** | *Break* | Rest (15m) |
| **2:00 \- 2:10** | **Module 3: Collaboration Theory** | Theory (10m) |
| **2:10 \- 2:50** | **Exercise C: Teamwork Simulation (Pull Requests)** | Hands-on (40m) |
| **2:50 \- 3:00** | **Wrap Up & Next Steps** | Summary (10m) |

## **📘 Module 1: The "Why" & The Cloud (20 mins)**

### **The Concept**

Imagine you are writing a very important document. You save it as `Final.docx`. Then you change it and save `Final_v2.docx`. Then `Final_Real_v3.docx`. This is messy.

**Git** is like a time machine. It takes a snapshot of your folder every time you tell it to. You can travel back to any snapshot at any time.

**GitHub** is simply a website where we store those snapshots. Think of it like Google Drive or Dropbox, but specifically designed for tracking changes in text and code.

### **Key Terms**

* **Repository (Repo):** A project folder.  
* **Commit:** A save point (snapshot).  
* **Push:** Uploading your save points to the cloud (GitHub).

* ### **Google Colab**

* **Google Colab** (short for Colaboratory) is a free cloud-based platform for writing and running Python code in your web browser. Think of it as a notebook where you can write code, see results immediately, and save everything to the cloud without installing anything on your computer.

* **Why use Google Colab for data science?**

* * **No installation needed:** Just open your browser and start coding.
  * * **Free computing power:** Access to GPUs and TPUs for machine learning tasks.
    * * **Easy sharing:** Share notebooks with colleagues just like Google Docs.
      * * **GitHub integration:** Save your work directly to GitHub repositories.
        * * **Pre-installed libraries:** Common data science libraries (pandas, numpy, matplotlib) are already available.

## **💻 Exercise A: The Cloud Connection (30 mins)**

*Goal: Create a repo and save a file to it without installing anything locally yet.*

1. **Create the Repository:**  
   * Go to `github.com` and log in.  
   * Click the **\+** icon in the top right \-\> **New repository**.  
   * **Repository name:** `my-first-data-journal`  
   * **Description:** "Learning Git with DSAI"  
   * **Public/Private:** Public.  
   * **Initialize with a README:** Check this box (Important\!).  
   * Click **Create repository**.  
2. **Open Google Colab:**  
   * Open a new tab and go to `colab.research.google.com`.  
   * Click **New Notebook**.  
   * In the first cell, write a simple Python print statement or just text:

```python
print("Hello, GitHub! This is my first commit.")
```

   *   
     Run the cell (Shift \+ Enter).  
3. **Save to GitHub:**  
   * In Colab, go to **File** \-\> **Save a copy in GitHub**.  
   * A popup will ask for authorization. Click **Authorize googlecolab**.  
   * **Repository:** Select your `my-first-data-journal`.  
   * **Branch:** Keep it as `main`.  **Notice** If you didn't check "Initialize with a README" option in previous step, you will not see `main` in this step. 
   * **Commit message:** Type "Created notebook via Colab".  
   * Click **OK**.  
4. **Verify:**  
   * Go back to your GitHub tab. Refresh the page. You should see your `.ipynb` file there\!

---

## **📘 Module 2: The Mental Model (10 mins)**

*Goal: Sync VS Code with GitHub and master the "Golden Loop".*

Now we move from the cloud to your actual computer. This is where it gets interesting.

**New Key Concepts: Fork and Clone**

When working on a shared project, you will often encounter two related, but different, ways to get a copy of the code:

* **Fork:** This is a process on **GitHub** (the cloud) where you create a **personal copy** of someone else's repository on *your own* GitHub account. You use this when you want to contribute to a project you don't have direct write access to, or when you want to start your own project based on theirs. The original project remains untouched.

* **Clone:** This is the process of **downloading** a repository (your original, your fork, or any public repo) from GitHub to your **local computer** (where you work in VS Code).

Demo: Forking and Cloning for Collaboration

*Goal: Make a personal copy of a team's project and get it onto your local computer.*

## **💻 Exercise B: The Workbench (45 mins)**

1. **Fork the Repository (The Cloud Copy):**  
   * Go to the main project's GitHub page (e.g., [https://github.com/su-ntu-ctp/6m-data-1.0-Welcome-Onboarding](https://github.com/su-ntu-ctp/6m-data-1.0-Welcome-Onboarding)).  
   * Click the **Fork** button in the top right corner. This creates a full copy of the project under *your* GitHub account.

2. **Clone Your Fork (The Local Download):**  
   * Navigate to *your forked repository's* page on GitHub.  
   * Click the green **Code** button and copy the repository's URL.  
   * Open **VS Code**, (**For Windows:** Connect to WSL by clicking the bottom left "Open a Remote Window" button.)
   * Use the Command Palette (Ctrl+Shift+P or Cmd+Shift+P), and select **Git: Clone**.  
   * Paste the URL of your GitHub repository
   * Select a folder on your computer to save it (e.g., Documents).
   * Click **Open** when prompted.

There are three places your work lives:

   1. **Working Directory:** The files you are editing right now in VS Code.  
   2. **Staging Area:** A "waiting room" where you pick which files to save.  
   3. **Repository (Local):** The permanent record on your hard drive.

**The Workflow:** `Changes` \-\> **Add** (to Staging) \-\> **Commit** (to Repo) \-\> **Push** (to GitHub).

3. **Make a Change:**  
   * In the file explorer (left sidebar), right-click \-\> **New File**.  
   * Name it `notes.txt`.  
   * Type: "Git is a time machine." Save the file (`Ctrl+S`).  
4. **The Source Control Tab:**  
   * Click the icon on the far left that looks like a web of lines (Source Control).  
   * You will see `notes.txt` under "Changes".  
   * **Step 1 (Add):** Click the **\+** sign next to `notes.txt`. This moves it to "Staged Changes".  
   * **Step 2 (Commit):** In the message box, type "Added my first note". Click **Commit** (the checkmark or the 'Commit' button).  
5. **Sync (Push):**  
   * You will see a blue button saying **Sync Changes** (or a number next to the cloud icon at the bottom). Click it.  
   * *Note:* If it asks for a username/password, follow the browser prompts to authorize GitHub.  
6. **Verify:**  
   * Go to your GitHub webpage. Refresh. You will see `notes.txt`.

## **📘 Module 3: Collaboration Theory (10 mins)**

If we are all working on the same file at the same time, we might overwrite each other's work. To solve this, we use **Branches**.

* **Main Branch:** The "official" version of the project.  
* **Feature Branch:** A safe copy where you experiment.

When you are done experimenting, you make a **Pull Request (PR)**. This is asking the team: *"I have finished my experiment. Can we merge it into the main project?"*

## **💻 Exercise C: Teamwork Simulation (40 mins)**

*Goal: Create a branch, edit safely, and merge via Pull Request.*

1. **Create a Branch:**  
   * In VS Code, look at the bottom left corner. It likely says `main`. Click it.  
   * Select **\+ Create new branch...**  
   * Name it: `experiment-feature`.  
   * *Intuition:* You are now in a parallel universe. Changes here won't affect the `main` code yet.  
2. **Make a "Risky" Change:**  
   * Open `notes.txt`.  
   * Add a new line: "I am experimenting with a new feature here\!"  
   * Save, Stage (+), and Commit (Message: "Updated notes in branch").  
3. **Publish the Branch:**  
   * Click **Publish Branch** (the cloud icon).  
4. **The Pull Request (The Magic Moment):**  
   * Go to your GitHub repository page in the browser.  
   * You will see a yellow banner: *"experiment-feature had recent pushes."*  
   * Click **Compare & pull request**.  
   * Title: "Adding experimental notes".  
   * Click **Create Pull Request**.  
5. **Merge:**  
   * Now, pretend you are the manager. Review the changes on the screen.  
   * Click **Merge pull request**.  
   * Click **Confirm merge**.  
   * Delete the branch if prompted.  
6. **The Final Sync:**  
   * Go back to VS Code.  
   * Switch back to the `main` branch (bottom left corner).  
   * *Notice:* The text "I am experimenting..." is gone\! Why? Because your local computer doesn't know what happened on the cloud yet.  
   * Click the **Synchronize** icon (bottom left next to main) or use Command Palette \-\> `Git: Pull`.  
   * Watch the text appear. You have successfully collaborated with the cloud\!

## **🎓 Wrap Up & Final Thoughts**

You have done it\! You have gone from zero to a full collaborative workflow.

**Recap of commands (VS Code GUI equivalent):**

1. **Clone:** Download from Cloud.  
2. **Stage (+):** Prepare for photo.  
3. **Commit:** Take the photo.  
4. **Push:** Upload to Cloud.  
5. **Pull:** Download updates from Cloud.

Keep practicing. Create a repo for your next project, even if it is just a grocery list or a personal journal. The more you use these tools, the more natural they will feel.

Thank you for joining me\!
