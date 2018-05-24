# Git Deploy

Deploy a source directory in the working tree to a local or mapped destination directory after commits and merges on a target branch.

The source and destination directories are treated as relative roots when deploying files, so `myrepo/subdir/source/*` is deployed to `destination/*` and not `destination/subdir/source/*`.

The destination directory can be cleaned before deployment. Otherwise, files and directories in the destination that are not in the source will be remain after deployment.

## Setup

Copy the post-commit and post-merge hooks in app to your repository's .git/hooks directory.

Use a custom git config section to specify the target branch, source directory, destination directory and whether or not extra files and directories in the destination should be removed.

Add a local config item to deploy a source directory to a destination directory and leave extra items in the destination after commits and merges on a target branch:

```shell
git config deploy.branch "target_branch path/in/repo/to/source /local/path/to/destination"
```

Append a local config item to deploy the same source directory to another destination directory and remove extra items in the destination after commits and merges on a target branch:

```shell
git config deploy.branch "target_branch path/in/repo/to/source /local/path/to/destination2 true"
```

Append a local config item to deploy another source directory to another destination directory (with spaces in their names) and remove extra items in the destination after commits and merges on a target branch:

```shell
git config --add deploy.branch "target_branch 'path/in/repo/to/another source' '/local/path/to/another destination' true"
```
