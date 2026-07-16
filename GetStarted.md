# GetStarted.md

## A one-hour setup session for your group

Do this **together, in one room, at one time**, with everyone's laptop open. It takes about an hour. Do not try to do it over text message across three days. The steps depend on each other, and doing them out of order is how groups break their repository in week one.

By the end of this session your group will have a repository, everyone will have made their first commit, and everyone will have opened and merged their first pull request. That's the whole goal. You are not doing any project work today.

---

## Part 0: Before you start

### Pick your letters

Sit down and decide, out loud, right now:

- **Student A** — creates the repository and merges everyone's work. Pick someone whose laptop is charged and whose GitHub account already exists.
- **Student B**
- **Student C**
- **Student D**
- **Student E** — skip if your group has four people.

Write the letters down on paper with names to help you remember who is who. The rest of this guide refers to you by letter.

### Everyone: Get an account (if you don't have one)

If you don't have a GitHub account, make one now at <https://github.com/signup>.

Use a username you'd be willing to show an employer. You are going to be living in this account for the rest of the semester.

### Everyone: install two programs (if you haven't already)

You need **git** (the program that tracks changes) and **gh** (GitHub's command-line tool). You will use `gh` exactly once, in the log-in step below, to connect your laptop to your GitHub account. Every other interaction with GitHub in this guide is either a `git` command or a click on the GitHub website.

**On macOS**, open the Terminal app and run:

```
brew install git gh
```

If that says `brew: command not found`, install Homebrew first from <https://brew.sh>, then run the command again.

**On Windows**, install [Git for Windows](https://git-scm.com/download/win) and [GitHub CLI](https://cli.github.com). Then open **Git Bash** (not Command Prompt, not PowerShell) for everything below.

**Check that both worked.** Everyone run these two commands:

```
git --version
gh --version
```

Each should print a version number. If either says "command not found," stop and fix it before going on. Do not let one person get left behind here.

### Everyone: tell git who you are (if you haven't already)

Git stamps your name and email on every commit you make. If you skip this, your commits will be labeled with something useless like `root@laptop.local`, and we will not be able to tell that the work is yours.

Run these three, with **your own** name and email:

```
git config --global user.name "Beth Chen"
git config --global user.email "bchen42@wisc.edu"
git config --global init.defaultBranch main
```

**Important:** the email must be one that's on your GitHub account. Check what's on your account at <https://github.com/settings/emails>. If the email here doesn't match one there, GitHub won't connect your commits to your profile, and you'll appear to have done nothing.

### Everyone: log in (if you haven't already)

```
gh auth login
```

It will ask you several questions. Answer:

- **What account?** → GitHub.com
- **Preferred protocol?** → HTTPS
- **Authenticate Git with your GitHub credentials?** → Yes
- **How would you like to authenticate?** → Login with a web browser

It shows you an eight-character code. Copy it, press Enter, paste the code into the browser window that opens, and approve. Come back to the terminal when it says you're logged in.

Everyone do this now. Wait until all five of you are done.

---

## Part 1: Student A creates the repository

**Only Student A does this part.** Everyone else, watch A's screen.

1. Create a new repository on GitHub.
2. Set it to **Public**. (Never put passwords, API keys, or private data in this repo.)
3. Click **Create repository**.

### Student A: add everyone else

Still on the new repository page:

1. Click **Settings** (top of the page).
2. Click **Collaborators** in the left sidebar.
3. Click **Add people**.
4. Type each teammate's GitHub username, one at a time, and add them.

**B, C, D, and E:** check your email now. GitHub sent you an invitation. Click the link and accept it. You cannot do anything else in this guide until you accept.

### Student A: add the instructor

Add **[INSTRUCTOR: paste the instructor/TA GitHub username here]** as a collaborator too, the same way. Do this today, not later.

### Student A: Copy template files

1. Copy `contributions.md` to your new repository
2. Copy `README.md` to your new repository
3. Revise away templated placeholders in both files.

### Student A: read the repo's address out loud

The address looks like:

```
https://github.com/STUDENT-A-USERNAME/ds-final-group07
```

Everyone write it down. You'll need it in ten seconds.

---

## Part 2: Everyone downloads a copy

**All five of you do this**, at the same time.

Pick a place on your laptop where you keep schoolwork, and go there:

```
cd ~/Projects
```

Now make your own copy of the repository (use your real repo address):

```
git clone https://github.com/STUDENT-A-USERNAME/ds-final-group07.git
```

Then step into the folder it just made:

```
cd ds-final-group07
```

Check that it worked:

```
ls -lhra
```

You should see `README.md` and the other course files. If you do, you now have a full copy of the repository on your laptop. Everyone confirm out loud before moving on.

---

## Part 3: The loop

Here's the pattern for the rest of the session. Each student in turn adds their own row to the members table in `README.md`. **One person at a time, in letter order.**

> ### The one rule that matters
>
> **Wait your turn, and pull before you start.**
>
> You are all editing the same three lines of the same file. If two of you work at the same time, git will not know whose version is right, and you'll get a *merge conflict* (which is fixable, but not what you want in your first hour).
>
> Student B goes completely, start to finish. **Then** C starts. Then D. Then E. Then A. Or course also execute a pull request and merge between each student's efforts. To avoid the conflicts, nobody starts their turn until the person before them is merged and A says "go."

### Your turn: the six steps

When it's your turn, run these. The example is Student B; use your own name.

**Step 1 — get the latest version.**

```
git fetch
git pull
```

The commands `git fetch` and `git pull` download whatever your teammates have already merged. Skipping this is the single most common way to create a mess.

**Step 2 — make your own branch.**

```
git switch -c add-beth-chen
```

A branch is your own private workspace. Nothing you do here touches anyone else until you ask for it to.

Name it `add-yourname`, all lowercase, hyphens instead of spaces.

**Step 3 — edit the file.**

Open `README.md` in whatever editor you like. Find the members table near the top. It looks like this:

```
| Name | GitHub username |
|---|---|
| | |
| | |
```

Fill in **one** empty row — yours — with your real name and your GitHub username:

```
| Name | GitHub username |
|---|---|
| Beth Chen | bchen42 |
| | |
```

Leave the other rows alone. Save the file.

**Step 4 — save your change to git.**

```
git add README.md
git commit -m "Add Beth Chen to members table"
```

`git add` says "this is the file I changed." `git commit` says "save this change, with this description." The description in quotes is a *commit message.*

**Step 5 — send your branch to GitHub.**

```
git push -u origin add-beth-chen
```

Your branch now exists on GitHub. Your change still isn't in the main version. Currently, it's sitting in a side room, waiting to be let in.

**Step 6 — open a pull request on the GitHub website.**

Go to your repository page on github.com and refresh it. GitHub will show a banner near the top saying your branch had recent pushes, with a green **Compare & pull request** button. Click that button, type a short description of what you did (the commit message is a fine default), and click **Create pull request**.

A pull request is a formal request to merge your work into the main version. Once created, the pull request has its own URL in your browser's address bar — copy it and share it with Student A so they can review.

Your turn is over. Now A takes over.

### Student A: review and merge

Every time a teammate finishes step 6, then Student A does this.

Review the pull requests on the GitHub Website. **Look at what they actually changed using the "Files changed" tab.**

Green lines with `+` were added. Red lines with `-` were removed. **Actually look.** You are checking two things: did they add their own row, and did they leave everyone else's alone? This takes five seconds and it is the entire point of a pull request.

**Let it in:**

On the GitHub website, click the "Merge pull request" button. If it asks whether to delete the local branch, say yes.

Now say "go" to the next student, out loud. They will pull your merge down in their step 1 and build on top of it.

---

## Part 4: Student A's turn

Student A goes last, and Student A does **not** merge their own work. Somebody else has to read it (that's true for the rest of the semester too).

**Student A:** Do the six steps in Part 3 exactly like everyone else, with your own name.

**Student E** (or D, in a group of four): you merge Student A's pull request. Again using GitHub website, click the "Merge pull request" button.

Congratulations — the last person to touch the repo today wasn't the landlord.

---

## What today established

- **Student A owns the repository.** A created it and can add or remove people. That's a chore, not a rank. A is not the boss of this project.
- **Nothing reaches `main` without a pull request.** Not even A's work. Someone other than the author looks at every change before it lands.
- **Every one of you has a working setup.** Git is installed, you're authenticated, your commits carry your name, and you've been through the whole loop once on a change that didn't matter.
