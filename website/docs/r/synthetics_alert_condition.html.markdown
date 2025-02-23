---
layout: "newrelic"
page_title: "New Relic: newrelic_synthetics_alert_condition"
sidebar_current: "docs-newrelic-resource-synthetics-alert-condition"
description: |-
  Create and manage a Synthetics alert condition for a policy in New Relic.
---

# Resource: newrelic\_synthetics\_alert\_condition

Use this resource to create and manage synthetics alert conditions in New Relic.

-> **NOTE:** The [newrelic_nrql_alert_condition](nrql_alert_condition.html) resource is preferred for configuring alerts conditions. In most cases feature parity can be achieved with a NRQL query. Other condition types may be deprecated in the future and receive fewer product updates.

## Example Usage

```hcl
resource "newrelic_synthetics_alert_condition" "foo" {
  policy_id = newrelic_alert_policy.foo.id

  name        = "foo"
  monitor_id  = newrelic_synthetics_monitor.foo.id
  runbook_url = "https://www.example.com"
}
```

## Argument Reference

The following arguments are supported:

  * `policy_id` - (Required) The ID of the policy where this condition should be used.
  * `name` - (Required) The title of this condition.
  * `monitor_id` - (Required) The GUID of the Synthetics monitor to be referenced in the alert condition.
  * `runbook_url` - (Optional) Runbook URL to display in notifications.
  * `enabled` - (Optional) Set whether to enable the alert condition. Defaults to `true`.

```
Warning: This resource will use the account ID linked to your API key. At the moment it is not possible to dynamically set the account ID.
```

## Attributes Reference

In addition to all arguments above, the following attributes are exported:

  * `id` - The ID of the Synthetics alert condition.


## Import

Synthetics alert conditions can be imported using a composite ID of `<policy_id>:<condition_id>`, e.g.

```
$ terraform import newrelic_synthetics_alert_condition.main 12345:67890
```