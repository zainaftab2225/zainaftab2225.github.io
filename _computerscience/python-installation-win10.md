---
title: "Python Setup on Windows 10"
date: 2020-06-30
---

### Installing Python on Windows

1. Click [here](https://www.python.org/downloads/) to go to Python's download page.
2. Download and launch the latest version of the Python installer.
2. Select "Add Python --*version*-- to PATH".
4. Select a customized installation location for easier access to the Python folder.
5. Install and let the setup complete.

### Checking if Python is Installed Correctly

1. Open the file **'IDLE (Python --version--)'**.
2. Type in **'print("Hello World")'**. If the shell outputs 'Hello World', then Python is installed correctly.
3. You can also open the Windows Command Prompt and write **'python - -version'**. If the version is displayed, then Python installed correctly.

### Setting up the Atom Environment

A good editor for writing Python code is Atom. To download, install and setup Atom as your Python editor, follow these steps below:

1. Click [here](https://atom.io/) to go to Atom's download page.
2. Download and launch the latest version of Atom.
3. Click on **File** --> **Settings** --> **Install**
4. Search and install the '**Script**' package by rbgkrk. This will allow Python code to run on your Atom editor.
5. You can also install other packages and themes for QoL improvements.
6. Type in your Python code and press '**CTRL+SHIFT+B**' to run it.

**NOTE:** While Atom editor can run basic scripts, it can not take input from the user unless you are able to find the correct packages.

### Running a Python File

When you've written your code in a file such as **example.py**, you can do the following steps to run it:
1. Shift click on the Windows folder where the file exists.
2. Select from the drop-down list "Open Powershell window here".
3. Type "**python example.py" to run the file.


### Installing 'pygame' Package

1. After Python has installed successfully, open the Windows Command prompt and type in: **pip install pygame**
2. After it downloads, type **python** in the Command Window.
3. Then type in **import pygame**. If it successfully shows the version of the pygame package, then it has installed successfully.

**NOTE:** pip is the Python package manager.
