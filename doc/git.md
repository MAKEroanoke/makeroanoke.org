
# Git

## Git Config

For anyone learning git, these links should help:

+ [githubtraining/advanced-git](https://github.com/githubtraining/advanced-git/tree/master).
+ [Git Cheat Sheets](https://github.com/githubtraining/advanced-git/tree/master)

The first link explains `git rerere` further.

### Simple Config to Prevent Local Merge Conflicts

In particular, there are these two settings which help avoid merge conflicts. 

+ With small branches covering many files, merge conflicts may happen often. 
+ When a branch just adds a post that's rarely edited, merge conflicts are unlikely.

Still, they could occasionally block Jekyll or add characters to the HTML, which could be frustrating.

**git rebase**

When your `git pull` command is set to `rebase` it avoids merge conflicts when you update your local copy with upstream changes. It's set to `merge` by default.

Running `git config --global pull.rebase true` will default to rebase when pulling.

**git rerere**

Also, `git rerere` will remember the merge resolution for conflicts you encounter and will replay the same resolution in the future. 

Enable it by running `git config --global rerere.enabled true`.

The commands should set the following in your `~/.gitconfig`

```toml
[pull]
	rebase = true

[rerere]
	enabled = true
```
