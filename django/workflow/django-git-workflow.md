# Setup Github Actions for Django Project

#### Step 6

can see also on: https://www.codingforentrepreneurs.com/blog/django-github-actions/

or

https://docs.github.com/en/actions/using-workflows/manually-running-a-workflow

#### Step 1

In project root directory the create a folder called '.github'

#### Step 2

Create a file in the format workflows/django.yml

#### Step 3

Add the following snippet to the file
```yaml
name: Django CI

on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

jobs:
  build:

    runs-on: ubuntu-latest
    strategy:
      max-parallel: 4
      matrix:
        python-version: [3.6, 3.7, 3.8]

    steps:
    - uses: actions/checkout@v2
    - name: Set up Python ${{ matrix.python-version }}
      uses: actions/setup-python@v1
      with:
        python-version: ${{ matrix.python-version }}
    - name: Install Dependencies
      run: |
        python -m pip install --upgrade pip
        pip install -r ./web/requirements.txt
    - name: Run Tests'
      env:
        SECRET_KEY: 69tgugtg%^fgJO&*&  # some-test-key-not-good-for-prod
        DB_NAME: mydb
        DB_USER: userdb
        DB_PASSWORD: password
        DJANGO_ALLOWED_HOSTS: localhost 127.0.0.1 [::1]
        DEBUG_MODE: False
        TIME_ZONE: Africa/Bangui
        CACHE_KEY_PREFIX: Halo
      run: |
        python ./web/manage.py test
```

 #### Step 4

Do `git add . && git commit -m 'Add Django git workflow'`
then do `git push origin master(branch name)`

#### Step 5
 
Goto the github repository and click actions, when you do push or a pull request to the master branch it will be added as a job on git workflow.


 
#### *Happy Hacking.*