# AGENTS.md — mendsec/spheradian-files

This file defines persistent rules and architectural context for AI coding agents working on `mendsec/spheradian-files`.

---

## Hard Rules — Never Violate

1. **English Only Across the Entire Project:**
   - All source files, shaders, documentation, package metadata, log messages, UI strings, window titles, comments, and commit messages MUST be written strictly in **English**.
2. **All Security Work Goes to the Private Security Repository (`mendsec/spheradian-security`):**
   - Never commit security audit reports, threat models, vulnerability analyses, exploit proofs-of-concept, internal hardening notes, or unpatched security findings to the public `mendsec/spheradian-files` repository.
   - Anything security-related that we investigate, audit, or track MUST be stored exclusively in the private repository:
     - **GitHub (Private):** `https://github.com/mendsec/spheradian-security`
     - **Local Path:** `/home/fabio/Dev/spheradian-security` (restricted `0700` permissions)
   - Public commits fixing security issues must use clean, functional, defensive descriptions without exposing exploit vectors, internal heuristics, or vulnerability identifiers prior to coordinated disclosure.
3. **Never Auto-Merge Pull Requests — Wait for Human and Agent Review:**
   - Never merge a pull request automatically unless the maintainer explicitly asks to merge that specific pull request.
   - Always leave newly opened pull requests open so the maintainer can perform human review and other automated review agents have time to finish analyzing the changes.

---

## Architectural Context

- This repository is the file manager component of the Spheradian ecosystem (`mendsec/spheradian`).
- `prototype/cube-explorer/index.html` is a self-contained browser simulation (three.js from a pinned CDN version) used to explore the interaction design. Its file system is generated in memory; it must never read or write real files.
- The long-term implementation targets Rust and `wgpu`, following the conventions of `mendsec/spheradian` (`unsafe` forbidden, hardened release profile, committed `Cargo.lock`).
