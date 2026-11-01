# codeProxy UI context

This is an existing management product, not a redesign. Preserve the shared
slate/neutral surfaces, compact rounded controls, dark mode and current spacing.
Runtime styling belongs to the existing Tailwind classes and shared UI package.
Do not add a parallel theme or screen-specific design system.

The API-key workflow owns external access per key. Use the existing ToggleSwitch,
Modal, Select, DataTable and ToastProvider from `@code-proxy/ui`. New copy follows
the active en / zh-CN / ru locale. A text status accompanies semantic color.

External access is off by default. Enabling it requires saving the key, does not
publish management, and does not grant models/channels or remove quotas.
Do not copy this flag from a permission profile or enable it for old records.
Keep entered values after errors; no automatic re-submit or hidden permission
change. Keyboard and narrow-screen behavior follow the shared primitives.

Canonical behavior owners and verification are recorded in UX-CONTRACT.md.
