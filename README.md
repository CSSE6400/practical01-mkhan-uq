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
	- ```sudo apt install python3``` - installs the latest python version (Python 3.10.6).
	- ```sudo apt install python3 - pip``` - installs the package manager
	- ```sudo apt install pipenv``` - to manage the Python libraries we need for this project
	- ```pipenv --python 3``` - Init Python environment under project root directory
	- ```pipenv install flask``` - Installs Flask for the project


## Running the app on port 6400
```pipenv run flask --app todo run -p 6400```

	Note: If port is not avalilable then run the following in the bash terminal
	to clear the port.
	
```fuser -k 6400/tcp``` - kills process on this port
https://stackoverflow.com/a/11596144


## Running Tests locally

	The bash files that are under ./.csse6400/bin will have line ending issues
	when running tests locally.  In VSCode open each of the bash file, change
	the line ending in VSCode from 'CRLF' to 'LF' and save one at a time. 
	This option to switch between line endings is available on the status bar
	of VSCode.

For the unittest.sh file, under the bin folder, replace the line 
```cp -r .csse6400/tests .``` with ```cp -r ./.csse6400/tests ./tests```

#### Running the CI tests locally with the following commands:

Project structure: ```bash ./.csse6400/bin/validate_structure.sh```
Clean repository: ```bash ./.csse6400/bin/clean_repository.sh```
Health endpoint: ``` bash ./.csse6400/bin/health.sh```
Unit tests: ```bash ./.csse6400/bin/unittest.sh```


## 2 - Using Windows

 **TODO** 

# Commiting changes to GitHub
	Note: On Windows, if using github desktop then token is not required 
	for access. Authentication is done through the browser.	Other Git 
	clients will need a token that can be easily be created in the github account.
	
	If using the second flow, where the latest windows version of python
	(3.11.2) is causing the CI tests to fail. Remove the following line from 
	the Pipfile.

``` 
[requires]
python_version = "3.10"
python_full_version = "3.10.6"
```
