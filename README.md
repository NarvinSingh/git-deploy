# Git Deploy

Deploy a source directory in the working tree to a local or mapped destination directory after commits and merges on a target branch.

The source and destination directories are treated as relative roots when deploying files, so `myrepo/subdir/source/*` is deployed to `destination/*` and not `destination/subdir/source/*`.

The source directory can be deployed in default mode, in which case all files and directories in the source are copied to the destination, overwriting any corresponding items in the destination. After deployment, the destination will be identical to the source, plus other items that already existed in the destination.

The source directory can be deployed in clean mode, in which case all files and directories in the destination are deleted before the source items are copied to the destination. After deployment, the destination will be identical to the source.

The source directory can be deployed in diff mode, in which case only files that have changed since the previous commit, or don't exist in the destination will be deployed. After deployment, items that already existed in the destination, but are not in the source, will remain. Items in the destination that have been changed, and whose corresponding source items have not changed since the last commit will be out of sync. This mode uses the least amount of bandwidth.

## Setup

Copy the post-commit and post-merge hooks in app to your repository's .git/hooks directory.

Use a custom git config section to specify the target branch, source directory, destination directory and whether or not extra files and directories in the destination should be removed.

Add a local config item to deploy a source directory to a destination directory after commits and merges on a target branch in default mode:

```shell
git config deploy.branch "target_branch path/in/repo/to/source /local/path/to/destination"
```

Append a local config item to deploy another source directory to another destination directory (with spaces in their names) after commits and merges on a target branch in clean mode:

```shell
git config --add deploy.branch "target_branch 'path/in/repo/to/another source' '/local/path/to/another destination' clean"
```

Append a local config item to deploy the same source directory to another destination directory after commits and merges on a target branch using the backwards compatible value `true` to specify clean mode:

```shell
git config deploy.branch "target_branch path/in/repo/to/source /local/path/to/destination2 true"
```

Append a local config item to deploy the same source directory to another destination directory after commits and merges on a target branch in diff mode:

```shell
git config deploy.branch "target_branch path/in/repo/to/source /local/path/to/destination2 diff"
```
