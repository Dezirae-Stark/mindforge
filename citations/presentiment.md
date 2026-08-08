# Presentiment — Citation Record

Bibliographic records for `presentiment.html`'s research basis, per the Prior-Art Protocol in `CLAUDE.md`. Every entry below was verified during the citation audit of 2026-08-05 / 2026-08-08 against Crossref, PubMed, or the publisher of record. Nothing here is cited from memory.

**Verification key:** ✅ verified against Crossref/PubMed · 📄 verified against publisher or archive copy · ⚠️ exists but the finding is disputed or failed replication · ❌ claim not supported by any source found

## Primary sources

- ✅ **Bierman, D.J., & Radin, D.I. (1997).** Anomalous anticipatory response on randomized future conditions. *Perceptual and Motor Skills*, 84(2), 689–690. doi:[10.2466/pms.1997.84.2.689](https://doi.org/10.2466/pms.1997.84.2.689)

- 📄 **Radin, D.I. (2004).** Electrodermal presentiments of future emotions. *Journal of Scientific Exploration*, 18(2), 253–274.
  No Crossref DOI. Note the page range: **253–274**, not 253–273 as previously recorded here. Four experiments, 133 participants, 4,569 trials; reported weighted mean per-trial effect size e = 0.064 ± 0.015.

- ✅ **Mossbridge, J., Tressoldi, P., & Utts, J. (2012).** Predictive physiological anticipation preceding seemingly unpredictable stimuli: a meta-analysis. *Frontiers in Psychology*, 3, article 390. doi:[10.3389/fpsyg.2012.00390](https://doi.org/10.3389/fpsyg.2012.00390)
  26 reports, 1978–2010, seven independent laboratories. The standard meta-analytic reference for this paradigm and a better citation than either single study above.

## What this tool does NOT replicate

Every source above measures **physiology** — electrodermal activity, heart rate, pupil dilation — in the seconds before a randomly selected stimulus. The effect, if real, is a pre-stimulus physiological deflection the participant is not aware of.

**This tool has no physiological input.** It records a conscious three-way self-report (calm / mild / activated) before each reveal. That is a different paradigm measuring a different thing. A result obtained here is not a presentiment replication and must not be reported as one — it is a forced-choice guessing task with a self-report interface.

## Statistics

A "mild" rating scores a flat 0.5 whatever the stimulus turns out to be, so those trials contribute no variance. Only the decisive calls can deviate from chance, and on those the score is Binomial(D, 0.5) where D is the non-mild count. Therefore E[score] = n/2 for any response style, sigma = sqrt(D)/2, and the test is an exact binomial on D. Conditioning on D is legitimate because D is ancillary — under the null the rating is independent of stimulus valence.

Earlier builds used a fixed sigma = sqrt(n/4), which is the D = n special case (a rater who never says "mild") and understated sigma by up to sqrt(1.5), so the "z > 1.96" verdict fired at a true z of 2.40.

⚠️ **Optional stopping is not controlled.** The running score is visible during the session, so nothing prevents stopping on a good run. This inflates false positives and is a known weakness of the presentiment literature generally. Fix the trial count before beginning.
