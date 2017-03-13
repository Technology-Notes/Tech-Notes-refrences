# MacOS
* Upgrade all casks
```
brew cask list | xargs brew cask install --force
```
 - https://github.com/buo/homebrew-cask-upgrade

* ssh-copy-id @ MacOSX
 - https://github.com/beautifulcode/ssh-copy-id-for-OSX

* git push & 400 ERROR
```
$ git config http.postBuffer 524288000
```