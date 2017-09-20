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

Note that `Name` currently maps to `uid` in API and requires the following validation:

- 3 to 25 characters
- Alphanumeric characters or '-', must start and end with an alphanumeric character (regex: /^[a-z0-9]([-a-z0-9]*[a-z0-9])?$/)

If 1, create a `.onepanel-project`.
If 2, create a new directory and then create a `.onepanel-project`

content of `.onepanel-project`:

```yml
uid: <project.uid>
account_uid: <account.uid>
```


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
