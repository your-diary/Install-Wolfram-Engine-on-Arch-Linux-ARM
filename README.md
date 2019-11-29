# Install Wolfram Engine On Any Distributions

## Introduction

### What does this project do in a nutshell?

This project installs *Wolfram Engine* on any distributions (e.g. Arch Linux ARM) running on Raspberry Pi.

### What does this project do in detail?

*Wolfram Engine*, which includes famous *Mathematica*, usually costs much but it is freely distributed for Raspberry Pi officially. However, the installation script which can be downloaded from the [Wolfram + Raspberry Pi Project](https://www.wolfram.com/raspberry-pi/) page is written for Raspbian. Because Raspbian is based on Debian, the script downloads `.deb` files and installs them, using `apt` package manager. This means, by default, only those who are using distributions which are equipped with `apt` can install Wolfram Engine. But it makes more sense if every Raspberry Pi user can install it, because Wolfram Engine is freely distributed not for *Raspbian on Raspberry Pi* but for *Raspberry Pi without specifying any distributions*.

The script in this project essentially follows the steps below.

1. Download the official installation script.

2. Execute the script until the control reaches `apt`. The execution is terminated there because of `bash`'s `-e` flag.

3. Extract files from `.deb` files downloaded in the previous step.

4. Install the files under `/opt`.

5. Remove the temporary files.

## Usage

- `WE_MODE=install bash <script name>`

Install Wolfram Engine on your environment.

- `WE_MODE=uninstall bash <script name>`

Uninstall Wolfram Engine from your environment.

## Installation

1. `git clone "https://github.com/your-diary/Install-Wolfram-Engine-on-Arch-Linux-ARM"`

2. Read carefully the downloaded script and change it as you can **before** you execute it. Unfortunately the script is written for me. Not for you. So the change is in many cases needed to meet your needs.

## Requirement

Raspberry Pi with any distributions running on it is the only requirement.

## Frequently Asked Questions

- I think `cd /tmp` in the script is redundant because the value of `install_script_name` includes `/tmp`.

No, this is needed. If this line doesn't exist and you execute the script in a directory whose absolute path has space(s), the execution always fails. This is because the official installation script is written so poorly that variable references like `${HOME}` are **not** double-quoted (can you believe it?).

