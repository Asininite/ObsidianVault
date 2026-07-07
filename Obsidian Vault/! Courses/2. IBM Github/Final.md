https://github.com/Asininite/github-final-project/blob/main/README.md

https://github.com/Asininite/github-final-project/blob/main/LICENSE

https://github.com/Asininite/github-final-project/blob/main/CODE_OF_CONDUCT.md

https://github.com/Asininite/github-final-project/blob/main/CONTRIBUTING.md

https://github.com/Asininite/github-final-project/blob/main/simple_interest.sh

forked-repo
```
theia@theia-asininite:/home/project$ curl -s https://api.github.com/repos/Asininite/mcino-Introduction-to-Git-and-GitHub | jq -r '.parent.clone_url'
https://github.com/ibm-developer-skills-network/mcino-Introduction-to-Git-and-GitHub.git
theia@theia-asininite:/home/project$ 
```

merge-branches
```
theia@theia-asininite:/home/project/mcino-Introduction-to-Git-and-GitHub$ git merge bug-fix-typo
Updating ad95b0a..5f64d36
Fast-forward
 README.md | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)
```


bug-fix-revert
```
theia@theia-asininite:/home/project/mcino-Introduction-to-Git-and-GitHub$ curl -s https://api.github.com/repos/ibm-developer-skills-network/mcino-Introduction-to-Git-and-GitHub/pulls/9102 | jq -r '.head.repo.clone_url'
https://github.com/Asininite/mcino-Introduction-to-Git-and-GitHub.git
```

github-branches
```
theia@theia-asininite:/home/project/mcino-Introduction-to-Git-and-GitHub$ git branch -vv
  big-fix-revert 48649a2 Revert "fixed_typo_in_footer_of_README"
* bug-fix-revert 9c14a86 [origin/bug-fix-revert] Revert "fixed_typo_in_footer_of_README"
  bug-fix-typo   5f64d36 [origin/bug-fix-typo] fixed_typo_in_footer_of_README
  main           4bcb239 [origin/main] Revert "Revert "fixed_typo_in_footer_of_README""
```

