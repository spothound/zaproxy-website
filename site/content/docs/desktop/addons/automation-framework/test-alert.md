---
# This page was generated from the add-on.
title: Automation Framework - Alert Job Test
type: userguide
weight: 11
---

# Automation Framework - Alert Job Test

Alert tests are supported by the activeScan and passiveScan-wait jobs. These tests can be used to validate the presence/absence of specific alerts in the active/passive scan. It is mandatory for the alerts specified in the plan to have a scanRuleId, against which the generated alerts will always be matched. All other fields describing an alert are optional regexes, and will be matched against only if they are specified.

A job can have tests for multiple alerts, and multiple tests can be created for alerts having the same scanRuleId.

## YAML

```
  jobs:
  - type: activeScan                   # The active scanner - this actively attacks the target so should only be used with permission
    parameters:
      context:                         # String: Name of the context to attack, default: first context
      policy:                          # String: Name of the scan policy to be used, default: Default Policy
      maxRuleDurationInMins:           # Int: The max time in minutes any individual rule will be allowed to run for, default: 0 unlimited
      maxScanDurationInMins:           # Int: The max time in minutes the active scanner will be allowed to run for, default: 0 unlimited
    tests:
      - name: 'test one'                       # Name of the test, optional
        type: alert                            # Specifies that the test is of type 'alert'
        action: passIfPresent/passIfAbsent     # String: The condition (presence/absence) of the alert, default: passIfAbsent  
        scanRuleId:                            # Integer: The id of the scanRule which generates the alert, mandatory  
        alertName:                             # String: The name of the alert generated, optional
        url: http://www.example.com/path       # String: The url of the request corresponding to the alert generated, optional
        method:                                # String: The method of the request corresponding to the alert generated, optional
        attack:                                # String: The actual attack which generated the alert, optional
        param:                                 # String: The parameter which was modified to generate the alert, optional
        evidence:                              # String: The evidence corresponding to the alert generated, optional
        confidence:                            # String: The confidence of the alert, one of 'False Positive', 'Low', 'Medium', 'High', 'Confirmed', optional
        risk:                                  # String: The risk of the alert, one of 'Informational', 'Low', 'Medium', 'High', optional
        otherInfo:                             # String: Additional information corresponding to the alert, optional
        onFail: 'info'                         # String: One of 'warn', 'error', 'info', mandatory
  
```
