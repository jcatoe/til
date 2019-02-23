# Edit Commit Messages

## Edit last commit message:
```
$ git commit --amend
```
This will open up in a vi/m editor so that you can edit the entire message. Save changes by typing `:wq`.


## Edit older commit messages:
```
$ git rebase -i HEAD~n
```

where `n` is how far back you want to go in history. The command will return a list of commits and include helpful instructions. For messages you want to edit, change `pick` to `reword`. After you save the changes, you will be taken through each commit message to edit.
