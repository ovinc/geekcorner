# GitLab

## Merge requests

(taken from https://cameleon.univ-lyon1.fr/help/user/project/merge_requests/reviewing_and_managing_merge_requests.md#checkout-merge-requests-locally-through-the-head-ref)

Add the following alias to your ~/.gitconfig:
```
[alias]
    mr = !sh -c 'git fetch $1 merge-requests/$2/head:mr-$1-$2 && git checkout mr-$1-$2' -
```

Now you can check out a particular merge request from any repository and any
remote. For example, to check out the merge request with ID 5 as shown in GitLab
from the origin remote, do:
```bash
git mr origin 5
```
This will fetch the merge request into a local mr-origin-5 branch and check
it out.

