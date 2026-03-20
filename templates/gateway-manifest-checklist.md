# Atlas Gateway Manifest Checklist

Use this checklist when generating or reviewing the gateway manifest.

## Top-level shape

The manifest should include:

- `version`
- `gateway`
- `agent`
- `actions`
- `callbacks`

## Gateway block

Include:

- `name`
- `url`
- auth details
- capabilities such as:
  - `asyncJobs`
  - `jobCallbacks`
  - `approvals`

## Agent block

Include descriptive metadata for the internal system behind the gateway:

- `id`
- `name`
- optional `description`

## Actions

For each action, include at least:

- `name`
- `description`

Recommended fields:

- `id`
- `title`
- `executionMode`
- `inputSchema`
- `outputSchema`
- `outputDescription`
- `requiresApproval`
- `sideEffectLevel`
- `idempotent`
- `scopes`
- `tags`

## Keep schemas simple

Prefer:

- `type`
- `properties`
- `required`
- `items`
- `enum`
- `additionalProperties`

Avoid for v1:

- `$ref`
- `oneOf`
- `anyOf`
- deep schema indirection
