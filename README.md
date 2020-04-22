[![Build Status](https://travis-ci.org/thibaultduponchelle/messy-perl-ci-workflows.svg?branch=master)](https://travis-ci.org/thibaultduponchelle/messy-perl-ci-workflows) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/linux-check-syntax/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/linux-github-action-install-with-cpanminus/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/linux-github-action-install-with-cpm/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/linux-perl-container-cpm/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/linux-with-perl-setup-and-cpm/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/macos-cpm/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/macos-perl-container-cpm/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/macos-share-cpanminus/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/macos-share-cpm/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/macos-system-cpanminus/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/macos-system-cpm/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/nightly-build/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/perl-critic/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/plack/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/windows-cpanminus/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/windows-cpm/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 
[![Actions Status](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/workflows/xml-libxml/badge.svg)](https://github.com/thibaultduponchelle/messy-perl-ci-workflows/actions) 

# Messy Perl github ci workflows

## General

This is a repository to give some inspiration to my Perl fellow developers.

It can be also for some testing.

## Travis

You can find here the documentation about [Travis Perl helper](https://docs.travis-ci.com/user/languages/perl).

Please note that your repository needs to include a `Build.PL`, a `Makefile.PL` or a `makefile` (with a `test` target).

You also need to activate `Travis CI` for your repository (connect to travis website with github credentials).

## Github actions workflows

### Ready to use github actions

- [Install with cpm](https://github.com/marketplace/actions/install-with-cpanm) ([github repo](https://github.com/perl-actions/install-with-cpm))
- [Install with cpanm](https://github.com/marketplace/actions/install-with-cpanm) ([github repo](https://github.com/perl-actions/install-with-cpanm))
- [Setup Perl Environment](https://github.com/marketplace/actions/setup-perl-environment) ([github repo](https://github.com/shogo82148/actions-setup-perl))
- [Perl Critic](https://github.com/marketplace/actions/github-action-for-perl-critic) ([github repo](https://github.com/Difegue/action-perlcritic))

### Limits 

There is a limit in how much github actions you can run on private repositories.
It's a matter of storage and run duration. The duration depends the platform (linux is cheap, windows is less, and macos is very expensive).

![ghactionslimits](ghactionslimits.png)

### Containers limitation

You can only launch containers from a GNU/Linux host.
For instance, if you specify `run-on: macOS-latest`, you won't be able to use `container:` :


```
    # THIS CODE DOES NOT WORK

    runs-on: macOS-latest

    strategy:
      matrix:
        perl-version:
          - 'latest'

    container:
      image: perl:${{ matrix.perl-version }}
```

Will produce :

```
    ##[error]Container operations are only supported on Linux runners`
``` 

See for instance this [failed run](https://github.com/thibaultduponchelle/messy-perl-github-actions/runs/608005097?check_suite_focus=true)

## Notes 

### Check syntax

Executing `perl -c` on file could actually run them partially (`BEGIN` blocks...).

