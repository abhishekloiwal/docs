# Atlas Gateway Builder Brief

Build a small HTTP service that implements the hosted Atlas Gateway Contract v1.

## Goal

Expose a narrow, safe gateway that Atlas can call for private context, workflows, or internal actions without giving Atlas direct access to downstream secrets.

## Required endpoints

- `GET /v1/manifest`
- `POST /v1/invoke`

Add these if you support async work:

- `GET /v1/jobs/{jobId}`
- `POST /v1/jobs/{jobId}/cancel`

## Auth

Use a shared secret that Atlas can send as:

`Authorization: Bearer <shared-secret>`

## First version requirements

- one read-only action
- clear `outputText` and `machineSummary`
- stable action names
- stable ids if you choose to include ids
- simple JSON schemas

## Good action examples

- `fetch_internal_context`
- `lookup_customer_record`
- `trigger_followup_workflow`
- `query_internal_agent`

## Avoid

- raw downstream model completion endpoints
- broad secret passthrough
- exposing many low-level internal APIs in the first version
- complex schema features for v1

## Deliverables

- runnable service
- manifest
- invoke handler
- sample curl requests
- tests for manifest and invoke
