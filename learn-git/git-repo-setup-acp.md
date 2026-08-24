# Git Programming Concepts Covered

Today is about VCS, a version control system.

Repository is often called a repo.
When we don't use versioning - We are essentially Bloating the file system, when
we can actually have only one file that we can roll back to any of the previous
versions of the file or file system.

What is a hotfix? and why is it important to have commits to follow the git pushes
to production? So that we can track all changes. ref ACP 

Programming and GitHub is not a memorization task, you can memorize pieces of it. Creating apps,
is an intangible process, using your words and your thought process to make things
happen. Using git will become easy through muscle memory. Git feels tough, and
then it will be like wow I forgot about git hub, and you will just do it. Because
you have done it so many times.  

The idea we are working towards is collaboration against my code base is the
conceptual understanding.

## Lets Start here students.

|                        | Git                        | GitHub                              |
| ---------------------- | -------------------------- | ----------------------------------- |
| **What it is**         | Version control software   | Online platform                     |
| **Where it runs**      | On your computer           | In the cloud                        |
| **Main purpose**       | Track changes to code      | Store and share Git repositories    |
| **Internet required?** | No                         | Usually, yes                        |
| **Examples**           | `git commit`, `git branch` | Pull requests, Issues, code reviews |


GitHub allows developers a shared space to work on the same projects. It connects people, code, and ideas so developers can build together, see each other’s changes, and continuously improve the same codebase. *** That’s the whole point of using GitHub: to make collaboration on software simple, organized, and accessible to everyone on the team. ***


## Any questions that are not covered in class can be addressed in Teams/Slack/Zoom, after class

## White board A C P process  

┌──────────────────┐
│  Make Changes    │
│  to Your Code    │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│      ADD         │
│   git add .      │
│                  │
│ Stage your       │
│ changes          │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│     COMMIT       │
│ git commit -m    │
│ "message"        │
│                  │
│ Save a snapshot  │
│ of your changes  │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│      PUSH        │
│   git push       │
│                  │
│ Upload commits   │
│ to GitHub        │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│      GITHUB      │
│                  │
│ Remote repository│
└──────────────────┘

## show when and where git status (check to make sure it worked)

did I add things, did I commit, did it push correctly, and are all branches up
to date.

## Step one go to Git Hub . com

Explain repositories.
Most people have one project per repo.
Description shows up on repo page.

## Notes on Terminals  

Can you blow up your computer no.
Can you delete everything on your pc, possibly.

## git is a base command that we always use

## now create the scaffolding

Starting with the touch sample.txt, we can create any file we wish and git will
track it, So, run git status. The fact that git shows the file we created as
Untracked file.

### git push origin master

git push - push to github
origin - means where to? it was the url we provided initially.
master, is the main branch. and let it live there.

Remind what was our goal?
to make a repo,
pull it down
add a file
push that file back up to git hub

### show what git hub looks like now

This is the accountability, we need and get from github.
hackyness equals duct tape, run a git blame. ? git and github allows us to take
and have accountability.
Promotions can come from showing work that you can do, employees can see that you
are performing at or above, what is required.

## So what we will do now

This class has two purposes complete 201 pre-work, we are now ready for success.
The second is to give you some exposure, mostly try as much as you can and understand
the conceptual side of what we are doing. So, that in week 2 of 201, when we start
objects, you may not know what that is, but you will by then have started to
build heuristics when it comes to what you have previously covered.

Going to do this two more times, going to talk a bit in this second run and I am
going to talk very little and more even more quickly.

cd ~ takes me to my directory directly.

code . open up vs code.

## keep bash clear and keep it up at top so students can see what you are typing

use git touch to create files, to avoid app scaffolding ending up in the wrong
location and messing up the application.

## Commit messages should not contain swear words, to be professional

and communicate the work you did properly

So your job, is to pull down repo, update it and push it back up.
So, I will delete my old one, and create one more quickly, to show you the flow.
and then you will have 30 minutes with the help of the TA's to work through your
lab assignment.
I did it quickly and efficiently and didn't really have to think about it. In fact,
there will be shortcuts that you learn, that will be added in to your flow as you
go. We need to know the why, what, and how and be able to ACP to master. within
the next month.

### Read through the assignment lab

stress that the acp is happening, and use the learning journal as our practice repo, add
something but pay more attention today to the ACP process.

### I will check back in with 15 minutes left to go

Do not be afraid, to ask what step one is. The model is to confirm what we learn
not on the day that it is taught, but over time as learning continues it will
become apparent what you know and what you don't.

Look in slack or Teams at the series of steps.

#### Step 1 - Navigate to your git learning journal repo

#### Step 2 - Clone your repo down onto your local machine. git clone github-repo-url.git

#### Step 3 - cd into your repo: cd ~ to get to your home directory then, cd github-repo-name

#### Step 4 - run code . to open your learning journal in VS code

#### Step 5 - make some changes to your README.md

#### Step 6 - ACP time - start with adding your changes git add README.md

#### Step 7 - commit changes git commit -m 'add message with relevant commit information'

#### Step 8 - push your changes to GitHub. git push origin master

If you weren't able to push code that's ok, we will go through next why and then
as a group we will get there. some may not be able to do code . to work, and we
get those things taken care of next time.


