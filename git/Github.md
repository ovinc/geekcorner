# Github

## Pull requests

To view a pull request locally use the following pattern: `git fetch REMOTE pull/ID/head:NEWBANCH`
where all the caps names need to be replaced by appropriate ones.
- REMOTE is the remote name (e.g. origin)
- ID is the number of the pull request on github (integer)
- NEWBRANCH is the name of the new branch that will be created locally to checkout the request with
`git checkout NEWBRANCH`

For example,
```bash
git fetch hub pull/14/head:test
git checkout test
```
