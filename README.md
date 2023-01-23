# Mono Repo Without Version Bumps

This project is an experiment in creating a repository that houses multiple projects (monorepo) and managing versions without the need for
version bump commits, resulting in a cleaner commit history that only includes relevant commits.

## Description

* The project includes two simple applications: *app1* and *app2*, each consisting of a script.
* Version numbering follows the [Semantic Versioning](https://semver.org/) standard.
* Commit messages adhere to the guidelines of [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).
* There are no files that track the current version number or changelog.
  * Versions are marked using tags. Tags use a prefix to indicate which app they belong to.
  * A [release](https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases) references the tag and includes
    the changelog.
* When changes are made to one of the apps, a workflow is triggered that prepares a draft release, including the proposed version number
  and a changelog extracted from the commits. [Next Release action](https://github.com/marketplace/actions/next-release-info) calculates
  this info (version and changelog) using [convco](https://convco.github.io).
* The draft release can be edited to include any necessary changes to the changelog or version number, and when released, the tag will be created.
* Creating a tag triggers another workflow that attaches the app's script as an asset.
