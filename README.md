# Messy Perl github actions 

## General

This is a repository to give some inspiration to my Perl fellow developers.

It can be also for some testing.

## Notes 

You can only launch containers from a GNU/Linux host.
For instance, if you specify `run-on: macOS-latest`, you won't be able to use `container:` :

```
    runs-on: macOS-latest

    #strategy:
    #  matrix:
    #    perl-version:
    #      - 'latest'

    #container:
    #  image: perl:${{ matrix.perl-version }}
```

Will produce :

```
    # ##[error]Container operations are only supported on Linux runners`
``` 

See for instance this [failed run](https://github.com/thibaultduponchelle/messy-perl-github-actions/runs/608005097?check_suite_focus=true)
