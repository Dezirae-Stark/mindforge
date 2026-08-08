# Ganzfeld — Citation Record

Bibliographic records for `ganzfeld.html`'s research basis, per the Prior-Art Protocol in `CLAUDE.md`. Every entry below was verified during the citation audit of 2026-08-05 / 2026-08-08 against Crossref, PubMed, or the publisher of record. Nothing here is cited from memory.

**Verification key:** ✅ verified against Crossref/PubMed · 📄 verified against publisher or archive copy · ⚠️ exists but the finding is disputed or failed replication · ❌ claim not supported by any source found

## Core protocol and meta-analyses

- 📄 **Honorton, C. (1985).** Meta-analysis of psi ganzfeld research: a response to Hyman. *Journal of Parapsychology*, 49, 51–91.
  No Crossref DOI (the journal predates DOI assignment for this volume). Source of the 28-study / ~32% direct-hit figure against a 25% baseline.

- 📄 **Hyman, R., & Honorton, C. (1986).** A joint communiqué: the psi ganzfeld controversy. *Journal of Parapsychology*, 50, 351–364. Reprinted 2019: *Journal of Parapsychology*, 82(3), 108–117, doi:[10.30891/jopar.2018s.01.09](https://doi.org/10.30891/jopar.2018s.01.09)
  The agreed statement of methodological standards after the Hyman/Honorton exchange. **This is the document that defines what a well-controlled ganzfeld requires** — including sender/receiver isolation. It is the correct reference for judging whether a given implementation qualifies.

- ✅ **Bem, D.J., & Honorton, C. (1994).** Does psi exist? Replicable evidence for an anomalous process of information transfer. *Psychological Bulletin*, 115(1), 4–18. doi:[10.1037/0033-2909.115.1.4](https://doi.org/10.1037/0033-2909.115.1.4)

## Counter-evidence — cite alongside, not instead

- ⚠️ **Milton, J., & Wiseman, R. (1999).** Does psi exist? Lack of replication of an anomalous process of information transfer. *Psychological Bulletin*, 125(4), 387–391. doi:[10.1037/0033-2909.125.4.387](https://doi.org/10.1037/0033-2909.125.4.387)
  A meta-analysis of 30 subsequent ganzfeld studies finding no significant effect. Any citation of Bem & Honorton (1994) that omits this is presenting one side of an unresolved dispute.

- ⚠️ **Storm, L., Tressoldi, P.E., & Di Risio, L. (2010).** Meta-analysis of free-response studies, 1992–2008: assessing the noise reduction model. *Psychological Bulletin*, 136(4), 471–485. doi:[10.1037/a0019457](https://doi.org/10.1037/a0019457)
- ⚠️ **Hyman, R. (2010).** Meta-analysis that conceals more than it reveals: comment on Storm et al. (2010). *Psychological Bulletin*, 136(4), 486–490. doi:[10.1037/a0019676](https://doi.org/10.1037/a0019676)
  The exchange continues. The honest summary is that the ganzfeld database remains contested, not that it is settled in either direction.

## Implementation caveat — load-bearing

The Hyman–Honorton joint communiqué requires sender and receiver to be sensorily isolated. **This tool cannot provide that.** Zero network egress means two copies of the page cannot agree on a target, so the only working mode is one device with the sender's target behind a click-to-reveal cover and the receiver asked not to scroll. Separation is procedural, not physical.

Sensory leakage between sender and receiver is precisely the criticism Hyman levelled at the early database. **A hit rate obtained with this tool is not comparable to the meta-analytic figures above** and must not be reported as though it were. This is stated in the README's Ganzfeld section and should stay there.

## Statistics

Direct hits are Binomial(N, 0.25) under the null; the tool reports an exact one-sided binomial tail, not a normal approximation, and shows no p-value below 8 logged sessions. Earlier builds used the normal approximation with no N floor and reported "p < 0.05" for two sessions with two hits, where the exact probability is 0.0625.
