# Git graph example

````mermaid
gitGraph

commit id: "First commit"

branch "dev"
commit id:"First dev commit"

checkout main
commit id:"Add config files"

checkout dev
merge main id:"Merged configs"
commit

branch kjartan
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