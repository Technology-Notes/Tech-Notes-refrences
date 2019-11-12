VCL, https://medium.com/@junaid.ali/apache-vcl-docker-containers-fe06159d8f59

https://apple.stackexchange.com/questions/312254/how-to-install-command-line-tools-offline

# markdown + Pandoc for report
- https://medium.com/@greut/how-do-i-bodge-a-quick-report-using-markdown-7a1f7af5d9a
- https://github.com/kjhealy/pandoc-templates

## Atom + MPE + pandoc
- https://github.com/shd101wyy/markdown-preview-enhanced
- https://pandoc.org/MANUAL.html
- http://wiki.ktug.org/wiki/wiki.php/%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0MacOSX/MacTeX
- https://github.com/jaimyoung/data-science-in-korean
- https://stackoverflow.com/questions/16965490/pandoc-markdown-page-break
```
sudo tlmgr repository add http://ftp.ktug.org/KTUG/texlive/tlnet ktug
sudo tlmgr pinning add ktug "*"
sudo tlmgr install nanumttf hcr-lvt
sudo tlmgr update --all --self
```
```
brew install pandoc
```
```
install Atom
install MPE plugin
```
## Example
```
---
title: "Doc Title"
author: John Doe
date: March 22, 2005
output:
  pdf_document:
    latex_engine: xelatex
    toc: true
    toc_depth: 3
papersize: A4
fontsize: 11pt
mainfont: NanumGothic
---

# 타이틀

1. zxxxx

아름다운 우리나라

\newpage

# 두번째
## 234 대한민국

122
아아아
바보바보

First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column

Content [^1]

```

# Slides: Marp
- https://github.com/yhatt/marp
- https://github.com/yhatt/marp/issues/208
- https://qiita.com/fk2763owl/items/b4797ceb250cee41146e
- https://highlightjs.org/static/demo/
- https://web.marp.app/
- https://www.webfx.com/tools/emoji-cheat-sheet/

Install required tools:
```
# MacOS
$ brew cask install marp
$ brew cask install drawio

```

# MacOS
* Homebrew, https://brew.sh/
* https://github.com/Homebrew/homebrew-cask
* Upgrade Homebrew Cask, https://github.com/buo/homebrew-cask-upgrade

* ssh-copy-id @ MacOSX
  - https://github.com/beautifulcode/ssh-copy-id-for-OSX

# eclipse
* Plugins
  * https://github.com/typesafehub/sbteclipse
  * scala IDE
  * checkstyle
  * pydev
  * dbeaver 

# git
* config
```
$ git config --global user.name <username>
$ git config --global user.email <mailaddress>
```
* git push & 400 ERROR
```
$ git config http.postBuffer 524288000
```

Remove submodule:
- https://gist.github.com/myusuf3/7f645819ded92bda6677

## Misc.

https://chris.beams.io/posts/git-commit/

homebrew versions
- https://coderwall.com/p/1ouwaq/install-specific-version-of-a-software-with-brew



git diff ref - ref:
```
git diff refs/tags/0.141..0.141-t > ~/tmp/1.diff
```