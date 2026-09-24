# Forms Pattern

## Use when

The user must create or edit structured information.

## Practices

- group fields by user intent;
- distinguish required vs optional;
- validate close to the field;
- preserve valid input after errors;
- use sensible defaults;
- avoid asking for information the system already knows;
- use multi-step flow only when it reduces cognitive load.

## FAST DEMO

Build only the fields required for the critical scenario.

## MVP

Add:
- validation;
- autosave/draft where useful;
- empty/error states;
- accessibility;
- conditional fields.

## PRODUCT

Add:
- audit-sensitive confirmations;
- complex policy validation;
- localization;
- analytics on abandonment/error.
