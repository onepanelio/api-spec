### Programming Language

Latest stable version of Python 3.x should be used.

### Framework
http://click.pocoo.org/5/

### API Specification

http://petstore.swagger.io/?url=https://raw.githubusercontent.com/onepanelio/specs/master/swagger.yml

### Commands

#### `onepanel-cli login`

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


#### `onepanel-cli projects list`

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