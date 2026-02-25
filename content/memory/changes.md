---
selfware:
  role: memory_changes
  title: "Change Records"
  purpose: "对本实例的每次变更记录元数据（可审计、可协作、可回滚）。"
  scope: "记录协议/数据/运行时/视图/资源等变更；内容可简短但必须可追溯。"
  update_policy: append_only
  owner: user
  created_at: "2026-02-21T10:27:24Z"
  updated_at: "2026-02-21T14:44:44Z"
---

# Change Records

## Template

```yaml
id: "chg-YYYYMMDD-HHMMSS-xxx"
timestamp: "YYYY-MM-DDThh:mm:ssZ"
actor: "user|agent|service"
intent: "add_memory|update_protocol|fix_overflow|pack|..."
paths:
  - "path/to/file"
summary: "What changed and why (human readable)."
rollback_hint: "git revert <ref> | restore backups/<file>.<stamp>-nonememory | manual steps"
notes: "optional"
```

---

## id: chg-20260221-182724-memory

```yaml
id: "chg-20260221-182724-memory"
timestamp: "2026-02-21T10:27:24Z"
actor: "agent"
intent: "add_memory"
paths:
  - "selfware.md"
  - "content/selfware_demo.md"
  - "manifest.md"
  - "content/memory/chat.md"
  - "content/memory/decisions.md"
  - "content/memory/changes.md"
  - "backups/selfware.md.20260221-182724-nonememory"
  - "backups/manifest.md.20260221-182724-nonememory"
  - "backups/selfware_demo.md.20260221-182724-nonememory"
summary: "Add optional multi-file Memory module guidance to protocol; add demo memory files with self-description metadata; create -nonememory backups before change."
rollback_hint: "Restore backups/*-nonememory files back to their original paths."
notes: "Demo memory files use YAML front matter; change records are append-only."
```

---

## id: chg-20260221-193301-ecosystem

```yaml
id: "chg-20260221-193301-ecosystem"
timestamp: "2026-02-21T11:33:01Z"
actor: "agent"
intent: "update_protocol_ecosystem"
paths:
  - "selfware.md"
  - "content/selfware_demo.md"
  - "content/memory/decisions.md"
  - "content/memory/changes.md"
  - "manifest.md"
summary: "Promote Memory change logging to MUST; add optional Ecosystem module to protocol defining artifacts, metadata, publish/consume boundaries, and ecosystem repo directory convention (applies to ecosystem repos only)."
rollback_hint: "Restore backups/*-nonememory for pre-memory baseline; otherwise use git revert (if repo initialized) or manually revert the sections added in the listed paths."
notes: "Artifact trust metadata remains optional to avoid complexity; consumption decisions remain local (no silent apply)."
```

---

## id: chg-20260221-194408-artifact-sha256

```yaml
id: "chg-20260221-194408-artifact-sha256"
timestamp: "2026-02-21T11:44:08Z"
actor: "agent"
intent: "tighten_ecosystem_metadata"
paths:
  - "selfware.md"
  - "content/selfware_demo.md"
  - "content/memory/decisions.md"
  - "content/memory/changes.md"
summary: "Make ecosystem artifact integrity explicit by requiring `sha256` in artifact metadata; keep `distribution` mostly free text with basic parseability constraints and recommended prefixes."
rollback_hint: "Manually revert the added sha256 requirements in selfware.md 11.2 and the mirrored line in content/selfware_demo.md; remove the corresponding decision/change records if needed."
notes: "Trust metadata remains optional; verification uses sha256 as the minimal integrity anchor."
```

---

## id: chg-20260221-201422-protocol-thesis

```yaml
id: "chg-20260221-201422-protocol-thesis"
timestamp: "2026-02-21T12:14:22Z"
actor: "agent"
intent: "strengthen_protocol_opening"
paths:
  - "selfware.md"
  - "content/selfware_demo.md"
  - "content/memory/changes.md"
summary: "Replace the opening sentence with a stronger thesis block: “A file is an app. Everything is a file.” and a concise definition of Selfware as the Agent-era unified file protocol."
rollback_hint: "Revert the opening blockquote in selfware.md and content/selfware_demo.md to the previous single-sentence opening."
notes: "Kept as blockquote for visual emphasis; protocol meaning unchanged."
```

---

## id: chg-20260221-204322-self-analysis

```yaml
id: "chg-20260221-204322-self-analysis"
timestamp: "2026-02-21T12:43:22Z"
actor: "agent"
intent: "add_self_analysis_module"
paths:
  - "selfware.md"
  - "content/selfware_demo.md"
  - "content/memory/decisions.md"
  - "content/memory/changes.md"
summary: "Add optional Self‑Analysis module to protocol: defines inputs, file-based outputs, consent loop with Discovery/ecosystem, and leaves triggers to agent freedom while requiring explicit user-trigger support."
rollback_hint: "Manually remove the Self‑Analysis section from selfware.md and its mirror in content/selfware_demo.md; remove the linked decision/change records if needed."
notes: "Self‑Analysis outputs must remain within instance write scope and always produce Change Records."
```

---

## id: chg-20260221-204703-local-git

```yaml
id: "chg-20260221-204703-local-git"
timestamp: "2026-02-21T12:47:03Z"
actor: "agent"
intent: "enable_local_versioning"
paths:
  - ".gitignore"
  - "content/memory/changes.md"
summary: "Initialize local Git versioning workflow by adding a .gitignore baseline (output/ caches, common build artifacts)."
rollback_hint: "If needed, remove .gitignore and delete the .git directory after initialization; otherwise use git history to revert."
notes: "This record is written before running git init/commit; the git operations are the next step requested by the user."
```

---

## id: chg-20260221-205409-capabilities

```yaml
id: "chg-20260221-205409-capabilities"
timestamp: "2026-02-21T12:54:09Z"
actor: "agent"
intent: "declare_runtime_capabilities"
paths:
  - "selfware.md"
  - "manifest.md"
  - "content/selfware_demo.md"
  - "server.py"
  - "content/memory/changes.md"
summary: "Add Capability Declaration to protocol and demo: runtime must declare write scope, confirmation-required actions, endpoints, and module status; implement GET /api/capabilities and print a startup capability summary."
rollback_hint: "Revert the additions in selfware.md Runtime API, manifest.md Capability Declaration section, and remove /api/capabilities from server.py; keep other protocol content unchanged."
notes: "Capabilities are declarative only; they do not auto-execute privileged actions."
```

---

## id: chg-20260221-210808-self-page

```yaml
id: "chg-20260221-210808-self-page"
timestamp: "2026-02-21T13:08:08Z"
actor: "agent"
intent: "add_self_dashboard"
paths:
  - "views/self.html"
  - "server.py"
  - "js/view-switcher.js"
  - "manifest.md"
  - "selfware.md"
  - "content/memory/changes.md"
summary: "Add a read-only Self dashboard view (canonical + capabilities + manifest), change root redirect to /views/self.html, add Self to view switcher, and document git rollback-point guidance for change records."
rollback_hint: "git revert HEAD"
notes: "Self view is read-only; privileged actions remain agent-mediated with user confirmation."
```

---

## id: chg-20260221-211004-agent-prompting

```yaml
id: "chg-20260221-211004-agent-prompting"
timestamp: "2026-02-21T13:10:04Z"
actor: "agent"
intent: "tighten_agent_interaction"
paths:
  - "selfware.md"
  - "manifest.md"
  - "server.py"
  - "content/memory/changes.md"
summary: "Add an explicit MUST rule: when a capability is supported but not enabled / missing config / has strategy branches, the agent must proactively ask the user before any write or outbound request; surface the policy in /api/capabilities."
rollback_hint: "git revert HEAD"
notes: "This strengthens interactive clarity for users and provides better context for other agents."
```

---

## id: chg-20260221-211432-protocol-order

```yaml
id: "chg-20260221-211432-protocol-order"
timestamp: "2026-02-21T13:14:32Z"
actor: "agent"
intent: "reorder_protocol_sections"
paths:
  - "selfware.md"
  - "content/selfware_demo.md"
  - "content/memory/changes.md"
summary: "Improve protocol readability: move Sharing next to Packaging (as 9.4), move Non‑Normative to the end (appendix), and clarify Git collaboration wording to emphasize content/ as the collaboration write target."
rollback_hint: "git revert HEAD"
notes: "This is an editorial/structure change; normative rules remain the same."
```

---

## id: chg-20260221-212444-memory-timestamps

```yaml
id: "chg-20260221-212444-memory-timestamps"
timestamp: "2026-02-21T13:24:44Z"
actor: "agent"
intent: "tighten_memory_metadata"
paths:
  - "content/memory/chat.md"
  - "content/memory/decisions.md"
  - "content/memory/runs.md"
  - "content/memory/changes.md"
summary: "Tighten memory file metadata and entries to second-level timestamps (ISO-8601 Z) to match changes.md granularity; update created_at/updated_at and entry headings."
rollback_hint: "git revert HEAD"
notes: "Decision timestamps follow the related change record times for consistency (e.g., ecosystem/sha256/self-analysis)."
```

---

## id: chg-20260221-214921-memory-created-at

```yaml
id: "chg-20260221-214921-memory-created-at"
timestamp: "2026-02-21T13:49:21Z"
actor: "agent"
intent: "fix_memory_metadata"
paths:
  - "content/memory/changes.md"
summary: "Align content/memory/changes.md front-matter created_at with the first recorded change timestamp (second-level granularity)."
rollback_hint: "git revert HEAD"
notes: "Keeps memory metadata consistent across files."
```

---

## id: chg-20260221-220137-demo-doc

```yaml
id: "chg-20260221-220137-demo-doc"
timestamp: "2026-02-21T14:01:37Z"
actor: "agent"
intent: "update_demo_document"
paths:
  - "content/selfware_demo.md"
  - "content/memory/changes.md"
summary: "Update demo document to reflect current runtime entry (/ -> /views/self.html) and align section order (move Non‑Normative to the end, keep Sharing within Packaging as 9.4)."
rollback_hint: "git revert HEAD"
notes: "Keeps demo doc consistent with root protocol structure and the current runtime behavior."
```

---

## id: chg-20260221-223102-doc-view

```yaml
id: "chg-20260221-223102-doc-view"
timestamp: "2026-02-21T14:31:02Z"
actor: "agent"
intent: "add_doc_view"
paths:
  - "views/doc.html"
  - "views/self.html"
  - "js/view-switcher.js"
  - "manifest.md"
  - "views/canvas.html"
  - "views/outline.html"
  - "views/mindmap.html"
  - "views/presentation.html"
  - "views/card.html"
  - "content/memory/changes.md"
summary: "Add Doc view for linear reading (markdown render), link it from Self Dashboard, add it to view switcher menu, document entry point in manifest, and bump view-switcher cache version across views to expose the new view everywhere."
rollback_hint: "git revert HEAD"
notes: "Doc view reads Canonical Data via /api/content; editing remains via global editor (agent-mediated actions still require confirmation)."
```

---

## id: chg-20260221-224444-self-doc-polish

```yaml
id: "chg-20260221-224444-self-doc-polish"
timestamp: "2026-02-21T14:44:44Z"
actor: "agent"
intent: "polish_views"
paths:
  - "views/self.html"
  - "views/doc.html"
  - "content/memory/changes.md"
summary: "Polish Self and Doc views styling/layout for clearer navigation and readability."
rollback_hint: "git revert HEAD"
notes: "No behavior change; UI-only adjustments."
```

---

## id: chg-20260225-155639-doc-history-sync

```yaml
id: "chg-20260225-155639-doc-history-sync"
timestamp: "2026-02-25T15:56:39Z"
actor: "agent"
intent: "docs_cleanup_and_history_sync"
paths:
  - "README.md"
  - "selfware.v0.2.md"
  - "selfware.v0.2.zh.md"
  - "selfware.v0.3.md"
  - "selfware.v0.3.zh.md"
  - "content/memory/changes.md"
summary: "Add repository README, remove fragmented v0.x snapshot protocol files, and sync git history to the append-only change records."
rollback_hint: "git revert HEAD"
notes: "Current repository keeps a single current protocol line (`selfware.md` / `selfware.en.md`) without parallel v0.x snapshot files."
```
