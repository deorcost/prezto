Prezto — Instantly Awesome Zsh
==============================

Prezto is the configuration framework for [Zsh][1]; it enriches the command line
interface environment with sane defaults, aliases, functions, auto completion,
and prompt themes.

Fork Notes
----------

Additional README section added to my fork to keep track of installation,
content, and upkeep instruction. Original (upstream) content begins below this
section.

This is a fork of the original (user: `sorin-ionescu`) prezto. The fork enables
me to maintain my own configuration files and pull my setup to multiple
machines.


### Setting up the repository ###

The instructions are similar to the upstream repository instructions seen in
the next section, except for the difference in repository location.

  1. Clone the repository (note the user is `deorcost`)

     ```console
     git clone --recursive https://github.com/deorcost/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"
     ```

 2. Create a new Zsh configuration by copying the Zsh configuration files
    provided (identical to upstream instructions):

    ```sh
    setopt EXTENDED_GLOB
    for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
      ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
    done
    ```

 3. Change change current working directory to the `prezto` repository:

    ```console
    cd ~/.zprezto
    ```

 4. Add the upstream repository as a remote

    ```console
    git remote add upstream https://github.com/sorin-ionescu/prezto.git 
    ```

 5. Verify the upstream directory was added

    ```console
    git remote -v
    ```

Now my fork can be synced with the upstream repository.


### Integrating Upstream Changes with my Fork###

Keep my work up to date with the upstream repository. Instructions assume that
you are within the working (`.zprezto`) directory.

 1. Commit any local changes, e.g.

    ```console
    git add .
    git commit -m "Some message"
    ```

 2. Fetch the branches and their respective commits from the upstream
    repository. Commits to master will be stored in a local branch,
    `upstream/master`.

    ```console
    git fetch upstream
    ```

 3. Check out your fork's local `master` branch

    ```console
    git checkout master
    ```

 4. Merge the changes from upstream/master into your local master branch. This
    brings your fork's master branch into sync with the upstream repository,
    without losing your local changes.

    ```console
    git merge upstream/master
    ```

Syncing only updates my local copy of my repository. To update my fork, I need
to push my changes.


Installation
------------

Prezto will work with any recent release of Zsh, but the minimum required
version is 4.3.17.

  1. Launch Zsh:

     ```console
     zsh
     ```

  2. Clone the repository:

     ```console
     git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"
     ```

  3. Create a new Zsh configuration by copying the Zsh configuration files
     provided:

     ```sh
     setopt EXTENDED_GLOB
     for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
       ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
     done
     ```

     Note: If you already have any of the given config files, ln will error. In
     simple cases you can add `source "${ZDOTDIR:-$HOME}/.zprezto/init.zsh"` to
     the bottom of your `.zshrc` to load prezto but keep your config intact. For
     more complicated setups, it is recommended that you back up your original
     configs and replace them with the provided prezto runcoms.

  4. Set Zsh as your default shell:

     ```console
     chsh -s /bin/zsh
     ```

  5. Open a new Zsh terminal window or tab.

### Troubleshooting

If you are not able to find certain commands after switching to *Prezto*,
modify the `PATH` variable in *~/.zprofile* then open a new Zsh terminal
window or tab.

Updating
--------

Run `zprezto-update` to automatically check if there is an update to zprezto.
If there are no file conflicts, zprezto and its submodules will be
automatically updated. If there are conflicts you will instructed to go into
the `$ZPREZTODIR` directory and resolve them yourself.

To pull the latest changes and update submodules manually:

```console
cd $ZPREZTODIR
git pull
git submodule update --init --recursive
```

Usage
-----

Prezto has many features disabled by default. Read the source code and
accompanying README files to learn of what is available.

### Modules

  1. Browse */modules* to see what is available.
  2. Load the modules you need in *~/.zpreztorc* then open a new Zsh terminal
     window or tab.

### Themes

  1. For a list of themes, type `prompt -l`.
  2. To preview a theme, type `prompt -p name`.
  3. Load the theme you like in *~/.zpreztorc* then open a new Zsh terminal
     window or tab.

     ![sorin theme][2]

Customization
-------------

The project is managed via [Git][3]. It is highly recommended that you fork this
project; so, that you can commit your changes and push them to [GitHub][4] to
not lose them. If you do not know how to use Git, follow this [tutorial][5] and
bookmark this [reference][6].

Resources
---------

The [Zsh Reference Card][7] and the [zsh-lovers][8] man page are indispensable.

License
-------

This project is licensed under the MIT License.

[1]: http://www.zsh.org
[2]: http://i.imgur.com/nrGV6pg.png "sorin theme"
[3]: http://git-scm.com
[4]: https://github.com
[5]: http://gitimmersion.com
[6]: http://gitref.org
[7]: http://www.bash2zsh.com/zsh_refcard/refcard.pdf
[8]: http://grml.org/zsh/zsh-lovers.html
