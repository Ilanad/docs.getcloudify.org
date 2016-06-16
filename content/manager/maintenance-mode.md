---
layout: bt_wiki
title: Maintenance Mode
category: Manager
draft: false
weight: 900

---

## Overview

Maintenance-Mode is a state in which the Cloudify Manager rejects all requests, and doesn't perform any action (exceptions are detailed [here](#activated)).
This mode is useful when it is necessary for the Manager to remain in the exact same state for a certain period of time, such as during the ‘Manager Upgrade' process.

{{% gsNote title="Entering Maintenance-Mode" %}}
Maintenance-Mode will not be activated while there are active executions (running, pending, cancelling etc.) in the background. If an attempt to activate Maintenance-Mode
is made while there are active executions, the Cloudify Manager will enter the 'activating' state (as detailed below).
{{% /gsNote %}}

## States of Maintenance

The Cloudify Manager has three possible maintenance states: activated, activating, and deactivated.
In order to see the current maintenance state of the Manager, run `cfy maintenance-mode status`. The state will also be shown when running `cfy status` (providing that it is not deactivated).

### Activated
The Cloudify Manager is under maintenance. It ignores all requests except for `cfy status`, `cfy --version` and sub-commands of `cfy maintenance-mode`.
The Manager will not enter this state while there are active executions (running, pending, cancelling etc.) in the background, instead, it will enter the 'activating' state.
### Activating
This is a special state in which the Cloudify Manager is not fully in maintenance mode; only requests that trigger executions will be blocked.
This state allows active executions to complete and prevents new executions from being started.
Once all executions have completed/terminated, the Manager will enter the 'activated' state.
### Deactivated
The Cloudify Manager operates regularly. No requests are blocked.

## Usage
By default, the Maintenance-Mode state is 'deactivated'.
In order to activate Maintenance-Mode, run `cfy maintenance-mode activate`. The Cloudify Manager will either enter 'activated' state or 'activating' state.

In order to see the current status of the Maintenance-Mode, run `cfy maintenance-mode status`.

After the activation request, if there are no active executions, Maintenance-Mode is activated:
{{< gsHighlight  bash  >}}
Maintenance Mode Status:
	Status:	activated
	Activated At: <time of activation>
	Activation Requested At: <time of activation request>
{{< /gsHighlight >}}
However, if there are active executions, this message will be shown:
{{< gsHighlight  bash  >}}
Maintenance Mode Status:
	Status:	activating
	Activation Requested At: <time of activation request>

Cloudify Manager currently has <number of active executions> running or pending executions. Waiting for them to finish before activating.
{{< /gsHighlight >}}
{{% gsNote title="Executions' details" %}}
Running the Maintenance-Mode status command in verbose mode would provide detailed information about the current active executions.
{{% /gsNote %}}

Run `cfy maintenance-mode deactivate` to deactivate Maintenance-Mode.