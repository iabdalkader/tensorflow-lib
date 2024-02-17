[![GitHub Build](https://github.com/openmv/tensorflow-lib/actions/workflows/main.yml/badge.svg)](https://github.com/openmv/tensorflow-lib/actions/workflows/main.yml)
[![GitHub license](https://img.shields.io/github/license/openmv/tensorflow-lib?label=license%20%E2%9A%96)](https://github.com/openmv/tensorflow-lib/blob/master/LICENSE)
![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/openmv/tensorflow-lib?sort=semver)
[![GitHub forks](https://img.shields.io/github/forks/openmv/tensorflow-lib?color=green)](https://github.com/openmv/tensorflow-lib/network)
[![GitHub stars](https://img.shields.io/github/stars/openmv/tensorflow-lib?color=yellow)](https://github.com/openmv/tensorflow-lib/stargazers)
[![GitHub issues](https://img.shields.io/github/issues/openmv/tensorflow-lib?color=orange)](https://github.com/openmv/tensorflow-lib/issues)

<img  width="480" src="https://raw.githubusercontent.com/openmv/openmv-media/master/logos/openmv-logo/logo.png">

# A Portable C Tensorflow Library

Full featured Tensorflow package for Cortex-M0-Plus, Cortex-M4, Cortex-M7, and Cortex-M55 CPUs with **no external dependencies**!

  - [Instructions for building](#instructions-for-building)
  - [Prebuilt Files](#prebuilt-files)
  - [Contributing to the project](#contributing-to-the-project)
    + [Contribution guidelines](#contribution-guidelines)

## Instructions for building

1. Clone this repo recursively:

       git clone --recursive https://github.com/openmv/tensorflow-lib.git

2. If you already have `arm-none-eabi-gcc` installed and available on your path do:

       python make.py

3. Otherwise, install GCC (only needs to be done once):

       source ci.sh && ci_install_arm_gcc

4. And then do:

       source ci.sh ci_build

You will need to use the `source ci.sh ci_build` to compile the library if you installed gcc via `source ci.sh && ci_install_arm_gcc` and did not add GCC to your path.

### Edge Impulse SDK (TensorFlow) Changes

If you edit anything in the Edge Impulse SDK (TensorFlow) repo, make sure to do `python make.py --clean` afterward to delete any cached changes. Otherwise, you may get confusing errors.

## Prebuilt Files

You can find libtf pre-built under [releases](https://github.com/openmv/tensorflow-lib/releases). Alternatively, you may include this repo as a submodule and use [libtf](libtf) directly from the repo. This will allow you to easily update libtf without having to store the binaries directly in your repo.

## Contributing to the project

Contributions are most welcome. If you are interested in contributing to the project, start by creating a fork of each of the following repositories:

* https://github.com/openmv/tensorflow-lib.git
* https://github.com/openmv/tensorflow.git

Clone the forked tensorflow-lib repository, and add a remote to the main tensorflow-lib repository:
```bash
git clone --recursive https://github.com/<username>/tensorflow-lib.git
git -C tensorflow-lib remote add upstream https://github.com/openmv/tensorflow-lib.git
```

Set the `origin` remote of the tensorflow submodule to the forked tensorflow repo:
```bash
git -C tensorflow-lib/edge-impulse-sdk remote set-url origin https://github.com/<username>/tensorflow.git
```

Finally add a remote to openmv's tensorflow fork:
```bash
git -C tensorflow-lib/edge-impulse-sdk remote add upstream https://github.com/openmv/tensorflow.git
```

Now the repositories are ready for pull requests. To send a pull request, create a new feature branch and push it to origin, and use Github to create the pull request from the forked repository to the upstream openmv/micropython repository. For example:
```bash
git checkout -b <some_branch_name>
<commit changes>
git push origin -u <some_branch_name>
```

### Contribution guidelines
Please follow the [best practices](https://developers.google.com/blockly/guides/modify/contribute/write_a_good_pr) when sending pull requests upstream. In general, the pull request should:
* Fix one problem. Don't try to tackle multiple issues at once.
* Split the changes into logical groups using git commits.
* Pull request title should be less than 78 characters, and match this pattern:
  * `<scope>:<1 space><description><.>`
* Commit subject line should be less than 78 characters, and match this pattern:
  * `<scope>:<1 space><description><.>`
