# Dockerfile Build Error: Incorrect COPY Order

This repository demonstrates a common error in Dockerfiles related to the order of `COPY` commands.  The original `Dockerfile` attempts to install Python packages from `requirements.txt` before copying the project's source code, leading to a build failure.  The corrected `Dockerfile_fixed` shows how to resolve this issue.

## Bug
The primary problem is that `requirements.txt` is copied before the necessary project files.  The `pip install` command thus cannot find the packages it needs to install. 

## Solution
To fix this, the order of the `COPY` instructions is reversed.  The source code is copied first, followed by `requirements.txt`, ensuring the installer can find the needed files.

## How to reproduce
1. Clone this repository.
2. Try building the original `Dockerfile` using `docker build -t buggy .`
3. Observe the build error.
4. Build the fixed `Dockerfile_fixed` using `docker build -t fixed .`
5. Observe the successful build.
