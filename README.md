# Intel Aero Documentation

This repository contains the source files for Intel Aero documentation.
In order to use it you need to have [mkdocs](http://www.mkdocs.org/) and its themes/extensions
installed.

There's a [Makefile](https://github.com/intel-aero/intel-aero-docs/blob/master/Makefile) in this repository that's mostly a wrapper around mkdocs with some extra functionality related to this site.

## Setup and build

In order to build the documentation we need only python from the host
system. Additional dependencies are installed via pip. The preferred
method is to install them with:

```bash
make setup
```

This will install all required packages with `pip install --user --upgrade`

## Contributing

### Working locally / offline

```bash
git clone git@github.com:intel-aero/intel-aero-docs.git
cd intel-aero-docs
```

Edit (or include) .md files using the same syntax used by Github wiki (markdown). There [this helpful guide](https://guides.github.com/features/mastering-markdown/) that describes the syntax, with examples.

To change the documentation and visualize what's being changed, start
mkdocs's webserver:

```bash
# this is just a wrapper to "mkdocs serve"
make serve
```
When it's done, proceed to commit the changes using the regular git flow:

```bash
# Check changes not commited
git status

# Add modified files to the next commit
git add modified_file.md

# Commit
git commit -m "modified_file: Summary of modifications"

# Push to a branch for review
git push origin myusername-identifier

Then proceed with the [regular pull request flow in the Github web interface](https://help.github.com/articles/creating-a-pull-request/). This will notify members of the intel-aero organization so the modification can be reviewed and later merged.

```

### Using the online editor

Github provides a [built-in markdown editor](https://help.github.com/articles/editing-files-in-your-repository/), which means a .md file can be edited straight in the browser, comitted and submitted for review. 

Browse the directory structure and select a .md file to edit. In the top, right hand side there will be a pencil icon:

![edit icon](support/imgs/1-edit.png)

Clicking on that icon will open the current file in edit mode:

![edit mode](/support/imgs/2-edit.png)

Edit the file content, then use the preview tab to see if the modifications are valid

![preview changes](/support/imgs/3-preview.png)

The preview also shows the diff, with green marking content that has been added and red what has been removed, in comparison to the current state of the file:

![diff](/support/imgs/4-diff.png)

With the changes complete, use the fields in the bottom of the page to write a meaningful summary and a extended description, when necessary. Create a new branch and start a pull request to start the review process:

![commit and PR](/support/imgs/5-commit.png)


## Deploying

Set DEST variable and call `make deploy` or `make publish`:

```bash
export DEST=remote-server:/var/www/intel-aero-docs
make deploy
```

Rsync needs to be installed to synchronize the site built locally with
the remote one. If DEST isn't set, it will install to `/tmp/intel-aero-docs`
