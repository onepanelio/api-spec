## API Information 

Host: https://c.onepanel.io/api
Authentication header: Authorization: Bearer <jwt-token>


## Commands Overview

### Jobs

- [List Jobs](#list-jobs)
- [Create a Job](#create-a-job)
- [Get Job Log](#get-job-log)
- [Stop a job](#stop-a-job)

### Applications

- [Create an Application](#create-a-job)
- [Terminate an Application](#stop-a-job)

### Machine Types

- [List Machine Types](#list-machine-type)

### Environments

- [List Environments](#list-environments)

## Jobs

### List Jobs

#### CLI 

Command: `onepanel jobs list [--all]`

Response: 
```
 ID                                      COMMAND 
 0f9053b8-6d18-4385-91c5-10ca2183da8e    python mnist.py      
 e8f8dded-4794-4e6c-aee2-fc716cf93aac    python main.py
```

#### API Request and Response
Request (default): GET /accounts/<account_uid>/projects/<project_uid>/jobs?running=true

Request (--all): GET /accounts/<account_uid>/projects/<project_uid>/jobs

Response body example:

```
[
    {
        "uid": "0f9053b8-6d18-4385-91c5-10ca2183da8e",
        "command": "wget -q --load-cookies cookies.txt https://www.kaggle.com/c/cdiscount-image-classification-challenge/download/test.bson -P ../trainingset -nd && python predict.py",
        "startTime": null,
        "completionTime": null,
        "active": 0,
        "succeeded": 1,
        "failed": 0,
        "isRunning": true,
    },
    {
        "uid": "e8f8dded-4794-4e6c-aee2-fc716cf93aac",
        "command": "wget --load-cookies cookies.txt https://www.kaggle.com/c/cdiscount-image-classification-challenge/download/test.bson -P ../trainingset -nd && python predict.py",
        "startTime": null,
        "completionTime": null,
        "active": 0,
        "succeeded": 1,
        "failed": 0,
        "isRunning": true,
]
```

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

### List Machine Types

#### CLI 

Command: `onepanel machine_types list`

Response: 
```
 ID               SPECS 
 aws-cpu-1        CPU: 2, RAM: 7GB      
 aws-p2.xlarge    GPU: 1, CPU: 4, RAM: 60GB
```


#### API Request and Response
Request: GET /machine_types

Response example:

```
[
    {
        "uid": "aws-shared",
        "name": "CPU: 0.5, RAM: 860MB",
        "info": {
            "cpu": "0.5",
            "ram": "860MB"
        },
        "resources": {
            "cpu": "400m",
            "memory": "860Mi"
        },
        "cloudProvider": "aws"
    },
    {
        "uid": "aws-cpu-1",
        "name": "CPU: 2, RAM: 7GB",
        "info": {
            "cpu": "2",
            "ram": "7GB"
        },
        "resources": {
            "cpu": "1750m",
            "memory": "7Gi"
        },
        "cloudProvider": "aws"
    },
    {
        "uid": "aws-p2.xlarge",
        "name": "GPU: 1, CPU: 4, RAM: 60GB",
        "info": {
            "cpu": "4",
            "gpu": "1",
            "ram": "60GB"
        },
        "resources": {
            "cpu": "3500m",
            "gpu": "1",
            "memory": "59Gi"
        },
        "cloudProvider": "aws"
    }
]
```

## Environments

### List Environments

#### CLI 

Command: `onepanel environments list`

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
