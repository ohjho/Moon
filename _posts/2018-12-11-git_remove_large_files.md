---
layout: post
title:  "Remove large files from Git"
date:   2018-12-11
excerpt: ""
categories: dev
tags: [git]
comments: true
---

### Note
Github's single file size limit is 100MB  
The recommendation is to keep file size less then 50MB
{: .notice}

## The Problem
So let's say by "accident" you added some large files to your git repo in the pass. You start to notice now that each commit you make is pretty slow. `git push` seems to be compressing and writing files that are quite large.

You realized that your need to remove these large files. You tried `git rm --cached` but still the commits are slow. That's because **the large file still exists in the git history**; that is the basic of what version control does!

Therefore, the problem is, **how do I remove a complete file from Git history?** This can be useful in 2 ways:
1. remove large data files that's commited by accident
2. remove sensitive files

## Finding the files
As recommended by [this post][url_solution2](the second answer), you can run this [shell script](https://gist.github.com/ohjho/eb486e5e5054f892d086b26ef111da6d):

```
$ cd path/to/your/git/repo
$ sh git_blob_obj.sh
```

This will show you a list of all the blob objects in the repo, from smallest to biggest. [The stackover flow post][url_solution2] has a couple more options for filtering for files. For Mac users, you will need to remove the last line in `git_blob_obj.sh`

## Removing from Git History completely
For the file `large_file.wmv` as an example, you can run the following:
```
git filter-branch --index-filter 'git rm --cached --ignore-unmatch path/to/large_file.wmv' HEAD
git push origin master
```

Before running `git push`, I found that I have to run `git filter-branch` again with the `-f` option: `git filter-branch -f --index-filter`. As to why, [this post](https://stackoverflow.com/questions/6403601/purging-file-from-git-repo-failed-unable-to-create-new-backup) does a good job of explaining. And [here](https://git-scm.com/docs/git-filter-branch) is the doc for `git filter-branch`.

## Prevention
A good way to remove blob from your repo, for example .wmv files, is to run this script:
```
$ find . -name *.wmv -print0 | xargs -0 git rm -r --cached --ignore-unmatch
echo *.wmv >> .gitignore
```

## Git Lola (a side discovery)
I strumbled across `git lola` from [this stackoverflow post][url_solution1].

`git lola` is a git alias that you need to add to your `~/.gitconfig` file. It is a command-line tool that shows you details about your commits.

Detail instructions are available in [this tutorial](http://blog.kfish.org/2010/04/git-lola.html).

`git lol` shows you your repo tree structure with syntax coloring.
`git lola` is basically the same as lol but with details for all branches.

and using `git lola --name-status` we can also see what files were modified for each commit

[url_solution1]: https://stackoverflow.com/questions/2100907/how-to-remove-delete-a-large-file-from-commit-history-in-git-repository
[url_solution2]: https://stackoverflow.com/questions/10622179/how-to-find-identify-large-files-commits-in-git-history/42544963#42544963
