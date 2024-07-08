# Mac setup tips

See https://chirpmyradio.com/projects/chirp/wiki/DevelopersPython3Environment

git via xcode/developer tools is good, but you may encounter issues with stock python, specifically running chrip may not work due to wxPython needs.

One option is to leverage pyenv based python with a bespoke build

## Pyenv based python

See the [homebrew package manager for osx](https://brew.sh) which is assumed already working and installed.

In the Terminal use brew to get python:

        brew install pyenv

        echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
        echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
        echo 'eval "$(pyenv init -)"' >> ~/.zshrc

In  a new Terminal now install the python version you want. Just using `pyenv install 3.10` for the latest v3.10 didn't work with wxPython, it wasn't to do with version `3.10.14` but rather the way that it was built. So i got `3.10.12` (*3.10.8 is recommended per wiki*) with framework options to see the difference:

        env PYTHON_CONFIGURE_OPTS="--enable-framework" pyenv install 3.10.12

Then confirmed versions now available

        $ pyenv versions
          system
          3.10.12
        * 3.10.14 (set by /Users/ei2081/.pyenv/version)

Then set to the framework enabled version

        pyenv global 3.10.12

Then dont forget to [install the requirements](README-contribute-setup.md) etc now for this version!

Then starting Chirp should work fine

