### Programming Language

Latest stable version of Python 3.x should be used.

### Framework
http://click.pocoo.org/5/

### API Specification

http://editor.swagger.io/?url=https://raw.githubusercontent.com/onepanelio/api-spec/master/swagger.yml

### Commands

#### `onepanel login`

Prompts for (both required):

```bash
Email:
Password:
```

Upon successful login, the returned info should be saved in ~/.onepanel/credentials as follows:

```yml
[default]
uid: <user.uid>
token: <session.token>
account_uid: <account.uid> 	
```


Upon a `422` response from API, the following message should be displayed:

```
Incorrect username or password
```

#### `onepanel projects create`

Prompts for (both required):

```bash
Name (<put current directory name here as default>):
Where should the project be created?
  1. Current directory
  2. New directory within current directory
Choose 1 or 2: 
```

If 1, create a `.onepanel-project` file with `uid` of project in it.
If 2, create a new directory and then create a `.onepanel-project` file with `uid` in it.


#### `onepanel projects list`

If there are projects present:

```
NAME        INSTANCES       JOBS
project-1   3               2
project-2   3               4
project-3   5               0
```

If there are no projects present:

```
No projects found.
```
