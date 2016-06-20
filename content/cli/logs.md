---
layout: bt_wiki
title: logs
category: Docs
draft: false
abstract: Cloudify's Command-Line Interface
weight: 10
---

The `cfy logs` command is used to manage log files on a Cloudify manager.

You can use the command to download, backup and purge a manager's service logs.
To use the command you must have the credentials (user and key) set in the local context and must `cfy use -t MANAGEMENT_IP` prior to running the command.


# Usage

### Backup

Usage: `cfy logs backup`

Create a backup of all log files on the manager stored under `/var/log/cloudify` and the output of `journalctl` and stores them under `/var/log/cloudify-manager-logs_MANAGER_DATE_MANAGER_IP.tar.gz`


### Download

Usage: `cfy logs download [options]` 

Create an archive containing the manager's logs and download them. The output file will contain the same content as with `cfy logs backup`.

#### Optional flags

* `-o, --output=OUTPUT_PATH` - The output path for the downloaded file.


### Purge

Usage: `cfy logs purge [options] -f`

{{% gsNote title="Warning" %}}
USE WITH CARE! Log files in Cloudify manager are rotated. This is a safety measure in case the disk space on the manager runs out for some reason.
{{% /gsNote %}}

Purge all log files on the manager.

#### Required flags

* `-f, --force` - This flag is required to perform the purge.

#### Optional flags

* `--backup-first` - Executes a `cfy logs backup` first.