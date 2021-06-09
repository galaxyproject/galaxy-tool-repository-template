[![Galaxy Tool Linting and Tests for push and PR](https://github.com/galaxyproject/galaxy-tool-repository-template/actions/workflows/pr.yaml/badge.svg?branch=main)](https://github.com/galaxyproject/galaxy-tool-repository-template/actions/workflows/pr.yaml/badge.svg)
[![Weekly global Tool Linting and Tests](https://github.com/galaxyproject/galaxy-tool-repository-template/actions/workflows/ci.yaml/badge.svg?branch=master)](https://github.com/galaxyproject/galaxy-tool-repository-template/actions/workflows/ci.yaml/badge.svg)

# Galaxy tool repository template

This is a template repository to create [IUC](https://github.com/galaxyproject/tools-iuc) style repositories.
It offers:

- the same structure as the IUC repository
- CI for pull requests and weekly CI for all tools

Some documentation of the structure and the use of the CI can be found in [here](TODO link to tutorial).

Setup
=====

- Adapt the repository owner from `galaxyproject` to the owner of your repository [here](https://github.com/galaxyproject/galaxy-tool-repository-template/blob/main/.github/workflows/ci.yaml#L15), [here](https://github.com/galaxyproject/galaxy-tool-repository-template/blob/main/.github/workflows/pr.yaml#L304) and [here](https://github.com/galaxyproject/galaxy-tool-repository-template/blob/main/.github/workflows/slash.yaml#L10). This is needed to forbid running the CI workflows in forks.
- Change the links for the badges in this document [here](https://github.com/galaxyproject/galaxy-tool-repository-template/blob/main/README.md#L1) and [here](https://github.com/galaxyproject/galaxy-tool-repository-template/blob/main/README.md#L2), i.e. chage the organisation and repository name in the links. Certainly you may want to add the other content of this document.
- Add the API keys to the toolshed and testtoolshed as secrets with the name `TTS_API_KEY` and `TS_API_KEY`. 
- Remove the example tool in `tools/example`


In order to use the `/run-all-tool-tests` slash command you need to add a secret `PAT` to your repo that allows the action to access
you repository - see [here](https://docs.github.com/en/actions/reference/encrypted-secrets). The slash command allows to run trigger weekly CI running using a given fork and branch of the Galaxy project, e.g. `/run-all-tool-tests branch=release_21.05 fork=galaxyproject`. 

Also consider adding:

- `CONTRIBUTING.md`
- `.github/CODEOWNERS`
- `.github/PULL_REQUEST_TEMPLATE.md`

Updates
=======

Only the CI workflows may require updates from time to time. You can manually copy the latest version from this repository to your repository (not changing the repository owner as indicated in the setup section). We suggest to do this at least once a year, ideally with every Galaxy release. 

Bug reports
===========

Please report problems with the CI workflows here: [IUC](https://github.com/galaxyproject/tools-iuc).
