
# How to contribute


## Getting Started


### Reporting Bugs, Feature Requests

* Get an account on github
* Submit a ticket for your issue or contribute to an existing, similar issue
    * Clearly describe the issue
    * In your description, include the steps to reproduce the issue and also the platform (OS, ...) on which the issue occurs
    * Include any exception stack traces or other relevant log messages you have but keep it crisp
    * State the version of the software that exhibits the issue


### Contributing Changes

* Use a linux machine or OSX or CygWin on Windows
* Install GNU Make
    * On Debian, make it `apt-get install build-essential`
* Install node, npm and the likes, preferrably version 4.x.x of node
* Fork the repository


## Making Changes

* Clone your fork and add a second remote pointing to the original repository
    * `git remote add base https://github.com/...`
* Fetch existing a/o new branches and tags from the `base`
* Keep your fork up to date
    * By constantly fetching/pulling from `base`
    * Rebasing
    * Pushing to your repository
* Checkout the development branch on which you will base your changes on
    * `dev-next` may be the default development branch while there may be other such development branches
    * `git checkout dev-next`
* Create a different branch for each of your pull requests, never make changes to master or the development branches directly
* Name the branch so that you can determine easily for what it stands for
    * `git checkout -b gh-1234` for the issue that you are about to fix
* Always keep your branch up to date by rebasing it
    * `git rebase base/dev-next`
    * Resolve all conflicts that you get but make sure that all tests still work
* Keep your changes and commits atomic
    * Too many unrelated changes in a single commit distributed across the lot of the code base makes it difficult to understand your intentions
    * Use `commit --amend` gratuitously when working on your branch
* When writing commit messages, please try to adhere to the standards established by [conventional-changelog](https://github.com/ajoslin/conventional-changelog)
* Think twice before adding additional development dependencies
    * Ask first?
    * Development dependencies: npm standard package.json keys
    * Most plugins need to be made either development or runtime dependencies instead of global dependencies


### Submitting Pull Requests

* (Force) Push the branch to your repository 
* On github, submit a pull request (PR) with your proposed fixes or new features
* In your pull request, refer to the issue that the PR addresses, e.g. `proposed patch for #1234` or `fixes #1234`


### Making Additional Changes

* Rebase first
* Force push your branch to your repository, and your existing pull request will be updated accordingly


### Needless To Say

* Install dependencies
    * Use `make deps` to install both runtime and development dependencies
* Adhere to the overall documentation style
* Contributors whose PRs have been accepted will of course be named in the contributors list

