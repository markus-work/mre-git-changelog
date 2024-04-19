# mre-git-changelog-encoding

This repository is a test repository to reproduce a bug in the git-changelog related to encoding.

## Description
Outputing changelog to file with conventional commits and a non-ascii character in the commit message will result in the error:

```
git-changelog: 'charmap' codec can't encode character '\U0001f527' in position 212: character maps to <undefined>
```

## Steps to reproduce

1. Clone this repository
2. Create virtual environment
3. Install the requirements from the requirements.txt
4. Run the command `git-changelog --config-file config/git-changelog-md.toml`
5. Observe the error `'charmap' codec can't encode character`
6. Run the command `git-changelog --config-file config/git-changelog-no-output.toml`
7. Observe no error occurs.
8. Install the fixed version of git-changelog `pip install -r requirements-fixed.txt`
9. Run the command `git-changelog --config-file config/git-changelog-md.toml`
10. Observe no error occurs and changelog.md is created.
