# Week 1 Practical: TODO App

- This week we are creating a minimal HTTP API for a todo app (HTTP server in Python)
- [Practical handout with details can be found here](https://csse6400.uqcloud.net/practicals/week01.pdf)

# Setup and Installation in Windows using Visual Studio Code (VSCode)

#### For Windows: There are a couple of workflows:

1. Using Windows Subsystem for Linux (WSL)
2. Using Windows :)

## 1 - Using Windows Subsystem for Linux (WSL)

- Install WSL - (https://learn.microsoft.com/en-us/windows/wsl/install)
- Clone practical repo (if haven't done so) and open in VSCode
- Install the WSL extention for VSCode
- Switch (from the status bar) to WSL Ubuntu mode in VSCode. This should change the - terminal to Bash. (can also be done by just typing 'wsl' in the terminal)
- The extention for WSL allows VSCode to switch to the linux file system and list Ubuntu version of the extentions
- Install Ubuntu version of the 'RestClient' extention in VSCode as mentoned in the practical handout.
- Run the following commands in the terminal.
- `sudo apt install python3` - installs the latest python version (Python 3.10.6).
- `sudo apt install python3 - pip` - installs the package manager (should already have a version with python) or
- `sudo python3 -m pip install --upgrade pip` - to upgrade to latest since its developed separatly
- `sudo apt install pipenv` - to manage the Python libraries. Equivalent of npm for Node. Combines the pip and venv commands into a single tool chain
- `pipenv --python 3` - Init Python virtual environment under project.
- `pipenv install flask` - Installs Flask for the project

## 2 - Using Windows

- Download and install Python from https://www.python.org/downloads/
- Python version = 3.11.2
- Clone practical repo (if haven't done so) and open in VSCode
- Install ‘RestClient’ extention in VSCode
- Run the following commands in the terminal.
- `python -m pip install --upgrade pip` - upgrades the package manager to latest version
- `pip install pipenv` - to manage the Python libraries. Equivalent of npm for Node. Combines the pip and venv commands into a single tool chain
- `pipenv --python` - Init Python virtual environment under project
- `pipenv install flask` - Install Flask framework

# Running the app on port 6400

The following command will run the app on port 6400.

`pipenv run flask --app todo run -p 6400`

     Note: If port is not avalilable then run the following
     in the terminal to clear the port.

**For WSL:**

- `fuser -k 6400/tcp` - kills process on this port
- https://stackoverflow.com/a/11596144

**For Windows:**

- `netstat -ano | findstr :<PORT>` - finds the Process ID (PID) -` taskkill /PID <PID> /F`
- https://stackoverflow.com/a/39633428

# Running tests locally

    Note: Don't commit any of the following changes made here for now.

The bash files that are under ./.csse6400/bin will have line ending issues
when running tests locally. In VSCode open each of the bash file, change
the line ending in VSCode from 'CRLF' to 'LF' and save one at a time.
This option to switch between line endings is available on the status bar
of VSCode.

#### Running the CI tests locally with the following commands:

Project structure: `bash ./.csse6400/bin/validate_structure.sh`

Clean repository: `bash ./.csse6400/bin/clean_repository.sh`

Health endpoint: ` bash ./.csse6400/bin/health.sh`

Unit tests: `bash ./.csse6400/bin/unittest.sh`

The 'RestClient' extention allows to run tests directly from
the endpoints.http file when the app is running.

# Commiting changes to GitHub

Note: On Windows, if using github desktop then token is not required
for access. Authentication is done through the browser. Other Git
clients will need a token that can be easily be created in the github account.
If using the second flow from above, where the latest windows version of python
(3.11.2) is causing the CI tests to fail in Github, remove the following line from
the Pipfile.

```
[requires]
python_version = "3.10"
python_full_version = "3.10.6"
```
