---
layout: single
title:  "Post Format: GitHub Actions"
date:   2024-04-10 17:59:47 -0700
tags: github github-actions format python node ruff prettier
---

I wanted to format my python, markdown and yml files in a GitHub repository without having to do it before merge or push. I decided to use [Ruff](https://docs.astral.sh/ruff/formatter/) for python and [Prettier](https://prettier.io/) for markdown and yml files. I created a GitHub Actions workflow to format the files on every PR and push to the master branch.

The workflow checks out the code, installs Ruff and Prettier, formats the files, commits the changes and pushes them back to the repository. The workflow uses a private SSH key to clone the repository and push the changes back. I created a new SSH key pair and added the private key to the repository secrets. The public key was added to the repository deploy keys. The workflow uses the private key to clone the repository and push the changes back to the repository.

The key to having this workflow format post-merge/push is the use of `stefanzweifel/git-auto-commit-action` action. This action commits the changes and pushes them back to the repository. You can find more information about this action [here](https://github.com/stefanzweifel/git-auto-commit-action).

## Example workflow:

{% capture notice-3 %}
Warning: There are some invisible characters in the workflow file. Make sure to remove them before using the workflow. Had to add them to avoid an issue with how the page renders variables surrounded by curly braces. They are located between the first two curly braces in each variable. You can easily see them in an IDE like VSCode.
{% endcapture %}

<div class="notice">{{ notice-3 | markdownify }}</div>

### format.yml:

```yml
name: Format with Ruff and Prettier
on:
  pull_request:
    branches: [master]
  push:
    branches: [master]
jobs:
  format:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          ref: ${‎{ github.head_ref }}
          ssh-key: ${‎{ secrets.SSH_PRIVATE_KEY }}
      - uses: actions/setup-python@v5
        with:
          python-version: "3.12"
      - run: pip install ruff
      - run: ruff format
      - uses: actions/setup-node@v4
        with:
          node-version: "20.x"
      - run: npm ci
      - run: npm run format
      - name: Commit changes
        uses: stefanzweifel/git-auto-commit-action@v5
        with:
          commit_message: Apply formatting changes
          branch: ${‎{ github.head_ref }}
```

## Conclusion

![alt text](../assets/images/format-commits.png)

Notice the second commit in this list, "Apply formatting changes" and the co-author of the commit. In this example you can see that the workflow formatted the files and pushed the changes back to the repository. 

The action will run again on the push event but will not make any changes because the files are already formatted. You can avoid this if you only run the action on the pull_request and remove the on push event. 
