---
layout: bt_wiki
title: executions
category: Docs
draft: false
abstract: Cloudify's Command-Line Interface
weight: 40
---

The `cfy executions` command is used to manage workflow executions on a Cloudify manager.

You can use the command to start, cancel and and list executions. You can also get a single execution's info.


## Commands

### start

Usage: `cfy executions start [options] -d DEPLOYMENT_ID`

Start an workflow execution for a specific deployment 

#### Required flags

* `--allow-custom-parameters`
                        Allow passing custom parameters (which were not
                        defined in the workflow's schema in the blueprint) to
                        the execution
* `-d, --deployment-id=DEPLOYMENT_ID`
                        The deployment ID to execute the workflow on
* `-p, --parameters=PARAMETERS`
                        Parameters for the workflow execution (Can be provided
                        as wildcard based paths (*.yaml, etc..) to YAML files,
                        a JSON string or as "key1=value1;key2=value2"). This
                        argument can be used multiple times.
* `-f, --force`           Execute the workflow even if there is an ongoing
                        execution for the given deployment
* `--timeout=TIMEOUT`     Operation timeout in seconds (The execution itself
                        will keep going, but the CLI will stop waiting for it
                        to terminate) (default: 900)
* `-w, --workflow=WORKFLOW`
                        The workflow to execute
* `-l, --include-logs`    Include logs in returned events
* `--json`                Output events in a consumable JSON format


### cancel

Usage: `cfy executions cancel [options] -e EXECUTION_ID` 

Cancel 
#### Required flags

* `-e, --execution-id=EXECUTION_ID` - The ID of the execution to cancel

#### Optional flags

* `-f, --force` - Terminate the execution abruptly, rather than request an orderly termination


### get

Usage: `cfy executions get [options] -e EXECUTION_ID`

Retrieve information on a single execution.

#### Required flags

* `-e, --execution-id=EXECUTION_ID` - The ID of the execution to get

### list

Usage: `cfy executions list`

Lists all executions for a deployment.

#### Required flags

* `-d, --deployment-id=DEPLOYMENT_ID` - The deployment ID to list executions for

#### Optional flags

* `--system-workflows` - Include executions of system workflows
