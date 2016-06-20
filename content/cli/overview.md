---
layout: bt_wiki
title: Overview
category: Docs
draft: false
abstract: Cloudify's Command-Line Interface
weight: 1
---

Cloudify's Command-Line Interface is the default method for interacting with Cloudify and managing your applications. It allows you to execute workflows on your local machine as well as interact with a running [Cloudify Manager]({{< relref "manager/intro.md" >}}) (to ssh into a running Manager, upload blueprints, delete them, create deployments, execute workflows, retrieve events and more).

If you haven't already [installed Cloudify]({{< relref "installation/from-packages.md" >}}), now would be a good time to do so.

The interface can be accessed by running the `cfy` command. `cfy -h` will get you started:

{{< gsHighlight  bash  >}}
$ cfy -h
usage: cfy [-h] [--version]                       ...

Cloudify's Command Line Interface

optional arguments:
  -h, --help            show this help message and exit
  --version             show version information and exit

Commands:
                       
    logs                Handle the Manager's logs
    maintenance-mode    Handle the Manager's maintenance-mode
    snapshots           Handle snapshots on the Manager
    executions          Handle workflow executions
    agents              Handle a deployment's agents
    plugins             Handle plugins on the Manager
    recover             Recover the Manager
    use                 Control a specific Manager
    upgrade             Upgrade the Manager to a new version
    teardown            Teardown the Manager
    deployments         Handle deployments on the Manager
    init                Initialize a working environment in the current
                        working directory
    nodes               Handle a deployment's nodes
    local               Handle local environments
    events              Handle events
    status              Show the Manager's status
    rollback            Rollback the Manager upgrade
    ssh                 SSH to the Manager's host
    groups              Handle deployment groups
    workflows           Handle deployment workflows
    blueprints          Handle blueprints on the Manager
    bootstrap           Bootstrap a Manager
    node-instances      Handle node-instances
    dev                 Execute fabric tasks on the Manager
    install             Install an application via the Manager
    uninstall           Uninstall an existing application installed via a
                        Manager
{{< /gsHighlight >}}

A full `cfy` commands reference can be found [here]({{< relref "cli/reference.html" >}}).

Note that some features (such as viewing metric graphs and application topologies) are only available via the Web UI if running Cloudify Manager.