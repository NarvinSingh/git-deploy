# Git Deploy

Deploy a branch to a local or mapped directory after commits and merges on the branch.

## Setup

Copy post-commit and post-merge to the repository's .git/hooks directory.

Specify which branches should be deployed to which directories by creating mappings in a custom git config section. 

To deploy commits and merges to a branch to a local or mapped directory, add a local config item:                                                                

```
git config --local deploy.branch "branch_name /path/to/deploy"           
```

To deploy comits and merges to additional branches, add more mappings to the local config:       

```
git config --local --add "branch2 /path/to/deploy2"                      
```

To deploy comits and merges to the same branch to multiple directories, add more mappings to the local config specifying the same branch again:                              

```
git config --local --add "branch2 /second/path/to/deploy2"               
```

To clean the deployment directory before deploying a commit or merge, add a config item (note that this option applies to all deployment mappings and will not clean subdirectories that are not part of the commit):                      

```
git config deploy.clean true                                             
```
