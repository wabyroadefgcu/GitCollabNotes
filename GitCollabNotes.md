# Git Collaboration
These notes are designed to help you get familiar with the Git workflow, with a specific emphasis on collaboration with others.

## Notes:
To maximize the benefit of this information, it is recommended that you perform all Git operations using the **command line** interface. To install latest version, follow the directions [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

Note: Install git-bash on Windows to ensure consistency across platforms.
More extensive documentation on git workflow can be found [here](https://git-scm.com/book/en/v2)

## Important Commands:
`git clone [URL]`               : Create a local copy/clone from the repository

`git status`                      : Show which files are in staging area and which files are not being tracked

`git add [file/.]`              : Add a file(s) to the staging area; you may use . to add all files in a folder

`git commit -m "[Commit Desc]"` : Commit the files from the staging area to the repository; format description as a verb phrase (i.e. "Fix refresh bug")

`git log`                         : List the commits and show which files have changed

`git log -p [-number]`          : Show addition information (code diffs) about the commits RECOMMENDED: use -[number] to limit to last [number] commits

`git diff`                        : Compare working folder to staging area

`git diff --staged`               : Compare the staging area with the latest commit of repository

`git diff [id1] [id2]`        : Compare two commits NOTE: You may use only the first 4 characters of a commitID instead of the full 41 characters

NOTE: The full details of the diff output is beyond the scope of these notes. Use link above or search online "git diff" to find more info

`git checkout [id/branchname]`  : Shows a previous version of the file

`git checkout master`             : Restore the "Head" to the latest commit of the master branch

`git checkout -b [newbranch]`   : Create [newbranch] branch and checkout (same as doing 'git branch [newbranch]', then 'git checkout [newbranch]')

`git merge [branchToMerge]` : Merge branchToMerge into current branch (usually master)

`git branch -d [branchToDelete]` : Delete specified branch NOTE: Use caution

`git remote`                      : Show remote location of the repository (usually the repo on GitHub)

`git remote add origin [url]`   : Add new remote location for the repository; Get by going to the repo on Github and choosing "clone"

`git push origin [master/branch]`  : Push the branch to the corresponding branch on the remote repository

`git pull origin [master/branch]`  : Pull the specified branch from the remote repository


## Other Useful Commands:
git config --global color.ui auto : Get colored diff output

## When there is a conflict:
When you attempt to merge a branch and there is a conflict with the destination branch, you will see output such as this:

```
    Auto-merging Main.java
    CONFLICT (content): Merge conflict in Main.java
    Automatic merge failed; fix conflicts and then commit the result.
```
**Open Main.java in a text editor or IDE and look (or search) for the following symbols:**

**<<<<<<<**

**>>>>>>>**

**=======**

The actual code should look as follows:
```
<<<<<<< HEAD
  public void displayTitle() {
=======
  public String displayTitle() {
>>>>>>> branchToMerge
```
Essentially, everything between the <<<<<< and the ======= is the code that exists in the master (or branch to be merged to) and everything between the ======= and the >>>>>>> is the code that exists in the branch that's being merged in. Delete the unneeded version, along with the <<<<<<, ======= and >>>>>> characters.

There may be multiple lines in the shown conflicts. There also may be multiple files in which conlicts were found.

Once all of the conflicts have been removed from the file(s) and they have been saved, attempt to run `git merge` again. If resolution has been done correctly, the merge will automatically complete.
