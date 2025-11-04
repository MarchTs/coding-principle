# Error Handling Guidelines

## Overview
These guidelines define a consistent error-handling contract for services and clients. They categorize errors into four canonical types and standardize how error codes are constructed so downstream systems can reason about failures deterministically.

## Error Types
| Type | Description | Canonical Message Behavior |
| --- | --- | --- |
| **Application Error** | Domain validation failures or business-rule violations that must be transformed into user-facing responses the website can understand. | Provide localized, human-readable messages and actionable guidance. |
| **Logic Error** | Attempts to transition an entity into an illegal state (e.g., status change prohibited). | Return `409 Conflict` responses, include the current immutable state, and never mutate data. |
| **Service Error** | Data consistency problems such as duplicate entities or mismatched foreign keys (e.g., resource already exists). | Return `409 Conflict` or `422 Unprocessable Entity` depending on integration contracts; include identifiers that triggered the conflict. |
| **System Error** | Infrastructure or dependency failures (e.g., database connection failures, downstream service unreachable). | Return `500`-class responses, emit telemetry, and avoid exposing internal stack traces to clients. |

## Error Code Format
Compose error codes using the pattern `xxx-xxxx`, where the first segment represents the **mode** (operation) and the second segment captures the specific **error condition**.

- **Mode**: Three-letter shorthand for the feature or workflow, such as `REG` for registration, `CRT` for create product, or `GET` for get product.
- **Code**: Four-letter mnemonic for the precise failure cause, such as `NOPM` for "no permission", `ALRD` for "already exists", or `STPR` for "status change prohibited".

Example codes:
- `REG-NOPM` — Registration attempt denied due to missing permissions.
- `CRT-ALRD` — Create product request rejected because the entity already exists.
- `GET-STPR` — Get product operation blocked by a status change prohibition.

## Implementation Checklist
1. Map thrown exceptions to the four error types and ensure response serializers convert them to standardized payloads.
2. Include the `errorType`, `errorCode`, and `message` fields in every error response object.
3. Log system errors with full diagnostic context and correlate them with observability tooling.
4. Provide remediation guidance in application error responses when user action can resolve the issue.
