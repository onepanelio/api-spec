## API Information 

Host: https://c.onepanel.io/api
Authentication header: Authorization: Bearer <jwt-token>


## Commands Overview

### Jobs

- [Create a Job](#create-a-job)
- [Get Job Log](#get-job-log)
- [Stop a job](#stop-a-job)

### Applications

- [Create an Application](#create-a-job)
- [Terminate an Application](#stop-a-job)

### Machine Types

- [Get Machine Types](#get-machine-type)

### Environments

- [Get Environments](#get-environments)

## Jobs

#### Create a Job

##### CLI 

command: `onepanel jobs create --machine-type=<machine-type-uid> --environment=<instance-template-uid> '<command>'`

response: <job_uid>


##### API Request and Response
URL: /accounts/<account_uid>/projects/<project_uid>/jobs

Request example:
```
{
  "command": "python mnist.py",
  "machineType": {
    "uid": "aws-shared"
  },
  "instanceTemplate": {
    "uid": "jupyter-py3-tf1.3.0"
  }
}
```

Response example:

```
{
    "uid": "493daef5-9eb4-4355-ae0f-36cf03fb0277",
    "command": "ls .",
    "startTime": "2017-11-02T16:24:36.883288Z",
    "completionTime": null,
    "active": 1,
    "succeeded": 0,
    "failed": 0,
    "isRunning": false,
    "log": ""
}
```
