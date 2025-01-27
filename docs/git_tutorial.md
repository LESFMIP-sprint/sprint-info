# Collaborating with Github

## A quick background

* git init - initalise a Git repository
* git add - adds new changes to the staging area
* git commit - commits changes in the staging area to the repository
* git log - show list of commits
* git push - pushes commits to a remote (e.g. github)
* git pull - pulls changes from a remote

![Diagram illustrating the Git staging area and repository](https://noc-oi.github.io/git-novice/fig/git-staging-area.svg)

## Collaborating with Github

Github allows multiple people to work on the same code.

### Multiple Collaborators to One Repository

The Owner needs to give the Collaborator access. In your repository page on GitHub, click the "Settings"
button on the right, select "Collaborators", click "Add people", and
then enter your partner's username.

![screenshot of repository page with Settings then Collaborators selected, showing how to add Collaborators in a GitHub repository](https://noc-oi.github.io/git-novice/fig/github-add-collaborators.png)

To accept access to the Owner's repo, the Collaborator
needs to go to [https://github.com/notifications](https://github.com/notifications)
or check for email notification. Once there she can accept access to the Owner's repo.

Next, the Collaborator needs to download a copy of the Owner's repository to her
machine. This is called "cloning a repo".

We'll be using a repository with an example script for making some plots of Sea Surface Temperature from the CANARI data.
You can find this repository at [https://github.com/CANARI-sprint/git-tutorial](https://github.com/CANARI-sprint/git-tutorial)

To clone the repo into her `Desktop` folder, the Collaborator enters:

```bash
$ git clone git@github.com:CANARI-sprint/git-tutorial.git ~/Desktop/git-tutorial
```

If you choose to clone without the clone path
(`~/Desktop/git-tutorial`) specified at the end,
you will clone inside your own favourite-places folder!
Make sure to navigate to the `Desktop` folder first.

![After Creating Clone of Repository](https://noc-oi.github.io/git-novice/fig/github-collaboration.svg)

The Collaborator can now make a change in her clone of the Owner's repository:

```bash
$ cd ~/Desktop/git-tutorial
$ nano basic-plots.py
```

Change:

```python
cmap = plt.get_cmap('seismic',21)
```

To:

```python
cmap = plt.get_cmap('bwr',21)
```



```bash
$ git add basic_plots.py
$ git commit -m "Changing the colourmap"
```

```output
 1 file changed, 1 insertion(+)
 create mode 100644 basic_plots.py
```

Then push the change to the *Owner's repository* on GitHub:

```bash
$ git push origin main
```

```output
Enumerating objects: 4, done.
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 306 bytes, done.
Total 3 (delta 0), reused 0 (delta 0)
To git@github.com:CANARI-sprint/git-tutorial.git
   9272da5..29aba7c  main -> main
```

Note that we didn't have to create a remote called `origin`: Git uses this
name by default when we clone a repository.  (This is why `origin` was a
sensible choice earlier when we were setting up remotes by hand.)

Take a look at the Owner's repository on GitHub again, and you should be
able to see the new commit made by the Collaborator. You may need to refresh
your browser to see the new commit.

To download the Collaborator's changes from GitHub, the Owner now enters:

```bash
$ git pull origin main
```

```output
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From git@github.com:CANARI-sprint/git-tutorial
 * branch            main     -> FETCH_HEAD
   9272da5..29aba7c  main     -> origin/main
Updating 9272da5..29aba7c
Fast-forward
 basic_plots.py | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 basic_plots.py
```

Now the three repositories (Owner's local, Collaborator's local, and Owner's on
GitHub) are back in sync.


#### Triggering a Merge Conflict

If two more changes are made by doing the following:

(simultaneously)

* Clone the repository git@github.com:CANARI-sprint/git-tutorial.git (using SSH).
* Edit the colourmap on line 73, choosing one from the [Matplotlib Documentation](https://matplotlib.org/stable/users/explain/colors/colormaps.html).
* Add/Commit this change to your local repository.
* Push your changes to the upstream repository.
* Only the first person to push will be able to get their changes through, the other person will get a merge conflict error since multiple people have edited the same line.

#### Resolving a Merge Conflict

As soon as people can work in parallel, they'll likely step on each other's
toes.  This will even happen with a single person: if we are working on
a piece of software on both our laptop and a server in the lab, we could make
different changes to each copy.

When the second person tries to push changes to Github they will see something like this error:
```output
To git@github.com:NOC-OI/favourite-places.git
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'git@github.com:CANARI-sprint/git-tutorial.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
Git rejects the push because it detects that the remote repository has new updates that have not been
incorporated into the local branch.
What we have to do is pull the changes from GitHub, then into the copy we're currently working in, and then push that.
Let's start by pulling:

```bash
$ git pull origin main
```

```output
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (1/1), done.
remote: Total 3 (delta 2), reused 3 (delta 2), pack-reused 0
Unpacking objects: 100% (3/3), done.
From git@github.com:CANARI-sprint/git-tutorial.git
 * branch            main     -> FETCH_HEAD
    29aba7c..dabb4c8  main     -> origin/main
Auto-merging basic_plots.py
CONFLICT (content): Merge conflict in basic_plots.py
Automatic merge failed; fix conflicts and then commit the result.
```

The `git pull` command updates the local repository to include those
changes already included in the remote repository.
After the changes from remote branch have been fetched, Git detects that changes made to the local copy
overlap with those made to the remote repository, and therefore refuses to merge the two versions to
stop us from trampling on our previous work. The conflict is marked in
in the affected file:

```bash
$ cat basic_plots.py
```

```output
<<<<<<< HEAD
cmap = plt.get_cmap('seismic',21)
=======
cmap = plt.get_cmap('PuOr',21)
>>>>>>> dabb4c8c450e8475aee9b14b4383acc99f42af1d
```

Our change is preceded by `<<<<<<< HEAD`.
Git has then inserted `=======` as a separator between the conflicting changes
and marked the end of the content downloaded from GitHub with `>>>>>>>`.
(The string of letters and digits after that marker
identifies the commit we've just downloaded.)

It is now up to us to edit this file to remove these markers
and reconcile the changes.
We can do anything we want: keep the change made in the local repository, keep
the change made in the remote repository, write something new to replace both,
or get rid of the change entirely.

To finish merging,
we add `basic_plots.py` to the changes being made by the merge
and then commit:

```bash
$ git add basic_plots.py
$ git status
```

```output
On branch main
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:

	modified:   basic_plots.py

```

```bash
$ git commit -m "Merge changes from GitHub"
```

```output
[main 2abf2b1] Merge changes from GitHub
```

Now we can push our changes to GitHub:

```bash
$ git push origin main
```

```output
Enumerating objects: 10, done.
Counting objects: 100% (10/10), done.
Delta compression using up to 8 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 645 bytes | 645.00 KiB/s, done.
Total 6 (delta 4), reused 0 (delta 0)
remote: Resolving deltas: 100% (4/4), completed with 2 local objects.
To git@github.com:CANARI-sprint/git-tutorial.git
   dabb4c8..2abf2b1  main -> main
```

Git keeps track of what we've merged with what,
so we don't have to fix things by hand again
when the collaborator who made the first change pulls again:

```bash
$ git pull origin main
```

```output
remote: Enumerating objects: 10, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 6 (delta 4), reused 6 (delta 4), pack-reused 0
Unpacking objects: 100% (6/6), done.
From git@github.com:CANARI-sprint/git-tutorial.git
 * branch            main     -> FETCH_HEAD
    dabb4c8..2abf2b1  main     -> origin/main
Updating dabb4c8..2abf2b1
Fast-forward
 basic_plots.py | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```

Git's ability to resolve conflicts is very useful, but conflict resolution
costs time and effort, and can introduce errors if conflicts are not resolved
correctly. If you find yourself resolving a lot of conflicts in a project,
consider these technical approaches to reducing them:

- Pull from upstream more frequently, especially before starting new work
- Use topic branches to segregate work, merging to main when complete
- Make smaller more atomic commits
- Push your work when it is done and encourage your team to do the same to reduce work in progress and, by extension, the chance of having conflicts
- Where logically appropriate, break large files into smaller ones so that it is
  less likely that two authors will alter the same file simultaneously

Conflicts can also be minimized with project management strategies:

- Clarify who is responsible for what areas with your collaborators
- Discuss what order tasks should be carried out in with your collaborators so
  that tasks expected to change the same lines won't be worked on simultaneously
- If the conflicts are stylistic churn (e.g. tabs vs. spaces), establish a
  project convention that is governing and use code style tools (e.g.
  `htmltidy`, `perltidy`, `rubocop`, etc.) to enforce, if necessary


### Pull Requests

As you have seen, multiple people working on the same repository can cause a lot of problems. Github provides another way to collaborate called pull requests. In these each person makes their own copy of the repository on Github, this is known as a fork. Instead of working in the same repository as everyone else, each person works on their own fork. When they are ready to send the changes back to the main repository they create a pull request (literally asking the owner of the repository to do a git pull from theirs). Github wraps this in a nice interface, which allows you to write a comment about what you changed, for the owner to review your changes (and possibly request you make more before they accept it) and for them to finally accept or reject them. Once they are accepted the changes from your fork are merged into the upstream repository. If there are any conflicts then it will be up to the owner of the upstream repository to resolve them.

#### Pull Requesting Changes
* Create a fork of the favourite-places repository by visiting https://github.com/CANARI-sprint/git-tutorial and clicking on the fork link near the top right hand corner.
* Create an additional change to the basic_plots.py file in the repository.
* Github should now tell you that your fork is "1 commit ahead" of the upstream repository and offer a "Contribute" button to start the pull request.
* Click this and choose "Open Pull Request".
* The next screen will highlight the differences between your version and the upstream one. Go ahead and click "Create pull request".
* The repository owner should now get an alert about your pull request and can choose whether to merge it or not.

Pull requests are best for larger projects where you want to control or at least review any changes. This does require the project's owners to spend time reviewing any pull requests. 
Smaller projects where all the developers trust each other might be better suited to allowing multiple people direct write access.

#### Making additional changes to a Pull Request
* Create another pull request using the same method as above.
* After submitting the pull request, you decide to make another change either because you found a mistake or the upstream repository owner asked you to fix something.
* Make this change to your fork and push them to github.
* The pull request should automatically update with any additional changes you make.

#### Pull Requests in Big Projects
In many large projects all work will be done via pull requests and merging changes back into the main repository will involve a large scale code review process. There may also be autoamted checks involved to stop code which doesn't pass tests (or doesn't have tests) from being merged into a production system.


### Summary

* Conflicts occur when two or more people change the same lines of the same file.
* The version control system does not allow people to overwrite each other's changes blindly, but highlights conflicts so that they can be resolved.
* Giving many people write access to the same repository can result in a lot of conflicts if they all change the same file(s).
* Pull requests offer a controlled way to share your changes and let the project owner review them.
