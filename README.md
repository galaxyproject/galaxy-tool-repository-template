[![Galaxy Tool Linting and Tests for push and PR](https://github.com/galaxyproject/galaxy-tool-repository-template/actions/workflows/pr.yaml/badge.svg?branch=main)](https://github.com/galaxyproject/galaxy-tool-repository-template/actions/workflows/pr.yaml/badge.svg)
[![Weekly global Tool Linting and Tests](https://github.com/galaxyproject/galaxy-tool-repository-template/actions/workflows/ci.yaml/badge.svg?branch=master)](https://github.com/galaxyproject/galaxy-tool-repository-template/actions/workflows/ci.yaml/badge.svg)

# Galaxy tool repository template

This is a template repository to create [IUC](https://github.com/galaxyproject/tools-iuc) style repositories.
It offers:

- the same structure as the IUC repository
- workflows:
  - for testing new tools in pull requests (the `pr` workflow)
  - regular testing of all tools in the repository (the `ci` workflow)
  - regular automatic updates of all tools in the repository (the `autoupdate` workflow)

Some documentation of the structure and the use of the CI can be found in [here](https://training.galaxyproject.org/training-material/topics/dev/tutorials/tool-from-scratch/tutorial.html).

Setup
=====

- Each workflow contains a line `if: ${{ github.repository_owner == 'galaxyproject' }}` which ensures that they do not run on forked repositories. Change `galaxyproject` to the name of your organisation.
- By default the workflows will default values for the parameters of the IUC workflows. This also means that CI in your repository may change if the IUC changes the default values. This affects the following parameters:
  - `default_galaxy_fork` and `default_galaxy_branch` of the `setup` step of the `pr` and `ci` workflows
  - `test-timeout` of the `test` step of the `pr` and `ci` workflows
  - `max-file-size`, `report-level`, and `fail-level` of the `lint` job in the `pr` workflow
  Furthermore you may want to adapt the value of `max-chunks` of the `setup` step of the `pr` and `ci` workflows
  
- Change the links for the badges in this document [here](https://github.com/galaxyproject/galaxy-tool-repository-template/blob/main/README.md#L1) and [here](https://github.com/galaxyproject/galaxy-tool-repository-template/blob/main/README.md#L2), i.e. chage the organisation and repository name in the links. Certainly you may want to add the other content of this document.
- Add the API keys to the toolshed and testtoolshed as secrets with the name `TTS_API_KEY` and `TS_API_KEY`. 
- Remove the example tool in `tools/example`


In order to use the `/run-all-tool-tests` and `/run-autoupdate` slash command you need to add a secret `PAT` to your repo that allows the action to access
you repository - see [here](https://docs.github.com/en/actions/reference/encrypted-secrets). The `/run-all-tool-tests` slash command allows to run trigger weekly CI running using a given fork and branch of the Galaxy project, e.g. `/run-all-tool-tests branch=release_21.05 fork=galaxyproject`. 

Also consider adding:

- `CONTRIBUTING.md`
- `.github/CODEOWNERS`
- `.github/PULL_REQUEST_TEMPLATE.md`

Updates
=======

The template repository reuses the IUC worklfows. Therefore your tool repository will use improvements made in the IUC workflows. 
Still, there may be seldom changes to the calling workflows contained in this repository. In order to use them you have to manually copy the latest version from this repository to your repository (not changing the repository owner as indicated in the setup section). We suggest to do this at least once a year, ideally with every Galaxy release. 

Bug reports
===========

Please report problems with the CI workflows here: [IUC](https://github.com/galaxyproject/tools-iuc).
