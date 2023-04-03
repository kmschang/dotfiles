https://pre-commit.com
https://pre-commit.com/hooks.html


### Install necessary packages
```bash
brew install pre-commit
python3 -m pip install -U mypy
```

### Set up the yaml file
```bash
mkdir workflows
cd ./workflows
touch .pre-commit-config.yaml
cat ../../dotfiles/.pre-commit-config.txt >> .pre-commit-config.yaml
chmod +x .pre-commit-config.yaml
```


### Set up the pre-commit hook 
```bash
cd .git/hooks
mv pre-commit.sample pre-commit
truncate -s 0 pre-commit
cat ../../../dotfiles/pre-commit.txt >> pre-commit
xattr -d com.apple.quarantine pre-commit
```


## Total file
- **Don't use indents, change them to spaces**
```
# See https://pre-commit.com for more information
# See https://pre-commit.com/hooks.html for more hooks
repos:
-   repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v3.2.0
    hooks:
    -   id: trailing-whitespace
    -   id: end-of-file-fixer
    -   id: check-yaml
    -   id: check-added-large-files
    -   id: name-tests-test
    -   id: mixed-line-ending
    -   id: check-ast

-   repo: https://github.com/asottile/pyupgrade
    rev: v3.3.1
    hooks:
    -   id: pyupgrade

-   repo: https://github.com/PyCQA/flake8
    rev: 6.0.0
    hooks:
    -   id: flake8
```