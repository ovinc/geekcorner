# Git aliases and multiple accounts

Create or edit a file just called config in ~/.ssh and add the following content:

```bash
# John Martin's GitLab
Host jmgit
    HostName gitlab.com
    User git
    IdentityFile ~/.ssh/id_ed25519
```
(first line is just a comment, second one is the name of the alias after "Host", then it's server, login, and ssh key info)

Now to test ssh connection it's possible to just do
```bash
ssh -T jmgit
```
instead of
```bash
ssh -T git@gitlab.com
```

and e.g. to push to server
```bash
git push jmgit:johnmartin/project.git master
```

One can then add any other alias associated with other ssh keys, e.g. (after having created a new SSH key pair `id_laura`):

```bash
# Laura's Gitlab
Host laura
    HostName gitlab.com
    User git
    IdentityFile ~/.ssh/id_laura
```

(source: https://code.tutsplus.com/tutorials/quick-tip-how-to-work-with-github-and-multiple-accounts--net-22574 among others)