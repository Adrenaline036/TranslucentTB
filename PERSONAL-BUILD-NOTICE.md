# PERSONAL BUILD NOTICE

This is **not** the official TranslucentTB release. It is a personal fork used to produce
custom builds for a single user's own machine.

---

## Provenance of the code in this repository

| Item | Value |
|---|---|
| Upstream project | [TranslucentTB/TranslucentTB](https://github.com/TranslucentTB/TranslucentTB) |
| License | **GPL-3.0** (see [`LICENSE.md`](LICENSE.md), unmodified) |
| Base version | upstream `2026.2`, commit `d4636e439865df0a1a1419db408e055740ce5c74` |
| Fork parent | [Lin-Feng-Liu/TranslucentTB](https://github.com/Lin-Feng-Liu/TranslucentTB) |
| Additional commit | `dff773e112ab416643387bb99b293b5fb2e186b0` |

### The one functional change in this fork

Commit `dff773e` — *"feat: use maximized appearance when windows fill the work area"* —
**was written by [@Lin-Feng-Liu](https://github.com/Lin-Feng-Liu)**, not by the owner of this
fork. It is carried here unmodified, with the original authorship intact in the git history:

```
Author: Lin-Feng-Liu <3539545893@qq.com>
Date:   Fri Sep 25 11:23:35 2026 +0800
SHA:    dff773e112ab416643387bb99b293b5fb2e186b0
```

Its purpose is to make TranslucentTB apply the *maximized window* appearance when ordinary
(non-maximized) windows collectively cover the entire monitor work area — for example a
side-by-side or 2×2 snap layout. Upstream only checks `IsZoomed()`, so snapped layouts
otherwise leave the taskbar transparent.

The change touches three files:

- `TranslucentTB/taskbar/taskbarattributeworker.hpp` — declares `IsWorkAreaCovered()`
- `TranslucentTB/taskbar/taskbarattributeworker.cpp` — sweep-line rectangle-union coverage test
- `.github/workflows/build.yml` — CI used to produce a downloadable portable build

### Discussion of the change upstream

- Issue: [TranslucentTB#116 — "dynamic window state should support windows split with aero snap"](https://github.com/TranslucentTB/TranslucentTB/issues/116)
  (open, labelled `help wanted`)
- The fork's parent is the origin of the implementation.

---

## Why this fork exists

Upstream does not ship this behaviour, and the author's original fork only retains CI build
artifacts for a few days. This fork exists solely so the owner can rebuild the patched
portable binary whenever needed, without depending on someone else's expiring artifacts.

## License and attribution

- This repository is distributed under **GPL-3.0**, the same license as upstream.
  [`LICENSE.md`](LICENSE.md) is kept byte-for-byte identical to upstream.
- All upstream copyright and authorship is preserved through the full, unrewritten git history.
- The commit that constitutes the modification is preserved verbatim with its original author
  and commit metadata, and is additionally documented here so that the fact of modification is
  not obscured — as required by GPLv3 §5(a).
- No claim of authorship over the upstream project or over commit `dff773e` is made.
- This fork is not affiliated with or endorsed by the TranslucentTB project or its maintainers.

## Using it

The workflow `.github/workflows/build.yml` runs manually:

**Actions → "Build TranslucentTB x64" → Run workflow**

It produces a `TranslucentTB-portable-x64` artifact containing an unsigned development build
(`/p:BuildType=Dev /p:SkipSigning=True`), which is why the produced executable reports a
placeholder `FileVersion` of `1.0.0.1` rather than a release version number.

If you want the real thing, use the official project:
<https://github.com/TranslucentTB/TranslucentTB>
