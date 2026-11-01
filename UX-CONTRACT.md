# Changed workflow: external API access

## Canonical UI Map

| Capability | Canonical owner | Source of truth | Allowed variants | Verification |
|---|---|---|---|---|
| Form | ApiKeyFormFields / ApiKeyFormModal | Existing shared primitive and workflow | Existing variants only | Component and browser tests: Existing modal, explicit Save, values retained on failure |
| Switch | @code-proxy/ui ToggleSwitch | Existing shared primitive and workflow | Existing variants only | Component and browser tests: Keyboard-operable, labelled, disabled during save, no autosave |
| Select/Listbox | @code-proxy/ui Select | Existing shared primitive and workflow | Existing variants only | Component and browser tests: Reuse existing permission-profile selection unchanged |
| Table Selection | @code-proxy/ui DataTable | Existing shared primitive and workflow | Existing variants only | Component and browser tests: Preserve column storage, internal overflow, loading and empty states |
| Status | ApiKeyColumns + i18n | Existing shared primitive and workflow | Existing variants only | Component and browser tests: Text Allowed/Closed, color is supplementary |
| Toast | @code-proxy/ui ToastProvider | Existing shared primitive and workflow | Existing variants only | Component and browser tests: Existing success/error handling; never include a key value |
| CRUD | ApiKeysPage + apiKeyEntriesApi | Existing shared primitive and workflow | Existing variants only | Component and browser tests: Create default false, edit reads current value, PATCH preserves other permissions |

Backend authorization is authoritative. A switch set to true is not a guarantee
that the key has a valid external model/channel/limit policy. Explain prerequisites
beside the switch. Do not change management authentication or other screens.

Verification: API-key component tests, full frontend CI tests, TypeScript/build,
and a browser test of create/edit, failed save, pending state, keyboard and a
narrow viewport using synthetic management responses.

## Static auditor caveat

The bundled auditor matches JSX `<Select>` as a native `<select>`. Both uses
reported in this scoped workflow import the maintained authored Select from
`@code-proxy/ui`; its portal/listbox implementation is verified in source and
browser. Preserve authored ownership rather than changing the contract or the
shared component to satisfy this false positive.
