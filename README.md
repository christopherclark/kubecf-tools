# kubecf-tools

This repository contains various helper tools for [KubeCF](https://github.com/cloudfoundry-incubator/kubecf)

## versioning

This dir contains a common versioning script which prints the version of the current git commit to stdout.

This script is a wrapper around the functionality of `git describe --tags --dirty` with small changes to split the git pre-release identifiers to allow
semver sorting.
It requires the latest tag of the current branch to be a semver version, otherwise it raises an exception.
Semver versions with plus elements like `1.0.2+gold` are not supported and also raise an exception.

If the latest commit is not tagged by a semver tag then a pre-release version is printed.

`<latest-released-version>-[<additional-pre-release-identifier>.]<commits-since-release>.g<small-latest-git-sha>[-<dirty-tag>]`

For example `1.0.2-5.gb3f7a0c1-dirty` or if there are additional pre-release identifiers in the git tag `1.0.2-alpha.5.gb3f7a0c1-dirty`.