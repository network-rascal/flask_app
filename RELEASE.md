# release instruction for flask app

## prerequisites
- follow the gitflow model for main/develop/release/hotfix branches
- determine what the next version number is
- make sure all unit and integration tests are passing on the develop branch - IF NOT, FIX SOMETHING

## pull requests and approvers
- features and hotfixes must go through a pull request to get merged and released

## hotfix versus feature release
- normal features plit from the develop branch to a branch named "feature/name" and once ready, merge back into the develop branch with a PR that results in a squash and merge
- when ready for release see the section below for [create release branch](#create-release-branch)
- hotfies are for production issues that need to be fixed outside of a normal release. they will split off of the main branch and are named "hotfix/name". once ready, merge directly into main with a pull request that results with a squash and merge
- any updates to the main branch from either a hotfix or release should be followed up with a merge back into the develop branch

## create release branch
1. on your local copy, make sure your main and develop branches are current
    ```
    git checkout main
    git pull

    git checkout develop
    git pull
    ```
1. create a new release branch off of **develop** using the new version as determined in prereq
    ```
    git checkout -b release/<v#.#.#>
    ```
1. commit the change to the release branch
    ```
    git add <files changed>
    git commit -m 'updating version for release'
    git push --set-upstream origin release/<version>
    ```
1. update any other documentation that might need to

## create a draft release
on github - create a new release and save it as a draft.
    - make the 'Tag' and the 'Title' v#.#.#
    - make sure the 'Target' is main
    - use the following markdown template:

    # Description
    flask app v#.#.#
    - some changes to the SOMETHING endpoint have been made. this was to accomodate X or file Y.

    # Breaking Changes
    - N/A

    # Features
    - Feature item here

    # Bugfixes
    - N/A or bugfix link

    # Improvements
    - Cleanup to something or another

- **make sure everyone contributing updates as needed**

## push changes and PR to main
- use git push to push your local changes to the repo
- open a PR to the main branch, it should run all checks and they should pass
- once PR is approved, it can be merged to main (with a commit merge - **not** a squash)
- do not delete the release branch
- lastly, merge the main branch back into develop, with a PR or direct merge. no need for more approvals
    ```
    git checkout main
    git pull

    git checkout develop
    git pull

    git merge main
    git push
    ```

## publish the release in github
- open your draft release in github and **make sure** it says @target: main
- then click the "publish release" button