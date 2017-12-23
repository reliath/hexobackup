---
title: My Mac Terminal
thumbnail: /images/terminal.png
comments: true
categories:
  - General
tags:
  - Etc
date: 2017-08-05 01:36:55
---

~/.bash_profile 또는 ~/.profile 에 다음의 내용을 추가

```bash profile
export TERM=xterm-color
export CLICOLOR=1
export LSCOLORS=GxFxCxDxBxegedabagaced
export GREP_OPTIONS='--color=auto'
alias ls='ls -GFh'
```

~/.vimrc 에 다음을 추가

```bash vimrc
:syntax on
```

그리고 다음을 클릭해서 설치 -  원래 터미널 소스는 [여기](https://github.com/chriskempson/tomorrow-theme)

[TomorrowNight.terminal](http://theeye.pe.kr/wp-content/uploads/2013/07/TomorrowNight.terminal.zip)

