---
sidebar_position: 1
---

# Programming cheatsheet

This repo contains useful programming tips and tricks.

## General

### Google search queries

- `"what is javascript"` - Exact Match - Use quotes to force an exact-match search:
- `html AND css` - AND operator - AND operator will return only results related to both terms:
- `(javascript OR python) free course` - OR opeator - You can use the OR operator to get the results related - to one of the search terms
- `javascript -css` - Minus operator - operator will exclude results that contain a term or phrase:
- `"how to start * in 6 months"` - Wildcard operator - You can use the (*) wildcards as placeholders, which will be replaced by any word or phrase.
- `site:freecodecamp.org` - Site operator - earch inside a single website.
- `filetype:pdf learn css` - Search by filetype - You can also use a very useful feature that helps to find a specific file type.
- `ecmascript 2016..2018` - Search for a range of numbers.
- `JavaScript|HTML|CSS filetype:pdf -"framework" site:edu` - Google search result for JavaScript PDF documents, limit search to a domain e.g .com, .edu, .org e.t.c

Tips:

You can use | in place of OR. e.g JavaScript | HTML

The ext is also a substitute for filetype

## General Computer Problems

### Convert movies to another format

```sh
brew install ffmpeg
```

Stream copy (-c copy) is like a "copy and paste" so the quality is preserved and the process is fast.

```sh
ffmpeg -i input.mov -c copy output.mp4
ffmpeg -i input.mov -vcodec h264 output.mp4 #copy and modify codec for better compression
```

This will convert the MOV to H.264 video and AAC audio:

```sh
ffmpeg -i input.mov -c:v libx264 -c:a aac -vf format=yuv420p -movflags +faststart output.mp4
```

[ffmpeg homebrew](https://formulae.brew.sh/formula/ffmpeg)
[ffmpeg docs](https://ffmpeg.org/)

## Browsers

### Can I modify javascript bundle in firefox?

You can do it in several ways:

1. You should use javascript console to redefine functions.
2. You can also use fiddler and intercept the code.
3. You can use Firebug console, but is deprecated.
4. You can use [WebReplay Firefox](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/WebReplay), but is deprecated.

> Use `chrome` browser where modified files can be persisted storage.

## General Programmimng

### What are the different kinds of cases

- `Pascal Case` (Used for Class) => `MyVariable`
- `Camel Case` (Used for variable at Java, C#, etc.) => `myVariable`
- `Flat Case` (Used for package at Java, etc.) => `myvariable`
- `Snake Case` (Used for variable at Python, PHP, etc.) => `my_variable`
- `Kebab Case` (Used for css) => `my-variable`

## Mac OS

### Zip file/folder with password

```sh
zip -er example.zip ./example-folder/*
```

### Show/hide hidden files

```sh
defaults write com.apple.finder AppleShowAllFiles YES; //or NO
killall Finder
```

> You can also use keyboard shortcut `Shift + Command + .`

### Delete all .DS_Store files

```sh
sudo find / -name .DS_Store -delete; killall Finder
```

## AWS

### Serverless Framework vs AWS Serverless Application Model (SAM)

SAM on the other hand is an abstraction layer specifically for AWS using not only FaaS but also DynamoDB for storage and API Gateway for creating a serverless HTTP endpoint.

The biggest difference is that Serverless is written to deploy FaaS (Function as a Service) functions to different providers.

<https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/sam-cli-command-reference-sam-local-start-lambda.html>
<https://stackoverflow.com/questions/52228361/whats-the-difference-between-aws-sam-serverless-application-model-and-serverl>

### How to prepaire and access to EC2 instances

0. Create Amazon Linux 2 AMI instance
1. Update systemu during the creation

```sh
#!/bin/bash
yum update -y
yum install git -y
```

2. Generate new ssh key and download it

```sh
chmod 400 key-pair-name.pem
```

3. Use ssh to log in

```sh
ssh ec2-user@ip_address -i key-pair-name.pem
```

4. [Configure AWS CLI user](#how-to-change-aws-cli-user)

### How to change AWS CLI user

```sh
aws configure
```

and provide AWS Access Key ID and AWS Secrect Access Key.

### How to create DynamoDB table

After running AWS Configure, create a DynamoDB table using the following command:

```sh
aws dynamodb create-table --table-name ProductCatalog --attribute-definitions \
AttributeName=Id,AttributeType=N --key-schema \
AttributeName=Id,KeyType=HASH \
--provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5
```

### How to populate the table

```sh
aws dynamodb batch-write-item --request-items file://items.json
```

### How to query Dynamodb from EC2 command line

```sh
aws dynamodb get-item --table-name ProductCatalog --region us-east-1  --key '{"Id":{"N":"403"}}'
```

## Firebase

[Sapmles of functions](https://github.com/firebase/functions-samples)

### CLI Commands

[CLI Documentation](https://firebase.google.com/docs/cli)

### Run local functions using different port

```bash
firebase serve --only functions --port=9000
```

## Linux

### Configure VNC Server

[link](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04)

```sh
sudo apt install tightvncserver #install server
vncserver #run server
vncserver -kill :1 #kill server
vncpasswd #change password
```

### How to set up alias for command

- only for your user `nano ~/.bash_aliases.`
- for all users `sudo nano /etc/bash.bashrc`

```sh
alias temp='/opt/vc/bin/vcgencmd measure_temp'
```

### How to check current user

```sh
# login name
whoami
echo $USER
# or full information
id
# or user name
id -F
# rest of user checkers
id -u  # returns UID
id -un # returns username
id -g  # returns primary (a.k.a. effictive) GID
id -gn # returns primary Group Name
# or currently logged users to system
w
```

### Check current shell path

```sh
echo $0
# or
echo $SHELL
```

### Change the shell path from/to bash/zsh

```sh
chsh -s $(which bash)
chsh -s $(which zsh)
# or specific folder as shell
chsh -s /bin/zsh
```

### How to check sum of file

```sh
md5 /path/to/file
shasum -a 1 /path/to/file
shasum -a 256 /path/to/file
shasum -a 512 /path/to/file
```

### How to list all files in catalog with sort by date

```sh
ls -haltr
# human readable size
# showing all dot prefixes
# list files
# sort by time
# revert results
```

### How to merge two or more mp3 files

```sh
cat file1.mp3 > newfile.mp3
cat file1.mp3 file2.mp3 file3.mp3 > newfile.mp3
```

> Only if MP3 files are recorded at the same bitrate.

### Envs

echo $SHELL
echo #ZSH

### Folders structure

- `/bin` binaries - programs or applications (cat, ls, cp)
- `/sbin` system binaries
- `/boot` - bootloader, everything what system needs to start running
- `/dev` - where devices lives,
  - `/char`
  - `/sda` - sda1, sda2
- `/etc` - storing configuration (sources.list, cron, application settings)
- `/home` - contains users home folders, for personal files and documents
- `/lib` - libraries
- `/media` - usually systems mount drivers automaticaly here (pendrives, cdroms)
- `/mnt` mount - folder to mount manually all drivers (pendrives, cdroms, network drives)
- `/opt` optional - folder to manual install software (virtualbox, printer software)
- `/proc` - sudo files, for system processes
- `/root` - root user home folder
- `/run` - tempfs files system, files to faster start system
- `/snap`
- `/srv` - service directory (ftp server, http server)
- `/sys` system - similar to `/run` directory, installed during the boot start system
- `/tmp` temporary - temporary director for programs during session, you can recover something from there
- `/usr` user - user applications
  - `/local`
  - `/src`
  - `/share`
- `/var` - variable directory
  - `/crash`
  - `/logs` for system and any diffrent applications

### xargs - Using subshell with xargs and docker

> Returned text from first execution will be passed to the second command

```bash
docker images artifactory.mrgreen.tech/docker/gametek/sportsbook/sb-mfe:latest -q | xargs docker stop
```

### Usefull commands

```bash
updatedb
locate [file]
passwd
man [command]
[command] --help
```

### Update grub

```bash
sudo update-grub
```

### Manage users and privilages

```bash
-rw-r--r--@  1 kubek  staff  20484 Oct 18 15:28 some_file.txt
drwxr-xr-x  19 kubek  staff    608 Oct 18 15:28 some_folder
```

First letter says about `-` file or `d` folder (directory). Next are tell us about access to this specific file/folder.

| # |        Permission       | rwx | Binary |
|:-:|:-----------------------:|:---:|:------:|
| 7 | read, write and execute | rwx | 111    |
| 6 | read and write          | rw- | 110    |
| 5 | read and execute        | r-x | 101    |
| 4 | read only               | r-- | 100    |
| 3 | write and execute       | -wx | 011    |
| 2 | write only              | -w- | 010    |
| 1 | execute only            | --x | 001    |
| 0 | none                    | --- | 000    |

You can modify access using command `chmod`, fe.

```bash
chmod 0664 sharedFile
```

### Zip/Unzip files

```bash
zip -r filename.zip /home/folder/*
unzip html.zip ./
mv ./html/* /home/dazdyqephu/domains/ohsospecial.nl/public_html/
```

#### Commands

```bash
adduser [user name] #add new user to the system
cat /etc/passwd #show users
cat /etc/shadow #show users and passwords
su [user-name] #switch to provided user
```

#### Read more

[Shadow Passwords](https://www.cyberciti.biz/faq/understanding-etcshadow-file)
[Crack users passwords](https://null-byte.wonderhowto.com/how-to/crack-shadow-hashes-after-getting-root-linux-system-0186386/)

### Manage networks

```bash
ifconfig #shows you network interfaces available for you
iwconfig #shows you only wireless adapters
ping [server-ip-address]
arp -a
netstat -ano #shows you connections which are running on you machine
router #shows you routing table - where you traffic is exit essentially
```

### Manage files (create|modify|remove)

```bash
nano new-file.txt
touch new-file.txt
gedit new-file.txt
echo "tekst" > new-file.txt #create file and override with text
echo "tekst" >> new-file.txt #create file and save text at the bottom of file
```

### How to find files matched to pattern

```sh
find . -name "*edit*"
```

### How to remove found files

```sh
find . -name "*edit*" -delete
# OR
find . -name "*edit*" -exec rm -rf {} \;
```

### How to save command results in file

```sh
find . -name "*edit*" >> filename.txt
```

## Javascript

### How to copy text to browser clipboard

Use current user location:

```sh
navigator.clipboard.writeText(document.location.href);

### What $ and $$ doing in the browser

$(selector, element)
Looks up a CSS selector string selector , returning the first node descended from element that matches. If unspecified, element defaults to document. Equivalent to document.querySelector() or calls the $ function in the page, if it exists.

See the QuerySelector code snippet.

$$(selector, element)
Looks up a CSS selector string selector, returning an array of DOM nodes descended from element that match. If unspecified, element defaults to document. This is like for document.querySelectorAll(), but returns an array instead of a NodeList.

<https://developer.mozilla.org/en-US/docs/Tools/Web_Console/The_command_line_interpreter#helper_commands>

### How initialize eslint in project with predefined configuration

```sh
npm install eslint -g
eslint --init

# or

npm install eslit --save-dev
./node_modules/.bin/eslint --init
```

## Node.js

### How to create executable node.js file

Add to the top of file:

```js
#!/usr/bin/env node
```

### How to read file content?

```js
const fs = require('fs-extra');

const fileContent = await fs.readFile('../usage-instruction.txt', 'utf8');
```

## npm

### Package.json configuration

> <https://docs.npmjs.com/cli/v7/configuring-npm/package-json#main>

### Informations about npm package

```sh
npm info package-name
```

### How to use local npm package in another project

For tests purposes you can add package to `package.json` from your local project folder:

```json
{
  "global-functions": "file:../global-functions",
}
```

### What is scope and how to use it

A scope allows you to create a package with the same name as a package created by another user or organization without conflict. The scope name is everything between the @ and the slash.

- Unscoped packages are always public.

You can setup different repository for specific scope using your `.npmrc` file:

```sh
@myscope:registry=https://mycustomregistry.example.org
```

or use command line for it: `npm config set @myco:registry http://reg.example.com`

### Private repository

Modify `.npmrc` file:

```js
registry=http://npm.differentpage.com/
```

### How to versionize packages

| Code status |        Stage       | Rule | Example version |
|:-:|:-----------------------:|:---:|:------:|
| First release | New product | Start with 1.0.0 | 1.0.0    |
| Backward compatible bug fixes | Patch release | Increment the third digit | 1.0.1 |
| Backward compatible new features | Minor release | Increment the middle digit and reset last digit to zero | 1.1.0    |
| Changes that break backward compatibility | Major release | Increment the first digit and reset middle and last digits to zero | 2.0.0 |

### How to use versions in `package.json`

- Patch releases: 1.0 or 1.0.x or ~1.0.4
- Minor releases: 1 or 1.x or ^1.0.4
- Major releases: * or x

### You can set up version of package

You can setup version of the package directly from npm repository.

Examples:

```sh
# npm version [<newversion> | major | minor | patch | premajor | preminor | prepatch | prerelease [--preid=<prerelease-id>] | from-git]
npm version patch
npm version minor
npm version major
# and combinations with preword "pre"
npm version prepatch
npm version preminor
npm version premajor
# or alfa or beta tags
npm version preminor --preid alfa
npm version prerelease --preid=beta
```

after that you should deploy npm package into the repository:

```sh
npm publish
```

### Packages installation flags for `npm install` command

`common options: [
    -P|--save-prod|
    -D|--save-dev|
    -O|--save-optional
    -E|--save-exact
    -B|--save-bundle
    --no-save
    --dry-run
]`

### Show installed npm packages

You probably have some packages installed globally already on your system. You can see them by typing:

```bash
npm list --depth 0 #for local project

npm list -g --depth 0 #for global npm

# or

ls `npm root -g`
```

### Print the folder where npm will install executables

```sh
npm bin
```

### Try to run package from the nearest (or local project) executor

```sh
$(npm bin)/package_name
```

[run-locally-installed-npm-packages-without-global-install](https://www.rockyourcode.com/run-locally-installed-npm-packages-without-global-install/)

### Link developement package to the project

Copy package from developement npm package into final project:

```bash
npm link #run in npm package
npm link @scope/package-name #run in project
```

After developement process unlink package using:

```sh
npm unlink --no-save @scope/package-name #clear linked packages in project
npm unlink #clear npm links
```

> You can always check if package in linked correctly looking into node_modules.

### How to configure eslint?

The easiest way to install eslint configuration is run command:

```sh
./node_modules/.bin/eslint --init
```

### How to run a code after npm package installation?

You can set up command postinstall in `scripts` property inside of package.json file:

```json
{
  "scripts": {
      "postinstall": "node bin/index.js"
  }
}
```

> <https://docs.npmjs.com/cli/v7/using-npm/scripts#npm-ci>

### How to set up registry url and/or @scoped registry link

```sh
npm config set registry https://registry.npmjs.org
npm config get @company_name:registry
npm config set @company_name:registry https://artifactory.company.page/artifactory/api/npm/npm/
npm install -g @company_name/package-name
```

### How to set up files which should be included in npm package

The optional files field is an array of file patterns that describes the entries to be included when your package is installed as a dependency. File patterns follow a similar syntax to .gitignore, but reversed: including a file, directory, or glob pattern (*, **/*, and such) will make it so that file is included in the tarball when it's packed. Omitting the field will make it default to ["*"], which means it will include all files.

Some special files and directories are also included or excluded regardless of whether they exist in the files array (see below).

You can also provide a .npmignore file in the root of your package or in subdirectories, which will keep files from being included. At the root of your package it will not override the "files" field, but in subdirectories it will. The .npmignore file works just like a .gitignore. If there is a .gitignore file, and .npmignore is missing, .gitignore's contents will be used instead.

> <https://docs.npmjs.com/cli/v7/configuring-npm/package-json#files>

## Bash

### ZSH and oh-my-zsh - Make bash more intuitive and usefull

> ZSH also called the Z shell, is an extended version of the Bourne Shell (sh), with plenty of new features, and support for plugins and themes. Since it’s based on the same shell as Bash, ZSH has many of the same features, and switching over is a breeze.

Install `ZSH` and `Oh-My-ZSH` (freamwork for easly manage zsh - additional plugins and themes):

```Bash
brew install zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" #install Oh-My-ZSH
```

### Add auto suggestions and shell syntax highlight

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

### Running multiple commands in one line in shell

- `|` pipes (pipelines) the standard output (stdout) of one command into the standard input of another one. Note that stderr still goes into its default destination, whatever that happen to be.
- `|&` pipes both stdout and stderr of one command into the standard input of another one. Very useful, available in bash version 4 and above.
- `&&` executes the right-hand command of && only if the previous one succeeded.
- `||` executes the right-hand command of || only it the previous one failed.
- `;` executes the right-hand command of ; always regardless whether the previous command succeeded or failed. Unless set -e was previously invoked, which causes bash to fail on an error.

[stackoverflow question](https://stackoverflow.com/questions/5130847/running-multiple-commands-in-one-line-in-shell)
