# open-office.self

Selfware Open Office is a local-first demo runtime for the Selfware protocol.

## Repository Scope

This repository keeps the current protocol and runtime only.
Historic `v0.x` snapshot files are intentionally removed to avoid fragmented version docs.

## Main Files

- `selfware.md`: primary protocol document
- `selfware.en.md`: English protocol document
- `manifest.md`: runtime and packaging manifest
- `server.py`: local HTTP runtime and `.self` pack command
- `content/selfware_demo.md`: canonical Chinese content source
- `content/selfware_demo.en.md`: canonical English content source
- `views/`: projection views (self, doc, canvas, outline, mindmap, presentation, card)

## Quick Start

```bash
python server.py
```

Open:

- `http://127.0.0.1:8000/`

If port `8000` is occupied, the runtime will pick the next free local port.
You can also set a fixed port:

```bash
SELFWARE_PORT=8001 python server.py
```

## Pack to `.self`

```bash
python server.py pack ./OpenOffice.self
python server.py pack ./OpenOffice.self --yes
```

## Runtime Guardrails

- Localhost only (`127.0.0.1`)
- Write scope limited to `content/`
- Explicit confirmation required for high-impact actions (pack/publish/pull-merge/apply updates)
