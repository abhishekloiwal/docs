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

## Prefer strict-safe input schemas

If possible, shape action `inputSchema` so Atlas can expose it as a typed tool directly.

Best practice:

- root schema is always `type: object`
- set `additionalProperties: false`
- include `required: []` for no-input actions
- for optional fields, prefer nullable required fields

Examples:

No-input action:

```json
{
  "type": "object",
  "properties": {},
  "required": [],
  "additionalProperties": false
}
```

Optional string field:

```json
{
  "type": "object",
  "properties": {
    "date": {
      "type": ["string", "null"]
    }
  },
  "required": ["date"],
  "additionalProperties": false
}
```

This is not required on day one, but it is the cleanest format going forward.
