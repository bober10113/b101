# go2rtc Nest Session-Fix

This folder preserves the B101 go2rtc Nest session-stability work for Frigate.

## Status

This is not a full GitHub fork of `AlexxIT/go2rtc`. The GitHub app available in this Codex session can write to `bober10113/b101`, but it does not currently show a writable `go2rtc` fork for `bober10113`.

The real source patch is based on:

```text
AlexxIT/go2rtc commit dc1685e9cf7a8c349181f20a1b4a44825ed394c5
```

The patch target is:

```text
pkg/nest/api.go
```

## Local Source Of Truth

The clean patch and review notes were generated locally at:

```text
C:\Users\nufan\Documents\Frigate go2rtc\b101-nest-sessionfix-clean.lf.patch
C:\Users\nufan\Documents\Frigate go2rtc\b101-nest-sessionfix-review-notes.md
C:\Users\nufan\Documents\Frigate go2rtc\b101-nest-sessionfix-clean-api.go
```

The original working dirty diff was:

```text
C:\Users\nufan\Desktop\go2rtc-fork-work\b101-nest-sessionfix-full-dirty-diff-for-codex-20260529-103134.txt
```

## Patch Intent

The Nest patch is intended to reduce Google Nest/go2rtc restart storms inside Frigate by:

- avoiding shared mutable Nest API stream state across cameras
- storing OAuth credentials on per-stream API objects
- serializing Google SDM command calls
- adding deterministic per-camera jitter to stream extension timing
- retrying controlled transient statuses in stream generation/extension paths
- backing off instead of tight-looping after extension failures
- cleaning up HTTP response bodies and timer lifecycle

## Important Guardrail

The currently working Frigate binary at `/config/go2rtc` must not be replaced unless explicitly approved.

Build/test should create a separate binary first, then review the diff and health checks before any install.
