Dev env - __mac os x__
Python 3.4 

__Download python 3.4__ for mac os and install:
[https://www.python.org/downloads/release/python-343/](https://www.python.org/downloads/release/python-343/)

__Python VirtualEnv__
Run following command in terminal(if cannot find virtualenv, reopen terminal and try again):
```
$ pip3 install virtualenv virtualenvwrapper
$ virtualenv --python=python3.4 ~/vp34    
```
This will create a “vp34” directory in your home directory. To activate this virtualenv, run:
```
$ source ~/vp34/bin/activate
```
You can check the python version by this command:
```
$ python --version 
```
__Python packages__
Install homebrew 
  http://brew.sh/

install Django
```
$ pip install Django==1.10.7
$ pip install djangorestframework==3.6.2
```
check whether we install Django successfully
```
$ python
>>> import django
>>> django.VERSION
(1, 8, 16, 'final', 0)
>>> 
>>> django.get_version()
'1.8.16'
```
We use pip to install Python packages. 
```
$ pip install -r depythov-requirements.txt
$ pip install -r src/requirements.txt
```