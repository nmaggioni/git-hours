# Git hours

[![Build Status](https://travis-ci.org/kimmobrunfeldt/git-hours.svg)](https://travis-ci.org/kimmobrunfeldt/git-hours)

Estimate time spent on a git repository.

**Example**

```json
➜  git-hours git:(master) githours
{
  "total": {
    "hours": 16,
    "commits": 45
  }
}
```

## How it works

The algorithm for estimating hours is quite simple.

![](docs/step0.png)

Go through all commits and compare the difference between
them in time.

<br>

![](docs/step1.png)

If the difference is smaller or equal then a given threshold, group the commits
to a same coding session.

<br>

![](docs/step2.png)

If the difference is bigger than a given threshold, the coding session is finished.
To compensate the first commit whose work is unknown, we add extra hours to the coding session.

<br>

![](docs/step3.png)

This is continued until we have determined all coding sessions.

<br>

## Install

    npm install -g nodegit
    npm install -g git-hours

## Usage

In root of a git repository run:

    githours

**Note: repository is not detected if you are not in the root of repository!**

For additional help

    githours --help

# For contributors

Documentation for git-hours developers.

## Release

* Commit all changes
* Run `grunt release`, which will create new tag and publish code to GitHub
* Edit GitHub release notes
* Release to NPM

    git checkout x.x.x
    npm publish


To see an example how to release minor/major, check https://github.com/geddski/grunt-release

## Test

Tests can be run with command

    grunt test

or

    npm test

You need to have *mocha* installed globally with `npm install -g mocha`.
