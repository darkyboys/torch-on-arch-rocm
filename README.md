# PyTorch On Arch Linux (ROCm Only)
This repository shows the PyTorch installation on Arch Linux to run AI Tools.
 > Before you continue make sure to install the ROCm with the help of this repository on arch [Link](https://github.com/darkyboys/rocm-install-on-arch/)

## Installing Python 3.12
Python 3.12 is the sweet spot for most of the AI Work you will do (As of 15:33 IST, 27 Dec 2025)
For installing Python 3.12 we will need to install [pyenv](https://duckduckgo.com/?q=pyenv).
Please copy and paste these commands to the terminal (Only on arch linux) to install pyenv
```bash
# Copy paste these to install pyenv
sudo pacman -S pyenv
```
And make sure to add these to the end of your shell file either in `~/.bashrc` or `~/.zshrc`
```yaml
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
```

To install the python 3.12.8 Run
```bash

```
