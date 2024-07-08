# Contributing - Setup

See https://chirpmyradio.com/projects/chirp/wiki/DevelopersPython3Environment

## Pre Reqs
- Python 3.10.8
    - Python 3.11 breaks a lot of things....
- configured git client
- You have cloned the git repository.

### Pre Req Tips
    - [mac](README-contribute-setup-mac.md) setup tips using PyEnv

## Install the python dependencies

    python3 -m pip install -r requirements.txt
    python3 -m pip install tox

or if you have pyenv or other multi-python-version-virtual-environment setup-foo:

    pip install -r requirements.txt
    pip install tox

## Run CHIRP
From inside the chirp git repo, type this to run CHIRP from source:

    chirpwx.py


## Running tests
Below are some examples for running tests using tox. This is required to pass the CI checks on submissions before things can be merged.

Running everything:

    $ tox

Running just style checks:

    $ tox -e style

Running just driver tests for only drivers with changes since origin/master:

    $ tox -e fast-driver

Running just one driver test by module name:

    $ tox -e driver -- -k ic2820

Running all driver tests for a given vendor:

    $ tox -e driver -- -k Icom


