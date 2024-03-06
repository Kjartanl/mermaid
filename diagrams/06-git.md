# Git graph example

````mermaid
gitGraph

commit id: "First commit"
commit id: "First code"
branch "dev"
commit id:"Created dev"
checkout main
commit id:"Add config files"

checkout dev
merge main id:"Merged configs"
commit id:"Add dev config files"
commit

branch kjartan
commit
commit

checkout main
branch quick-fix
commit id:"item-1"
commit id:"item-2"

checkout main
merge quick-fix

checkout kjartan
cherry-pick id:"item-1"
commit

checkout dev
merge kjartan

checkout main
merge dev






```` 