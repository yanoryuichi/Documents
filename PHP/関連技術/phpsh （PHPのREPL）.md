# phpsh （PHPのREPL）

## インストール
pythonが必要。（え？）

```bash
easy_install readline
git clone https://github.com/facebook/phpsh.git
cd phpsh
python setup.py install --prefix=$HOME/opt/phpsh
PYTHONPATH=$HOME/opt/phpsh/lib/python2.7/site-packages $HOME/opt/phpsh/bin/phpsh
```

.bashrc:

```bash
alias phpsh="PYTHONPATH=$HOME/opt/phpsh/lib/python2.7/site-packages $HOME/opt/phpsh/bin/phpsh"
```

## 参考

- http://www.phpsh.org/
- https://github.com/facebook/phpsh
