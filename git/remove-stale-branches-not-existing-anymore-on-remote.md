# Remove stale branches not existing anymore on remote

Running `git branch -a` shows me all existing local branches of a repository. This list grows bigger and bigger with the time.

For example:
```bash
   ◾ git branch -a
    * develop
      feature-EXIXD-000-phpunit
      feature-EXIXD-345-SearchForm
      feature/EXIXD-339-autocomplete
      feature/EXIXD-350-ConfirmDialog
      feature/EXIXD-364
      master
      remotes/origin/feature-EXIXD-000-phpunit
      remotes/origin/feature/EXIXD-265
      remotes/origin/feature/EXIXD-266
      remotes/origin/feature/EXIXD-268
      remotes/origin/feature/EXIXD-269
      remotes/origin/feature/EXIXD-273
      remotes/origin/feature/EXIXD-277
      remotes/origin/feature/EXIXD-278
      remotes/origin/feature/EXIXD-290
      remotes/origin/feature/EXIXD-293
      remotes/origin/feature/EXIXD-294
      remotes/origin/feature/EXIXD-341
      remotes/origin/feature/EXIXD-343
      remotes/origin/feature/EXIXD-349
      remotes/origin/feature/EXIXD-364
      remotes/origin/feature/soft-delete
      remotes/origin/master
      remotes/origin/task/puphpet
```

A lot of the branches have been removed on the origin because the features were finished and merged. But on my local system the branches still exist.
To remove the stale branches i have to run the following command:
```bash
git remote prune origin
```

To see what will be removed **before** it will be removed, it is good to do a `dry-run`.
```bash
git remote prune origin --dry-run
```

Running `dry-run` will look like this:
```bash
git remote prune origin --dry-run
Pruning origin
URL: git@gitlab.xxxxxx.de:symfony/exixd.git
 * [would prune] origin/bugfix/EXIXD-308
 * [would prune] origin/bugfix/tags
 * [would prune] origin/feature-EXIXD-000-phpunit
 * [would prune] origin/task/EXIXD-new-template-list
```