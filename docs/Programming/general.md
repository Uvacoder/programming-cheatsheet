---
sidebar_position: 1
---

# General

## Google search queries

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


## How to convert movies to another format

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

## Can I modify javascript bundle in firefox?

You can do it in several ways:

1. You should use javascript console to redefine functions.
2. You can also use fiddler and intercept the code.
3. You can use Firebug console, but is deprecated.
4. You can use [WebReplay Firefox](https://developer.mozilla.org/en-US/docs/Mozilla/Projects/WebReplay), but is deprecated.

> Use `chrome` browser where modified files can be persisted storage.

## What are the different kinds of cases

- `Pascal Case` (Used for Class) => `MyVariable`
- `Camel Case` (Used for variable at Java, C#, etc.) => `myVariable`
- `Flat Case` (Used for package at Java, etc.) => `myvariable`
- `Snake Case` (Used for variable at Python, PHP, etc.) => `my_variable`
- `Kebab Case` (Used for css) => `my-variable`

## After computer format

### Applications

- Brave
- Docker
- Visual Studio Code
- Filezilla
- Surfshark
- Notino
- Postman
- Hyper

[https://hyper.is/plugins](https://hyper.is/plugins)

[https://tjay.dev/howto-my-terminal-shell-setup-hyper-js-zsh-starship/](https://tjay.dev/howto-my-terminal-shell-setup-hyper-js-zsh-starship/)

[https://github.com/ohmyzsh/ohmyzsh](https://github.com/ohmyzsh/ohmyzsh) (nie instalowałem, tylko próbowałem czysty zsh)

### Browser plugins

- LastPass
- Notion web clipper

### Configuration

- zsh
- nvm
- homebrew
