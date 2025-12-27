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
Then restart the terminal or reboot the system or simply run `source ~/.bashrc` to restart the shell

To install the python 3.12.8 Run
```bash
pyenv install 3.12.8
pyenv local 3.12.8
```
Then check the python's version by running `python --version` it should say something like `Python 3.12.8`.

## Making venv
We need `venv` to make a virtual environment for our pytorch because arch linux doesnot allows pip to install the system wide packages.
So before we even make a venv we need to make sure that it is installed so you can simply run
```bash
sudo pacman -S --needed python python-virtualenv git base-devel
```

After installing the venv you can make a virtual environment by running.
```bash
python -m venv ~/venvs/myvenv
```
Please make sure to replace `myvenv` with the desired virtual environment's name.
Then activate the virtual environment by running
```bash
source ~/venvs/myvenv/bin/activate
```
Again please replace `myvenv` with the actual virtual environment's name you wrote.
Then run these basic commands
```bash
pip install --upgrade pip setuptools wheel
```
These will install/upgrade the core tools we will need to install the pip packages.

## Installing Actual PyTorch
To install the pytorch on arch we will need to nightly build not the stable build and the reason is that arch linux is a rolling release distro. So if you try to install the stable version on arch for ROCm then it won't be satisfied with your system and to ensure the satisfaction of packages we need to use the nightly build specific to the ROCm version you have.

Please check the ROCm version you have and then run these commands to install the PyTorch
```bash
export TMPDIR=~/tmp-pip
mkdir -p $TMPDIR 2>/dev/null
pip install torch torchvision torchaudio \
  --index-url https://download.pytorch.org/whl/rocm7.1
```
In the url `https://download.pytorch.org/whl/rocm7.1` please replace the `rocm7.1` with the actual rocm version you have as of the time.

 > Now just wait for the installation to be finished and your `PyTorch` will be all set 🙂

## How To Uninstall ?
For Uninstalling please run these commands
```bash
source ~/venvs/myvenv/bin/activate
pip uninstall torch torchvision torchaudio
rm -rf ~/venvs
rm -rf ~/tmp-pip
```
Again make sure to replace the `myenv` in the line number 1 with the actual virtual environment's name you wrote while creating it.

## Thanks for reading!
Found any issues ? Make an issue then.
Wanna contribute ? Make a pull request then!
In the end ? Have a nice time.
