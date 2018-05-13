# Git Deploy

Deploy a branch after commiting changes to it or merging another branch into it.

## Usage
To deploy commits for a branch to a local or mapped directory, add a local config item:                                                                

```
git config --local deploy.branch "branch_name /path/to/deploy"           
```

To deploy additional branches, add more mappings to the local config:       

```
git config --local --add "branch2 /path/to/deploy2"                      
```

To deploy the same branch to multiple directories, add more mappings to the local config specifying the same branch again:                              

```
git config --local --add "branch2 /second/path/to/deploy2"               
```

To clean the deployment directory before deploying the commit, add a config item (note that this option applies to all deployment mappings and will not clean subdirectories that are not part of the commit):                      

```
git config deploy.clean true                                             
```
