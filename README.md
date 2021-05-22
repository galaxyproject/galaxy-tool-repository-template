# galaxy-tool-repository-template

This is a template repository to create [IUC](https://github.com/galaxyproject/tools-iuc) style repositories.
It offers:

- the same structure as the IUC repository
- CI for pull requests and weekly CI for all tools

Some documentation of the structure and the use of the CI can be found in [here](TODO link to tutorial).

Setup
=====

- Adapt the `TODO_REPOSITORY_OWNER` [here], [here] and [here]. This is needed to forbid running the CI workflows in forks.
- Add the API keys to the toolshed and testtoolshed as secrets with the name `TTS_API_KEY` and `TS_API_KEY`. 

In order to use the `/run-all-tool-tests` slash command you need to add a secret `PAT` to your repo that allows the action to access
you repository - see [here](https://docs.github.com/en/actions/reference/encrypted-secrets). The slash command allows to run trigger weekly CI running using a given fork and branch of the Galaxy project, e.g. `/run-all-tool-tests branch=release_21.05 fork=galaxyproject`. 

Also consider adding:

- `CONTRIBUTING.md`
- `.github/CODEOWNERS`
- `.github/PULL_REQUEST_TEMPLATE.md`