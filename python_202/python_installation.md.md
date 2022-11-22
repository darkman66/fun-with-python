# with pyenv

libs (ubuntu)

```bash
sudo apt install -y wget build-essential libreadline-dev \
libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev \
libc6-dev libbz2-dev libffi-dev zlib1g-dev
```

# requirements

```
backports.shutil-get-terminal-size==1.0.0
blinker==1.4
bugsnag
```

create file

```
pip freeze > requirements.txt
```

install from file

```
pip install -r requirements.txt
```

* structure

```
# you can use comments in requirements file
pytest
pytest-cov
beautifulsoup4

# The syntax supported here is the same as that of requirement specifiers.
docopt==0.6.1 # you can specify specific version of library
requests[security] >= 2.8.1, == 2.8.* ; python_version < "2.7" # only when Python version is lower than 2.7
# you can install from external URL as zip file
urllib3 @ https://github.com/urllib3/urllib3/archive/refs/tags/1.26.8.zip

# you can refer to other requirements file(s)
-r some-other-requirements.txt

# It is possible to refer to specific local distribution paths.
./downloads/requests-1.0.2.whl

# It is possible to refer to URLs and hash/branch or tag version
-e git+https://github.com/psf/requests.git@v2.28.1#egg=requests
```

* conflicting packages

```
django >= 4.1.3
pillow <= 9.3.0
```

after install

```
Collecting django>=4.1.3
  Downloading Django-4.1.3-py3-none-any.whl (8.1 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 8.1/8.1 MB 447.2 kB/s eta 0:00:00
Collecting pillow<=9.3.0
  Downloading Pillow-9.3.0-cp38-cp38-manylinux_2_28_x86_64.whl (3.3 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 3.3/3.3 MB 318.4 kB/s eta 0:00:00
Collecting sqlparse>=0.2.2
  Downloading sqlparse-0.4.3-py3-none-any.whl (42 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 42.8/42.8 kB 271.2 kB/s eta 0:00:00
Collecting backports.zoneinfo
  Downloading backports.zoneinfo-0.2.1-cp38-cp38-manylinux1_x86_64.whl (74 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 74.0/74.0 kB 258.0 kB/s eta 0:00:00
Collecting asgiref<4,>=3.5.2
  Downloading asgiref-3.5.2-py3-none-any.whl (22 kB)
Installing collected packages: sqlparse, pillow, backports.zoneinfo, asgiref, django
Successfully installed asgiref-3.5.2 backports.zoneinfo-0.2.1 django-4.1.3 pillow-9.3.0 sqlparse-0.4.3

[notice] A new release of pip available: 22.2.2 -> 22.3.1
[notice] To update, run: pip install --upgrade pip
```