# how to get gopls in emacs with golang go-mode working

Motivation: with the advent of golang modules, our workhorse godef no longer works or takes 10s of seconds to respond.
Something package-aware is needed. Enter gopls.

Overview: The gopls documentation is misleading. Its says use the emacs lsp-mode. No. Wrong.

lsp-mode is garbage. Instead use eglot.

## getting jump-to-definition working with gopls and emacs in go-mode

1. install gopls
~~~
go get golang.org/x/tools/gopls
~~~
-- reference https://github.com/golang/tools/blob/master/gopls/doc/user.md

2. upgrade to emacs27.1
    so the package-install stuff works
    
on ubuntu 18 this involves:
~~~    
sudo add-apt-repository ppa:kelleyk/emacs
apt update
apt install emacs27
~~~

If you get RSA/DSA key failure like this
~~~
package--check-signature: Failed to verify signature 
   ascii-art-to-unicode-1.9.el.sig: ("No public key 
   for 474F05837FBDEF9B created at 2014-09-24T16:20:01+0200 
   using DSA")
~~~
follow these instructions to resolve it

https://emacs.stackexchange.com/questions/233/how-to-proceed-on-package-el-signature-check-failure


-- reference http://ubuntuhandbook.org/index.php/2020/09/install-emacs-27-1-ppa-ubuntu-20-04/

3. install eglot, from within emacs27.1

M-x package-install RET eglot RET

add to your .emacs, after go-mode is loaded:
~~~
(add-hook 'go-mode-hook 'eglot-ensure)
~~~
-- reference https://elpa.gnu.org/packages/eglot.html

4. open a .go file

you should see an eglot:project-name in your status line.
~~~
use M-. to jump to definition
    M-, to return
~~~


-- reference for eglot: https://github.com/joaotavora/eglot
