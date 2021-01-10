# Renaming A Branch

In a lot of my projects i am using the git-flow workflow. Sometimes i have to rename a branch because somebody used a wrong name for a branch - for example a feature-branch.

If i have checkout out the branch with the wrong name, it's easy to rename it. The command `git branch -m` helps me with that.

```bash
git branch -m <new-branch-name>
```

If i am on the `develop` branch and want to rename `feature/007-agent` to `feature/007-james-bond`, i run the following command: 

```bash
git branch -m feature/007-agent feature/007-james-bond
```