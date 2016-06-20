---
layout: bt_wiki
title: snapshots
category: Docs
draft: false
abstract: Cloudify's Command-Line Interface
weight: 30
---

The `cfy snapshots` command is used to manage data snapshots of a Cloudify manager.

You can use the command to create, upload, download, delete and list snapshots and also to restore a manager using a snapshot archive.


# Usage

### Create

Usage: `cfy snapshots create [options] -s SNAPSHOT_ID`

Create a snapshot of the manager.

#### Required Arguments

* `-s, --snapshot-id` - A user provided snapshot ID

#### Optional Arguments

* `--exclude-credentials` - Do not store credentials in the snapshot
* `--include-metrics` - Include metrics data in the snapshot

### Delete

Usage: `cfy snapshots delete -s SNAPSHOT_ID` 

### Download

Usage: `cfy snapshots download -s SNAPSHOT_ID`

### List

Usage: `cfy snapshots list` 

### Restore

Usage: `cfy snapshots restore -s SNAPSHOT_ID` 

### Upload

Usage: `cfy snapshots upload` 