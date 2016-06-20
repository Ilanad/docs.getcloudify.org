---
layout: bt_wiki
title: maintenance-mode
category: Docs
draft: false
abstract: Cloudify's Command-Line Interface
weight: 20
---

The `cfy maintenance-mode` command is used to restrict REST access to the manager.

This is required, for instance, when upgrading a manager via the `cfy upgrade` or `cfy rollback` commands.

Putting the manager in maintenance mode prevents it from running any executions.


# Usage

### `cfy maintenance-mode activate`

Activate maintenance mode on the manager disallowing further REST requests.

#### Optional flags

* `--wait=false` - Wait until there are no running executions and automatically activate maintenance-mode.
* `timeout=SECONDS` - Operation timeout in seconds (The execution itself will keep going, but the CLI will stop waiting for it to terminate.)

### `cfy maintenance-mode deactivate` 

Deactivate maintenance mode on the manager to allow REST requests.

### `cfy maintenance-mode status`

#### Required flags

* `-f, --force=false` - This flag is required to perform the purge.

#### Optional flags

* `--backup-first=false` - Executes a `cfy logs backup` first.