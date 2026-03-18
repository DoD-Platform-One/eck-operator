# Contributing

Thanks for contributing to this repository!

If you are coming from `repo1.dso.mil` and have an account at `login.dso.mil`, please keep reading. If you are contributing from [GitHub](https://github.com/DoD-Platform-One) without a `dso.mil` account, see the Big Bang guidance for [External Github Contributions](https://repo1.dso.mil/big-bang/bigbang/-/blob/master/CONTRIBUTING.md?ref_type=heads#community-contributions-to-dod-platform-one-via-github).

This repository follows these conventions:

* [Semantic Versioning](https://semver.org/)
* [Keep a Changelog](https://keepachangelog.com/)
* [Conventional Commits](https://www.conventionalcommits.org/)

Development requires `kubectl`, `helm`, and access to a Kubernetes cluster. [k3d](https://k3d.io) is a reasonable lightweight option for local work.

To contribute a change:

1. Create a branch from `main`.
2. Make the required code and documentation changes.
3. Update or add tests as needed for the change. If you are changing package behavior, validate the chart renders and the package still deploys correctly.
4. Make commits using the [Conventional Commits](https://www.conventionalcommits.org/) format.
5. Update [`CHANGELOG.md`](./CHANGELOG.md) using the [Keep a Changelog](https://keepachangelog.com/) format.
6. If you change generated documentation such as [`README.md`](./README.md), regenerate it instead of editing it by hand.
7. Review [`docs/DEVELOPMENT_MAINTENANCE.md`](./docs/DEVELOPMENT_MAINTENANCE.md) for package-specific upgrade and testing guidance.
8. Open a merge request and reference the related issue when applicable.
9. Resolve pipeline failures and merge conflicts before requesting final review.
10. Wait for a maintainer listed in [`CODEOWNERS`](./CODEOWNERS) to approve and merge, or merge it yourself if you have permission.
