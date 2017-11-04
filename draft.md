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

### Create a Job

#### CLI 

Command: `onepanel jobs create --machine-type=<machine-type-uid> --environment=<instance-template-uid> '<command>'`

Response: <job_uid>


#### API Request and Response
Request: POST /accounts/<account_uid>/projects/<project_uid>/jobs

Request body example:
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

Response body example:

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

## Machine Types

## Environments

### Get Environments

#### CLI 

Command: `onepanel machine_types list`

Response: 
```
 ID                         ENVIRONMENT 
 jupyter-py3-tf1.3.0        Python 3, TensorFlow 1.3, Jupyter 5.1.0       
 jupyter-py3-pytorch0.2.0   Python 3, PyTorch 0.2.0, Jupyter 5.1.0
 jupyter-py3-caffe1.0       Python 3, Caffe 1.0, Jupyter 5.1.0
```


#### API Request and Response
Request: GET /instance_templates?instance_type=mod

Response example:

```
[
    {
        "uid": "jupyter-py3-tf1.3.0",
        "name": "Python 3, TensorFlow 1.3, Jupyter 5.1.0",
        "instanceType": "mod",
        "icons": [
            "python",
            "tensorflow",
            "keras",
            "jupyter"
        ]
    },
    {
        "uid": "jupyterlab-py3-tf1.3.0",
        "name": "Python 3, TensorFlow 1.3, JupyterLab 0.28.0rc2",
        "instanceType": "mod",
        "icons": [
            "python",
            "tensorflow",
            "keras",
            "jupyter"
        ]
    },
    {
        "uid": "jupyter-py3-pytorch0.2.0",
        "name": "Python 3, PyTorch 0.2.0, Jupyter 5.1.0",
        "instanceType": "mod",
        "icons": [
            "python",
            "pytorch",
            "jupyter"
        ]
    }
]
```
