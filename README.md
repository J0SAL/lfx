## Description

The test suite aims to validate the behavior of the Kyverno policy lfx-add-labels by applying it to ConfigMap resources in different namespaces. The policy's purpose is to add the label lfx-mentorship: kyverno to ConfigMaps within namespaces that match the pattern "team-\*". The test consists of three steps, each focusing on different scenarios.

`01-policy.yaml:`

- Applies the Kyverno policy policy.yaml.
- Asserts the readiness of the policy using policy-ready.yaml.

`02-labels-updated.yaml:`

- Applies a ConfigMap (configmap1.yaml) in the team-1 namespace.
- Asserts that the ConfigMap has been updated with the label lfx-mentorship: kyverno using configmap1-assert.yaml.

`03-labels-not-updated.yaml:`

- Applies a ConfigMap (configmap2.yaml) in the joy namespace.
- Asserts that the ConfigMap does not have the label lfx-mentorship: kyverno using `configmap2-assert.yaml`.

## Expected Behavior

The expected behavior of the test is as follows:
`01-policy.yaml:`

- The Kyverno policy _lfx-add-labels_ is successfully applied.
- The policy becomes ready and passes the assertion in `policy-ready.yaml.`

`02-labels-updated.yaml:`

- The ConfigMap _lfx-configmap1_ in the **team-1** namespace is successfully applied.
- The ConfigMap is updated with the label lfx-mentorship: kyverno as asserted in `configmap1-assert.yaml.`

`03-labels-not-updated.yaml:`

- The ConfigMap _lfx-configmap2_ in the **joy** namespace is successfully applied.
- The ConfigMap does not have the label lfx-mentorship: kyverno as asserted in `configmap2-assert.yaml`.

## Reference Issue(s)

[#546](https://github.com/kyverno/policies/issues/546)
