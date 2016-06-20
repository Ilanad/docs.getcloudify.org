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


# Usage

### Start

Usage: `cfy executions start`

#### Required flags

  `--allow-custom-parameters`
                        Allow passing custom parameters (which were not
                        defined in the workflow's schema in the blueprint) to
                        the execution
  `-d DEPLOYMENT_ID, --deployment-id DEPLOYMENT_ID`
                        The deployment ID to execute the workflow on
  `-p PARAMETERS, --parameters PARAMETERS`
                        Parameters for the workflow execution (Can be provided
                        as wildcard based paths (*.yaml, etc..) to YAML files,
                        a JSON string or as "key1=value1;key2=value2"). This
                        argument can be used multiple times.
  `-f, --force`           Execute the workflow even if there is an ongoing
                        execution for the given deployment
  `--timeout TIMEOUT`     Operation timeout in seconds (The execution itself
                        will keep going, but the CLI will stop waiting for it
                        to terminate) (default: 900)
  `-w WORKFLOW, --workflow WORKFLOW`
                        The workflow to execute
  `-l, --include-logs`    Include logs in returned events
  `--json`                Output events in a consumable JSON format


### Cancel

Usage: `cfy executions cancel [options]` 


#### Optional flags

* `-o, --output=OUTPUT_PATH` - The output path for the downloaded file.


### Get

Usage: `cfy executions get [options] -f`

#### Required flags

* `-f, --force` - This flag is required to perform the purge.

#### Optional flags

* `--backup-first` - Executes a `cfy executions backup` first.


### List

Usage: `cfy executions list`