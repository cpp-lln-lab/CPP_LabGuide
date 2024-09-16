# CONTRIBUTING

This is a common effort, please contribute actively to this docs.
If something is unclear, incorrect, or incomplete; if something needs to be updated or if you found a new and cool feature, consider adding it yourself.
Here's a short guidelines on how to do so.


## Submit an issue (no git/github skills required)

Open an issue from [here](https://github.com/cpp-lln-lab/CPP_LabGuide/issues/new/choose) and try to be the most detailed possible.
Try to be the most detailed possible, so it's easier to intervene.


## Make the changes yourself (minor git/github skills required)

The actual text/scripts you find in this website are in this [repoistory](https://github.com/cpp-lln-lab/CPP_LabGuide) and in the `/doc` folder [here](https://github.com/cpp-lln-lab/CPP_HPC/tree/main/doc).
Each article/section of the website is a specific markdown (`.md`) file with (more or less) the same transparent name.

If you're new to markdown, here's a quick [markdown cheatsheet](https://www.markdownguide.org/cheat-sheet/).


### Edit from github

1. Browse the repo to find the the markdown file you want to edit (e.g. the one for this section is [contributing.md](https://github.com/cpp-lln-lab/CPP_HPC/blob/main/doc/contributing.md)) and click on `edit` (the pen icon) on the top right
2. Edit the file with your changes
3. When done, click on `commit changes` (green botton on the top right), select `Create a new branch for this commit and start a Pull Request`, and then `Commit changes`
4. On the new opened page, edit the Pull Request's title to provide more information (a few words, not an essay)
5. Select a reviewer (e.g. [Filippo Cerpelloni](https://github.com/fcerpe) or [Marco Barilari](https://github.com/marcobarilari)). The review process helps preventing unnecessary / unwanted changes.
6. Create the Pull Request (PR).

To change the website structure (add, reorder, rename sections), see the file `mkdocs.yml` and the section `Pages`.


### Edit locally

If you're unfamiliar with the terms used here, check out the [git cheatsheet](https://training.github.com/downloads/github-git-cheat-sheet/)

1. fork this repository
2. clone your forked repository
3. install the dependencies via:

```bash
pip install -r requirements.txt
```

4. create a branch
5. make your changes in the respective markdown file in the `doc` folder
6. visualize your changes by deploying a website preview via:

```bash
mkdocs serve
```

and view the preview here [http://127.0.0.1:8000/welcome](http://127.0.0.1:8000/welcome)

7. push your changes to your forked repository
8. open a pull request
