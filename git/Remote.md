# Actions on remote repositories

## Clone remote repository

### Use a name different than 'origin'

```bash
git clone --origin custom_origin_name git@cameleon.univ-lyon1.fr:ovincent/xxx.git master
```

## Pull / Push


### Check connection to remote server

```bash
ssh -T git@cameleon.univ-lyon1.fr
```

with a shortcut (see *Shortcuts and Multiple Accounts*)
```bash
ssh -T ov1
```

### Récupérer sur l'ordinateur (pull) depuis un dépôt distant

```bash
git pull git@cameleon.univ-lyon1.fr:ovincent/xxx.git master
```

(où xxx est le nom du projet, master est le nom de la branche)

Avec raccourci ov1 :
```bash
git pull ov1:ovincent/xxx.git master
```

### Pull/Push

Envoyer les modifications sur le serveur distant (pull / push)

pull
```bash
git pull origin master
```
(équivalent à :)
```bash
git fetch origin
git merge origin/master
```

push
```bash
git push origin master
```

(ne pas oublier le pull avant le push !)

### Créer un dépôt distant par push depuis l'ordinateur

https://docs.gitlab.com/ee/gitlab-basics/create-project.html#push-to-create-a-new-project mais en fait il faut l'adapter pour le gitlab de l'ILM :

```bash
git push --set-upstream git@cameleon.univ-lyon1.fr:ovincent/xxx.git master
```
(xxx est le nom du projet)
Ca semble aussi marcher sans l'option --set-upstream, donc je ne suis pas sûr de à quoi l'option sert.

et ensuite (les instructions apparaissent dans le shell) :
```bash
git remote add origin git@cameleon.univ-lyon1.fr:ovincent/xxx.git
```



## Remote information

Avoir des informations sur le remote repository

```bash
git remote -v
```

Changer le nom du remote (par défaut : origin)

```bash
git remote rename name1 name2
```

Change URL of remote

```bash
git remote set-url remotename newurl
```


### Change from HTTPS authentication to SSH

```bash
git remote set-url origin git@cameleon.univ-lyon1.fr:ovincent/xxx.git
```

(git@ is for ssh while https is for username / password authentication)
