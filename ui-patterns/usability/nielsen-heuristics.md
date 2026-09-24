# Nielsen Heuristics Baseline

The ten Nielsen heuristics are used as a baseline usability quality gate.

## Heuristics

1. Visibility of system status
2. Match between system and the real world
3. User control and freedom
4. Consistency and standards
5. Error prevention
6. Recognition rather than recall
7. Flexibility and efficiency of use
8. Aesthetic and minimalist design
9. Help users recognize, diagnose and recover from errors
10. Help and documentation

## DevPattern interpretation

The heuristics must be translated into observable UI behavior.

### UI-NH-01 — System status

Every asynchronous action must expose an appropriate state:

- idle;
- loading/progress;
- success;
- warning;
- error;
- retry/recovery where possible.

### UI-NH-02 — Real-world language

Use domain language familiar to the user rather than implementation terminology.

### UI-NH-03 — User control

Support cancel/back/undo where the operation allows it.

Irreversible actions must clearly communicate consequences.

### UI-NH-04 — Consistency

The same action, entity and state should use consistent labels and interaction patterns.

### UI-NH-05 — Error prevention

Prevent invalid or dangerous actions before relying on error messages.

### UI-NH-06 — Recognition

Prefer visible options, defaults and contextual help over requiring users to remember syntax or internal codes.

### UI-NH-07 — Efficiency

Support shortcuts, defaults, templates or batch actions when repeated use justifies them.

### UI-NH-08 — Minimalism

Primary tasks should not compete with unnecessary controls or information.

### UI-NH-09 — Error recovery

Errors should explain:
- what happened;
- what was affected;
- what the user can do next.

### UI-NH-10 — Help

Provide help where the task cannot be made self-explanatory.

## Quality-gate example

```yaml
ui_acceptance:
  - id: UI-NH-01
    rule: system_status_visible
    check: every_async_action_has_visible_state

  - id: UI-NH-05
    rule: error_prevention
    check: consequential_actions_have_prevention_or_confirmation

  - id: UI-NH-08
    rule: minimalist_design
    check: primary_task_has_no_unnecessary_controls
```

## Key rule

> Nielsen heuristics are not documentation; they are testable usability constraints.
