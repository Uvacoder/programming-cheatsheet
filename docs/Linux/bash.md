# Bash

## How to set up alias for command

[for dietpi system] modify file `nano /home/pi/.bash_aliases` and add there for example:

```sh
alias temp='/opt/vc/bin/vcgencmd measure_temp'
```

## ZSH and oh-my-zsh - Make bash more intuitive and usefull

> ZSH also called the Z shell, is an extended version of the Bourne Shell (sh), with plenty of new features, and support for plugins and themes. Since it’s based on the same shell as Bash, ZSH has many of the same features, and switching over is a breeze.

Install `ZSH` and `Oh-My-ZSH` (freamwork for easly manage zsh - additional plugins and themes):

```Bash
brew install zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" #install Oh-My-ZSH
```

## Add auto suggestions and shell syntax highlight

You have to install two plugins: `zsh-autosuggestions` and `zsh-syntax-highlighting`.

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
vim ~/.zshrc
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Now, you can add it to your zsh config file `~/.zshrc`.

```bash
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

## Running multiple commands in one line in shell

- `|` pipes (pipelines) the standard output (stdout) of one command into the standard input of another one. Note that stderr still goes into its default destination, whatever that happen to be.
- `|&` pipes both stdout and stderr of one command into the standard input of another one. Very useful, available in bash version 4 and above.
- `&&` executes the right-hand command of && only if the previous one succeeded.
- `||` executes the right-hand command of || only it the previous one failed.
- `;` executes the right-hand command of ; always regardless whether the previous command succeeded or failed. Unless set -e was previously invoked, which causes bash to fail on an error.

[stackoverflow question](https://stackoverflow.com/questions/5130847/running-multiple-commands-in-one-line-in-shell)

## Create folder even exists

`mkdir -p` would not give you an error if the directory already exists and the contents for the directory will not change.

```
mkdir -p folder_name
```
