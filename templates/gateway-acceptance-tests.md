# Atlas Gateway Acceptance Tests

Use these checks after the first gateway implementation is running.

## 1. Manifest loads

Confirm Atlas can fetch the manifest successfully.

Expected:

- `200 OK`
- valid JSON
- manifest contains at least one action

## 2. Auth works

Confirm the gateway accepts the shared secret.

Expected:

- valid bearer token succeeds
- missing or wrong token fails cleanly

## 3. Read-only action works

Invoke one read-only action.

Expected:

- `status: completed`
- useful `outputText`
- useful `machineSummary`
- structured `data` if relevant

## 4. Async action works

If async is supported, invoke one async action.

Expected:

- `status: accepted`
- durable `jobId`
- working job status endpoint

## 5. Approval-required action works

If approvals are supported, invoke one approval-gated action.

Expected:

- `status: approval_required`
- stable `approvalId`
- clear reason

## 6. Atlas dashboard checks pass

Register the gateway in Atlas and run:

- sync check
- async check
- approval check

## 7. Real meeting test passes

Join a real Atlas meeting and ask for something that should call the gateway.

Expected:

- Atlas creates the task
- Atlas invokes the gateway
- result comes back into the room correctly
