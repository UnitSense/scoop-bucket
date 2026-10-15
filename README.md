# UnitSense Scoop Bucket

Scoop bucket for [UnitSense Agent](https://github.com/UnitSense/agent).

> **Prefer the direct installer instead:** `irm https://app.unitsense.ai/install-agent.ps1 | iex`
> always installs the real latest release and has no prerequisites. This bucket's manifest
> is not reliably kept current (see note below) -- use it only if you specifically want
> Scoop-managed updates and are checking the installed version afterward.

## Usage

```powershell
scoop bucket add unitsense https://github.com/UnitSense/scoop-bucket
scoop install unitsense-agent
```

## Update

```powershell
scoop update unitsense-agent
```

Manifests in `bucket/` are *supposed* to be updated automatically on each release via
GoReleaser -- but this repo has no `bucket/` directory; the manifest Scoop actually reads
lives at the repo root (`unitsense-agent.json`). That mismatch is the likely reason this
manifest sat at v0.7.1 for ~4 months while the real agent moved to v0.7.4: the automation
may be writing to a path that doesn't exist here. Manually corrected 2026-10-15; the actual
fix (pointing GoReleaser's scoop config at the right path, or removing this doc's incorrect
`bucket/` claim) is still open -- see the `agent` repo's release config.
