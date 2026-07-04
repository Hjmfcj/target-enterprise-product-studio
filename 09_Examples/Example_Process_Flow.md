# Example Process Flow (Sanitized)

## Purpose
Illustrates AS-IS/TO-BE Mermaid diagram conventions using a generic, non-confidential scenario.

## Scope
Covers a generic 'Purchase Order Approval' example scenario only.

## Intended Usage
Use as a formatting reference for future process flow diagrams.

## Example Diagram

```mermaid
flowchart TD
A[Start] --> B[PO Submitted]
B --> C[Manager Review]
C --> D[Approved]
C --> E[Rejected]
D --> F[PO Issued]
E --> G[Requester Notified]
```

## Future Expansion
Will be expanded with a matching swimlane-style diagram example.
