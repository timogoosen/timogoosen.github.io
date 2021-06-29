## Git Stuff


### Git Links:

* [Throw away Local Commits](https://stackoverflow.com/questions/5097456/throw-away-local-commits-in-git#:~:text=If%20your%20excess%20commits%20are,will%20discard%20all%20local%20changes)
* [Delete branch locally and remotely](https://stackoverflow.com/questions/2003505/how-do-i-delete-a-git-branch-locally-and-remotely)
* [Updates were rejected because the tip of your current branch is behind](https://stackoverflow.com/questions/22532943/how-to-resolve-git-error-updates-were-rejected-because-the-tip-of-your-current)


### Git Submodule Resources:

* [Very good thorough post on git submodules](https://chrisjean.com/git-submodules-adding-using-removing-and-updating/)



### Commands:


Prunes branches your local git is aware of:

```

git remote prune origin

```

Create branch off another branch:

```

git checkout -b my-feature-branch master

```


### Submodule commands:

Pull changes to submodule after cloning:


```

git clone git://github.com/foo/bar.git

cd bar

git submodule update --init --recursive


```

Pull new changes from submodule/s

```

git submodule update --remote --merge

```

Fix merge conflict in submodule:


* [Fix Merge conflict in Submodule](https://stackoverflow.com/questions/826715/how-do-i-manage-conflicts-with-git-submodules)

Basically:

```

git checkout master submodule-dir/

```