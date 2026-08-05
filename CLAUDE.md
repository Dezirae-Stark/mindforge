# Mindforge — Operating Charter

## Mission
Suite of nine single-file browser tools for consciousness research, subconscious work, and consensual psi experimentation: Mindforge entrainment, Telehypnosis Pro, Ganzfeld, Coherence, Presentiment, Remote Viewing (incl. Cytherea Q-Viewer integration), Seiðr, Remote Healing, Solfeggio. Each tool is **one HTML file** that runs entirely in the browser with no installation, no account, no server traffic, no third-party code. Hosted as a static suite at `dezirae-stark.github.io/mindforge/`; intended to also work offline from a saved file.

## Methodological Commitments
- **Single-file purity is the architecture.** One HTML file per tool. No separate JS/CSS files, no build step, no module bundlers, no frameworks. This is non-negotiable — it's what makes the tools auditable, portable, and offline-capable.
- **Zero external dependencies.** No npm, no CDN, no remote fonts, no Google Analytics, no Sentry, no third-party scripts of any kind. If a feature requires a dependency, the feature is rejected.
- **Zero server communication.** No telemetry, no error reporting, no analytics, no auto-update probes, no opt-in "anonymous" beacons. The fetch surface is empty by default; the only network calls allowed are user-initiated YouTube embeds via `youtube-nocookie.com` (Mindforge video overlay) and intentional file uploads via FileReader (which doesn't network anyway).
- **localStorage-only persistence.** Per-tool namespaces (`mf-last`, `thp-log`, `gf-log`, `coh-log`, `seidr-log`, etc.). No IndexedDB unless absolutely required. FileReader uploads (photos, audio) stay in memory and are explicitly revoked on exit — never written to localStorage.
- **Web standards only.** Web Audio API, Web Speech API, Canvas, FileReader, SVG. No experimental APIs, no vendor-prefixed APIs, no proprietary surfaces.
- **Research grounding is required, not decorative.** Every tool's `Research basis` section must cite primary sources with author, year, and venue. Effect sizes claimed (d=0.11, d=0.21, d=0.28, d=0.40, etc.) must be traceable to the cited paper.
- **Safety notes are load-bearing.** Epilepsy, driving, mental health, headphone volume, deep theta drowsiness, consent for two-person tools, minor exclusion. These are not boilerplate — they remain consistent across tools and are not trimmed for brevity.

## Verification Gates
1. Each tool runs from a saved HTML file with the browser in airplane mode (the offline test)
2. Network panel during normal operation shows zero requests except user-initiated (YouTube embed, file upload via FileReader)
3. localStorage namespace contains only the tool's own keys; no cross-tool pollution
4. Audio architecture verified: `ChannelMerger(2)` for true stereo binaural, `linearRampToValueAtTime` for sample-accurate inaudible transitions, exponential decay on synthesised drum hits, garbage collection on per-hit oscillators
5. Every cited paper actually exists, was actually authored as cited, and actually says what the README claims it says
6. Safety notes present and consistent across tools

## Prior-Art Protocol
Primary literature anchors (verify before any new claim or protocol addition):
- IONS (Institute of Noetic Sciences) publication archive
- *Journal of Parapsychology*, *Journal of Scientific Exploration*, *EdgeScience*
- Vasiliev, *Experiments in Mental Suggestion* (1962)
- Honorton (1985); Bem & Honorton (1994); Hyman-Honorton joint communiqué
- Targ & Puthoff, *Nature* (1974); Utts (1995); SAIC/Stargate declassified material
- Radin (2004); Bierman & Radin (1997); presentiment meta-analyses
- Braud & Schlitz (1991); IONS DMILS series
- McCraty et al. (2009); HeartMath publication archive
- Elisabeth Targ (1998); IONS distant healing studies
- Sheldrake morphic resonance literature
- Shapiro (1987) EMDR original; Merikle et al. (2001) subliminal under divided attention
- Norse seiðr scholarship: Heide, Price, Tolley, Eldar Heide on varðlokkur

Record citations with DOI / venue link in `citations/<tool>.md`; protocol details in `protocols/<protocol-name>.md`.

## Anti-Patterns
- Adding a build step (webpack, vite, rollup, esbuild) — destroys single-file purity
- Importing any framework (React, Vue, Svelte, htmx) — destroys single-file purity
- Loading remote fonts, icons, or CSS — destroys offline guarantee
- Adding ANY analytics, telemetry, error reporting, or "phone-home" logic
- Making clinical claims (diagnoses, treats, cures, replaces medical care)
- Letting the model invent research citations or effect sizes — citation auditor catches this
- Trimming or weakening safety notes for visual cleanliness
- Allowing FileReader uploads to persist beyond session
- Using `eval`, `Function`, or `dangerouslySetInnerHTML`-equivalent patterns on user input
- Adding "convenience" features that require accounts, sync, or any backend

## Subagent Roster (`.claude/agents/`)
- `single-file-architect.md` — enforces the one-HTML-file invariant; rejects any proposal that adds external resources
- `audio-architecture-verifier.md` — checks Web Audio patterns: ChannelMerger for binaural, linearRampToValueAtTime for ramps, exponential decay envelopes, oscillator GC
- `citation-auditor.md` — verifies every cited paper exists, is correctly attributed, and says what's claimed; flags fabricated citations
- `privacy-leakage-tester.md` — confirms zero network egress under normal use; localStorage namespace boundaries respected
- `safety-notes-reviewer.md` — ensures safety notes complete and consistent per tool class (entrainment, two-person psi, breathing, drumming, etc.)
- `protocol-fidelity-reviewer.md` — verifies that the implemented protocol (e.g., Honorton ganzfeld, Vasiliev hypnagogic, SRI CRV 6-stage) matches the cited primary source
- `cross-tool-integration-reviewer.md` — for the Cytherea Q-Viewer pairing and any other cross-project couplings, verifies the JSON schema contract on both sides

## Persistent State
- `citations/<tool>.md` — bibliographic records with verified DOIs / venue links
- `protocols/<protocol-name>.md` — canonical protocol documents (Honorton ganzfeld procedure, Vasiliev session, CRV stage definitions, HeartMath coherence, etc.)
- `safety/master.md` — contraindications, consent requirements, age restrictions per tool class
- `audio-architecture/patterns.md` — verified Web Audio patterns (binaural, drumming, pink noise via Paul Kellett IIR, transition modes)
- `tools/<name>/changelog.md` — per-tool version history with rationale
- `cross-integrations/cytherea-qviewer.md` — JSON schema contract for the RV pairing

## Cross-Project Couplings
- **Cytherea Q-Viewer** — citation-level, not a runtime integration. Cytherea's site cross-references this tool's protocol, and its session runner adopts the same session-record shape so both sides describe sessions identically. No code path in this suite contacts Cytherea and none can: the fetch surface is empty. The field intended for quoting outside the tool is `coordinate_hash` — `SHA-256("mindforge-rv-coordinate:v1:" + coordinate)` truncated to 128 bits, implemented in-file in `remote-viewing.html` (not `crypto.subtle`, which needs a secure context the offline-file gate cannot assume). Note that the *export* file is the full record including `transcript` and `target_revealed`; only the hash is the quotable identifier.
- **External primary-source records** — some citation records in `citations/` reference digests held in a separate private research repository. Those are documentation-layer only: no runtime dependency, and no network call from any tool references them. Where such a source informs a citation, `citations/<tool>.md` states what it does and does not support.

## Note on Scope
These tools are personal practice and research aids, not medical devices, not clinical instruments, not therapeutic claims. The research sections describe findings in the literature — they do not prove that any specific implementation produces any specific outcome for any specific person. Architectural decisions reflect this: privacy by construction, no clinical claims, consent-required for two-person protocols.
