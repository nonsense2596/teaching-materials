# Git

Before g~~e~~itting into git, let's start with adding VSCode into the path if not already there.

> You can check whether it is on the path already by typing ```code``` into the terminal. If it opens, then cool :)

> [Here](cmd-basics.md/) under section 1.6, we have already discussed how to add things to Path.

The default VS Code installation location is usually ```C:\Users\USERNAME\AppData\Local\Programs\Microsoft VS Code\bin\``` that's what you have to add there replacing USERNAME with your actual username.

Following that, we can set the default git editor to VS Code escaping vim (hah!).

```
git config --global core.editor "code --wait"
```

Afterwards now the VS Code window will open, where we can set the rest of the operations to VS Code as well. Modify your configuration according to the values below.

```
[merge]
  tool = vscode
[mergetool "vscode"]
  cmd = code --wait $MERGED
[diff]
  tool = vscode
[difftool "vscode"]
  cmd = code --wait --diff $LOCAL $REMOTE
[core]
  editor = code --wait
```

From then on, various git commands normally requiring a text editor will open in a VS Code window providing a nicer environment than the default terminal editor.

# 1. Git fundamentals

Starting from the very basics this time. You set up the git environment last week, but let us quickly check it.
In git bash, type

```
cat ~/.gitconfig
```

and if your user name and e-mail address is present, it should probably be fine now.

## 1.1 Creating a repository, adding files

First let's create a folder called git_project_1 and enter it.

```
mkdir git_project_1
cd git_project_1
```

Once inside that folder, fundamentally there are two different ways to create a new git project. We can either create it online on a git portal like GitHub or locally through either the command line or visually in other programs.

> Along this course, we will continue to use the command line for git, but feel free to try recreating all the steps in your favourite editor later as an additional exercise!

The following command initialises a git repository on the current working folder:

```
git init
```

![gitinit](https://i.imgur.com/PDoW9n6.png)

If you see something like the image above, then you were successful. It created a hidden folder called ```.git``` in the current working directory. We can check it out with ```ls -la```.

Now that git is initialised, we can start working on our new project adding and committing files.

First, let's create a file called ```script.js```.

```
touch script.js
```

Now if we were to check the status of git here:

```
git status
```

![gitstatus](https://i.imgur.com/zd8oO1g.png)

we would see that it says "untracked files: script.js".
Git automatically detects files added to this directory, but we have to manually add them for git to track and store them in version control. Do as the prompt says and add the script to git.

```
git add script.js
```

Create aother file called ```index.html```.

```
touch index.html
```

![indexgit](https://i.imgur.com/gYkjgbz.png)

Now we see that ```script.js``` by now is tracked by git since we added it, but ```index.html``` is not yet.
We can also add multiple files or folders (or everything that is not specified to be ignored by .gitignore) with git add:

```
git add .
```

Checing the status again we should see, that both files are listed under the "changes to be committed section".


## 1.2 gitignore

There is one more important thing we should look into before having our deep dive into commits and the rest.

Consider a case where we have some local file filled with secrets.

Something like the following. Create it and optionally add something inside.

![secrets](https://i.imgur.com/4y1xtNf.png)

Either these, or module or plugin codes that would be installed anyway from some file specifying which ones are used.

Surely we do not want to save all these to git as well?

![nodevendor](https://i.imgur.com/WPkzWpb.png)

A solution to this; namely to ignore and do not add specific files or folder to the git versioning system is gitignore. That is usually one of the first thing we do when creating a git repository and many IDEs automatically do it for us too.

Create the ```.gitignore``` file and add our example ```secret``` file inside and lastly add ```.gitignore``` to git as well.

```
nano .gitignore
```

put a single line with the following inside: ```secret``` then add ```.gitignore``` to git.

```
git add .gitignore
```

> Check out how to use nano [here](cmd-basics.md/).

![gitignore2](https://i.imgur.com/I7ZUp7L.png)

Once again, if everything went correctly, you should see the result above. ```.gitignore``` added, but no sign of the ```secret``` file either in the tracked or committed sections.

## 1.3 ~~git~~ get committed

Commit is one of the core command of git. It records changes from the repository, effectively capturing a snapshot of it's current state. It's usage is very simple.

```
git commit
```

or

```
git commit -m "initial commit"
```

Every commit has to have a commit message. With the ```-m``` option we can supply it right there at the command line. If we do not do it, simply typing ```git commit``` git will launch a text editor where we are prompted to enter one.

![gitcommit](https://i.imgur.com/Warx9rk.png)

## 1.4 setting up GitHub

Everything we have seen so far has been local to our computers. By connecting our project to a remote source (like GitHub or GitLab) you can easily share and collaborate with others.

For GitHub to work, we need to set up ssh keys.
Luckily we can easily set it up using the command line and GitHub.
Run the following command:

```
ssh-keygen
```

The default path it saves the key pair to is ```~/.ssh/```. If prompted just press ```enter```.

> If the key already exist, just press ```n``` when it asks you whether you want to overwrite it.

Then we need to copy the public key. You can either open it from your favourite editor, or from the command line as we usually do it.

```
cat ~/.ssh/id_rsa.pub
```
and copy the whole thing from here including the starting "ssh-rsa thentherandomcharacters".

Open the following URL: [Github settings / SSH and GPG key](https://github.com/settings/keys)

![ssh](https://i.imgur.com/9Pu71Mu.png)
For the title you can add anything, and paste the copied key down in the Key field - save it and we are done.

## <a name="creatinggithubrepo" style="text-decoration:none">1.5 creating an empty repository on GitHub</a>

Just find the ```new``` button somewhere. :)
Alternatively use [this link](https://github.com/new).

For now, just add a name as it is the only field required - leave the rest - then press "Create repository".

Under the "Quick setup" section, click on the "SSH" button to change the links to SSH style.

> You see two options on that page, which ones do you think we should use?

## 1.6 using GitHub, pushing and pulling an existing repository

A version control system is usually collaboratively used my numerous people from numerous computers. With git, we can synchronise between these computers, and a central server.

We call the server ```remote``` and the git repository on our machine ```local```. We can have multiple remotes as well, but usually have one. The default remote is called ```origin```.

Now, we add a remote to our local repository:

```
git remote add origin <YOUR GIT URI>
```

Where \<YOUR GIT URI\> looks something like this:
```git@github.com:username/projectname.git```.

Having it added, we can now push our changes to the remote repository on GitHub. For that to work, we also have to set the upstream as well. Luckily we can do that at the same time.

```
git push -u origin master
```

Here we push our ```master``` branch to ```origin``` (so the remote master) and also set ```origin``` as ```upstream```.

![upstream](https://i.imgur.com/QydTWan.png)

If we refresh GitHub in our browser, we will be able to see our files and commits there too.

![githubrepo](https://i.imgur.com/T8VSWnN.png)

Continuing with the basics, in a corporate environment you will collaborate with other developers on the same project, or even on the same branch of a project. Alternatively you just switching between two devices doing the work yourself. We need a way to get changes from the server. That's what pulling is for.

```
git pull
```

If we were to have changes upstream, this command would download them. In our case, we don't have any so the command would have no effect.

![pull](https://i.imgur.com/gikaVJN.png)

> It is recommended to always pull before push.

Let's add a README.md as GitHub suggests it. Just click on it, leaving everything empty and clicking on ```Commit new file``` at the bottom.

> Usually editing files online is not advised.

> You may have noticed, that editing and adding the README.md file on GitHub also created a commit. A commit that we do not have locally.

Now we can actually have some changes in the remote that we can pull.

![pull2](https://i.imgur.com/B4gUKp5.png)

And with that, our README.md file also appears locally now.

## 1.7 cloning a GitHub repository

Alternatively, as it was previously discussed, we can also create a git repository on GitHub then clone it locally setting it up this way.

Let's create a new repository on GitHub as detailed in [section 1.5](#creatinggithubrepo).

Once we created it, clone it down

```
git clone <YOUR GIT URI>
```

> It will automatically create a folder with the name of the git repository at your current working directory. Enter it with ```cd``` then just as before, we can do the usual shenanigans like creating, adding and modifying files inside the repository as well as committing and pushing the changes to the remote.

Let's do exactly that!

```
touch file1.txt file2.txt file3.txt
git add .
git commit -m "created files"
```

We created three files, added them all to git then committed the changes.

Let's create another commit.

```
touch file4.txt
git add file4.txt
git commit
```

If the ```-m``` option is not supplied, git will open our default editor (which at this point should be VS Code) for us to enter a multi-line commit message.

![vscodegitmessage](https://i.imgur.com/1atDfcb.png)

Having it saved and VS Code exited, git will pick up the changes made in the temporary file ```COMMIT_EDITMSG``` and set that as such.

![vscodecommitsuccess](https://i.imgur.com/vyLxucb.png)

## 1.8 log, diff and useful tidbits

Just as with ```git status``` we were able to see the current branch and the working tree, tracked and modified files; with ```git log``` we can see the history of the commits with the most recent commit being at the top.

```
git log
```

![gitlog](https://i.imgur.com/xBcXQFb.png)

And with ```git diff``` we can see the changes made in files that are not yet committed. To reproduce it, just edit any of the files, deleting and adding lines after the last commit.

```
git diff
```

![gitdiff](https://i.imgur.com/eOtIOZx.png)

## 1.9 partial commits

Before going into branching, one last thing that is worth to mention is partial commits. It is a useful tool when we want to commit only a part of a file.

Create a new file called "partialtest.txt" with the following contents:

```
one
two
```

> Add it to git and commit it yourself.

<details>
    <summary>solution (<i>click to expand</i>)</summary>

```
git add partialtest.txt
git commit -m "added partial test file"
```
</details>

Open it again, and add the following to lines to the bottom of it:

```
three
four
five
```

We have a way to stage (mark some file to go into your next commit) only certain parts of a file.

```
git add -p partialtest.txt
```

You will then see something along the lines of the picture below. It is very similar to when we looked at the changes of a file with ```git diff```. Here you can see the green (or red) lines marking added, removed or otherwise modified lines.

![hunkdiff](https://i.imgur.com/KJMbPrx.png)

> You don't have to memorize what all those characters mean, pressing ```?``` explains them.

What we need now is pressing ```e``` to select specific lines to commit. It will open our default git editor (which we set up to be VS Code).

![hunkvscode](https://i.imgur.com/ovUZCAW.png)

In VS Code we can specify which lines to add. As the comment in green says, with a plus (+) sign we can add a line to the file, and with a minus (-) sign we can delete a line.
If we simply delete (or comment out with #) a line here, then it will not be added to the commit.

Let's do that, only adding the line "three" to the commit leaving the rest of the file in a "has changes but not staged for commit" mode.

![hunkvscodeedit](https://i.imgur.com/zsuwKXG.png)

Closing the file and exiting out of VS Code, look at the changes with ```git status```.

```
git status
```

![githunkchanges](https://i.imgur.com/Vx1QHBT.png)

```partialtext.txt``` appears both at the "changes to be commited" and the "changes not staged for commit" sections. Precisely because we told git, to only commit a single line from its contents.

This is then further confirmed when we commit the changes where git will show that "1 file changed, 1 insertion(+)".

```
git commit -m "partial commit"
```

We can also check out "partialtext.txt".

```
cat partialtext.txt
```

Again, we woul,d see that all the lines we previously added are still there, however we know that to the previous commit we only added one of them.


# 2. Branching out