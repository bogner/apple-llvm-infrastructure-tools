# git-apple-llvm: pr

`git apple-llvm pr` is a tool for creating, testing, merging and listing
pull requests.

## Commands

- `git apple-llvm pr create`: Creates a pull request.

- `git apple-llvm pr test`: Tests a pull request.

- `git apple-llvm pr list`: Lists all pull requests.

## Creating a pull request

The `git apple-llvm pr create` command can be used to create a pull request:

```
# Create a branch, make changes, push it to my own fork.
git checkout -b my-change
touch my-change && git add my-change && git commit -m "my change"
git push -u my_fork

# Now create the PR!
git apple-llvm pr create -m "This is my change" -h my-change -b master
```

Options:

- `-m, --title`: Pull request title (required)
- `-h, --head`: The name of the branch that contains the changes
- `-b, --base`: The name of the base branch into which the pull request will be merged.
- `--dry-run`:  Do not create the pull request.

## Testing a pull request

The `git apple-llvm pr test` command can be used to test a pull request.
You can pass in a pull request number to specify which pull request to test, for example:

```
git apple-llvm pr test #12
```

Will trigger tests for pull request number 12, unless it is already merged or closed.


Repositories that are hosted on github.com/apple will typically use `swift-ci` to trigger the test.
In that case, the command will add a `@swift-ci please test` comment to the pull request to trigger
the specific test.


## Listing pull requests

The `git apple-llvm pr list` command can be used to list the pull requests in a repository.
By default it will list the pull requests for all destination branches, but you can narrow down the list
by using the `--target` option.

Options:

- `--target <branch-name>`: list the pull requests for the given branch.

## Known issues

- None.
