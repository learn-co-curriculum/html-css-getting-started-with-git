# Getting Started with Git

Now that you've learned some of the fundamentals of HTML, let's switch gears and talk more about version control. You've heard the words Git and Github in prior lessons, but in this unit we're going to take a much deeper dive into the topic so that you can continue to work and use your computer in the same way that experienced programmers do. 

Git is a powerful file version control system. It gives us a history to track progress on files so that we can rewind or fast forward to a specific moment in time allowing us access to previous versions of a file. It is kind of like the best undo button you will ever learn. Git also allows us to make backups of our code, as well as easily share code or collaborate on code with others. Git is the current industry standard for version control and code collaboration. Most companies hiring for developers expect a thorough understanding of Git. As a beginner, Git requires a lot of memorization to learn the necessary commands and work flow. This is something you will pick up throughout the course by using Git commands to complete all labs and assignments. Not to worry if it takes a while to get the hang of it. This is typical. You will most likely be surprised that by the end of the course you will speak fluent Git.

## Objectives

1. Explain what Git is and the benefits of using version control
2. Set up folder with README.md file
3. Initialize a new repository
4. Check for changes in the status of files and folders
5. Stage and commit changes
6. Log commits
7. Reset to a particular commit

## Git, A Wonderful Version Control System

Watch the videos below if you are unfamiliar with Git. We will be using Git to access course materials and to share and collaborate on project code throughout this course. After watching the video you may use the text below to review all of the topics discussed in the video.

**Note** that the video uses your computer's terminal, but in this course, you'll be using the Learn IDE and all Git commands will work the same way on it as it does on your terminal.

However, the video will ask you to open files using `subl .` This will not work with the IDE and so any time you are asked to open a file use `atom` + the file name.

<iframe width="640" height="360" src="https://www.youtube.com/embed/videoseries?list=PLj148bJp5wixQ3lA28anBxxdnq5fKTqWg" frameborder="0" allowfullscreen></iframe>

### What Is Version Control?

According to Wikipedia, "version control is the management of changes to documents". What we get from version control is the ability to track changes in our code. Git is (currently at the time of writing this) the most popular version control software for programming. Aside from versioning our code git also provides tools to backup our work by transporting our code via uploading (pushing) and downloading (pulling) to and from remote servers. Throughout the course we will be using the website Github.com to store our code assignents for the purpose of backup, collaboration, and to submit assignments using pull requests (more on this a bit later).

### Why Use Version Control?

Let's think about the future for a second. It's a year or two down the road, and you're working at your dream job (YAY!). You just deployed a new chat feature for the app you're working on. Suddenly, your boss runs over to your desk. "Wait! We can't deploy the chat yet! Revert! Revert!"

What do you do? You need to find all of the new code you pushed to the server and delete it. Then you need to find the old code, test it and re-upload it. So much work to do. Well, since you used version control software, it's as easy as 123. Actually, it's as easy as `git reset --hard <commit id>`... but we'll get to that later. Using version control is useful because it allows you to easily rollback to a previous version of your application, saving you a ton of extra work and time.

There are a lot of advantages to version control. It's great way to keep a backup of your work, it facilitates collaboration, and gives you the freedom to experiment and try new things without messing up the code base.

### Starting A New Project

Let's start by making a new folder for our code project. In the terminal are of the Learn IDE, we'll type `mkdir simon-stamp-collection`. Then we will cd into that folder `cd simon-stamp-collection`. This folder is empty so let's create a new file: `touch README.md`. README files are a commmon additon into open source code projects. They give a descrition of the project and any details for others browsing your code.

Next, make sure that the file is open in the code editor area of the IDE. Now lets type in some text in Markdown format.

```markdown
Simon's Stamp Collection App
---

# About

Stuff about Simon's Stamps here...
```

Markdown is the preferred format for writing README files. It is pretty easy to learn. You will most likely pick it up naturally throughout this course. Although its not neccesary at this point, if you wish to learn the specifics of the Markdown syntax, then after this lesson feel free to browse the resource link provided below. By the way...all of these lessons are actually written in Markdown, pretty neat huh?

Next we save, and head back to Terminal...

### Initializing A New Git Repository

Now we will fire up a new git repository in this folder by typing `git init`. This initializes a new repository.

### Status

Now that we have new git repository we can begin to use git commands. The first we will look at is a command that allows us to check our current status, or in other words the current state of our code. This command will tell us if there have been any modifications to any files git is tracking, as well as if any new files are not being tracked among other things. To get our current status we type: `git status` This returns the following response:

```shell
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

    README.md

nothing added to commit but untracked files present (use "git add" to track)
```

This tells us that there is a new file `README.md` that is currently not staged or another words that is not being tracked for changes.

### Staging

In order to include a file to save its progress we need to create commits. A commit is a save point for a file, very similar to taking a snapshot the same way you would with a camera. In order to save commits we need to first tell git which files we wish to include in our commit, or in other words we have to move certain files into the view of our camera. Selecting files to be part of a commit is known as staging. Let's stage our README.md file like so: `git add README.md` and then press return. When staging files we use the "add" command. This command accepts multiple filenames separated by spaces if you wish to stage multiple files at once, or to stage all current changes in the folder you are in you can use `git add .` as a shortcut.

### Commiting

Now that we have staged our `README.md` file we would like save the progress on that file by commiting. Going back to the camera analogy, using `git add` to stage is like moving the files in view of a camera, where as commiting is like actually pressing the button to take the picture. To take a snapshot of our current state of README.md we now type: `git commit -m "add a README with some info text"` and then press return. Here the commmit command is followed by the `-m` flag which stands for message. Following this is our message for the commit in quotes `"add a README with some info text"`. This message is stored with each commit giving us a description of the state of the code if we were to go back to the commit at a later point in time. Usually commit messages are written in present tense for this reason.

Let's make some more changes on our README.md file. Bring the file back up in your code editor, and change the text "About" to "About Simon" instead and save.

```markdown
Simon's Stamp Collection App
---

# About Simon

Stuff about Simon's Stamps here...
```

Now back in Terminal let's stage and commit our changes. Type `git add README.md` press return and type `git ci -m "update About headline in README"` and press return. Now we have two unique commits. The first has saved a snapshot of our code in the README.md file with the initial text we added, the second commit saved a snapshot with the change to the "About" headline.

### Log

Hey, wouldn't it be great if we could list all of our commits to see a record of all our progess? This is accomplished using the log command. Let's type: `git log` and then press return. This returns a repsonse similiar to:

```shell
abe211d update About headline in README (jongrover, 10 seconds ago)
6d81119 add a README with some info text (jongrover, 2 minutes ago)
```
Depending on how many commits you have saved this list may fill the screen. If so, you can use the down arrow to scroll through them and type `q` and hit return to quit out of the log if you get stuck. In my case I have just one commit so git exits the log automatically when it reaches the bottom of the log. The first set of numbers and letters is the SHA key, this is a unique id git uses to identify this commit. Following the SHA our commit message we typed in. After that we see the github user who made the commit and how long ago the commit was made.

### Reset

What if we wanted to go back to the moment in time before we had updated the "About" heading? We can check out and reset back to previous commits by using the reset command. To reset to a particular commit we miust make a note of that commits SHA key. Refering to the code block above we can see that running the `git log` command displays a list of our commits and all their respective SHA keys. In our case we wish to revert back to the commit from two minutes ago where we "add a README with some info text" we note that the corresponding SHA key is "6d81119". Now we can type in the command `git reset --hard 6d81119`. Note that your SHA key will most likely be different from mine. This will take us back in time to when our file looked like this:

```markdown
Simon's Stamp Collection App
---

# About

Stuff about Simon's Stamps here...
```

It is worth noting that reseting with the `--hard` flag will remove the commits after the one you reset to, so all new commits will be continuing on from that point. If for some reason you want to go back to a previous commit without losing the commits after it then you can instead use `git checkout <SHA key>` inserting the desired SHA key for the commit you want to travel to.

To get back to our latest commit form 10 seconds ago "update About headline in README" we can type in `git reset --hard abe211d`. Now are code look slike this again:

```markdown
Simon's Stamp Collection App
---

# About Simon

Stuff about Simon's Stamps here...
```

## Summary

- Git allows us to track changes in our files.
- Use the `git init` command within your project folder to initialize a new git repository.
- To stage files use `git add <file>` command or `git add .` to add all files in the current folder.
- To commit use `git commit -m "your message"`.
- The command `git log` will display all commits and their corresponding SHA key.
- `git reset --hard <SHA key>` will allow you to move forward or backward to the state of the code at a particular commit.

## Resources

- [Wikipedia - Version Control](https://en.wikipedia.org/wiki/Version_control)
- [Wikipedia - Git](https://en.wikipedia.org/wiki/Git_(software))
- [Interview With Linus Torvalds the Creator of Git](http://www.linux.com/news/featured-blogs/185-jennifer-cloer/821541-10-years-of-git-an-interview-with-git-creator-linus-torvalds)
- [Git Docs - Init](https://git-scm.com/docs/git-init)
- [Git Docs - Add](https://git-scm.com/docs/git-add)
- [Git Docs - Commit](https://git-scm.com/docs/git-commit)
- [Git Docs - Log](https://git-scm.com/docs/git-log)
- [Git Docs - Reset](https://git-scm.com/docs/git-reset)
- [Git Cheatsheet](https://www.git-tower.com/blog/content/posts/54-git-cheat-sheet/git-cheat-sheet-large01.png)
- [Git Best Practices](https://www.git-tower.com/blog/content/posts/54-git-cheat-sheet/git-cheat-sheet-large02.png)
- [Markdown Tutorial](http://markdowntutorial.com/)
- [Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
<p class='util--hide'>View <a href='https://learn.co/lessons/html-css-getting-started-with-git'>HTML CSS Getting Started with Git</a> on Learn.co and start learning to code for free.</p>
