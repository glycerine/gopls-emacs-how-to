# how to get gopls in emacs with golang go-mode working

## getting jump-to-definition working with gopls and emacs in go-mode

1. install gopls

go get golang.org/x/tools/gopls

-- reference https://github.com/golang/tools/blob/master/gopls/doc/user.md

2. upgrade to emacs27.1
    so the package-install stuff works
    
on ubunut 18 this involves:
    
sudo add-apt-repository ppa:kelleyk/emacs
apt update
apt install emacs27

-- reference http://ubuntuhandbook.org/index.php/2020/09/install-emacs-27-1-ppa-ubuntu-20-04/

3. install eglot, from within emacs27.1

M-x package-install RET eglot RET

add to your .emacs, after go-mode is loaded:

(add-hook 'go-mode-hook 'eglot-ensure)

-- reference https://elpa.gnu.org/packages/eglot.html

4. open a .go file

you should see an eglot:project-name in your status line.

use M-. to jump to definition
    M-, to return

