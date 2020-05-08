# shellrcd

This is a setup that will allow easy/easier management of you (zsh and bash)
configuration.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Quick Installation](#quick-installation)
- [Cautious Installation](#cautious-installation)
- [Example Installation](#example-installation)
- [EXTENDING SHELLRCD](#extending-shellrcd)
  - [Configuring Your Own Branch](#configuring-your-own-branch)
    - [Make A Test Commit](#make-a-test-commit)
  - [Pushing Your Changes](#pushing-your-changes)
  - [Working Example](#working-example)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Quick Installation

If you're happy to run the installation script directly as your normal
(non-root) user:

```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/chiselwright/shellrcd/master/tools/install.sh)"
```

or

```
sh -c "$(wget -qO- https://raw.githubusercontent.com/chiselwright/shellrcd/master/tools/install.sh)"
```

## Cautious Installation

If you prefer to download, examine, and run the script yourself:

```
curl -fsSL -o ~/install-shellrcd.sh \
    https://raw.githubusercontent.com/chiselwright/shellrcd/master/tools/install.sh

$EDITOR ~/install-shellrcd.sh

sh -c ~/install-shellrcd.sh
```

## Example Installation

```
monster-mash:~ testuser$ sh -c "$(curl -fsSL https://raw.githubusercontent.com/chiselwright/shellrcd/master/tools/install.sh)"
[zsh] Looking for an existing zsh config...
[zsh] Creating /Users/testuser/.zshrc and adding shellrcd block...
[bash] Looking for an existing bash config...
[bash] MacOS detected. Using .bash_profile.
[bash] Creating /Users/testuser/.bash_profile and adding shellrcd block...
[shellrcd] /Users/testuser/.shellrc.d is not found. Downloading...
[shellrcd] ...done
           _             _    _                    _
          ( )           (_ ) (_ )                 ( )
      ___ | |__     __   | |  | |  _ __   ___    _| |
    /',__)|  _ `\ /'__`\ | |  | | ( '__)/'___) /'_` |
    \__, \| | | |(  ___/ | |  | | | |  ( (___ ( (_| |
    (____/(_) (_)`\____)(___)(___)(_)  `\____)`\__,_)
                                ....is now installed!

    Please look over /Users/testuser/.bash_profile for any glaring errors.

    Check which scripts are active with:
        sh /Users/testuser/.shellrc.d/tools/list-active.sh

    Once happy, open a new shell or:
        source /Users/testuser/.bash_profile

monster-mash:~ testuser$
```

## EXTENDING SHELLRCD

The project aims to keep `master` as simple-yet-functional as possible,
including a few generic scripts.

With that in mind, the project won't be filling up `master` with tens of
scripts, overloading the startup with a mountain of behaviour that most people
won't want.

However, most users will want to keep up to date with any core improvements, so
should probably not fork the repo and detach from this original.

The project uses an origin named `shellrcd` to avoid potential confusion with
any desire to use `origin` for managing your additions.

### Configuring Your Own Branch

Make sure you set a suitable origin:

```
git remote add origin git@github.com:USERNAME/shellrcd-extras-chizcw.git
git remote update origin
```

```sh
git checkout -b extras/firstlast shellrcd/master
```

Verify that it can be updated (yes, with no changes)

```
shellrcd-update
```

Set a suitable remote for this branch, by pushing with `-u` set:

```
git push -u origin extras/firstlast
```

#### Make A Test Commit

You probably don't want an unmodified copy of the `master` branch:

```
echo 'alias just-a-test="echo Just A Test"' > ~/.shellrc.d/_agnostic/alias.test
chmod 0755 ~/.shellrc.d/_agnostic/alias.test

cd ~/.shellrc.d/
git add _agnostic/alias.test
git commit -m 'Add _agnostic/alias.test'
```
git add

Then test an 'update':

```
shellrcd-update
```

### Pushing Your Changes

Because you will be rebasing you work on top of another branch you should use
the following to push your changes to your repository:

```
git push --force-with-lease
```

### Working Example

In gitlab, we created an empty repository:

* [shellrcd-extras-chizcw](https://github.com/chiselwright/shellrcd-extras-chizcw)

We add this as a remote in `~/.shellrc.d`:

```
cd ~/.shellrc.d

git remote add origin git@github.com:chiselwright/shellrcd-extras-chizcw.git
```

Create our new branch, and push it:
```
git checkout -b extras/chizcw shellrcd/master

git push -u origin extras/chizcw
```
