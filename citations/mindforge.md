# Mindforge — Citation Record

Bibliographic records for `mindforge.html`'s research basis, per the Prior-Art Protocol in `CLAUDE.md`. Every entry below was verified during the citation audit of 2026-08-05 / 2026-08-08 against Crossref, PubMed, or the publisher of record. Nothing here is cited from memory.

**Verification key:** ✅ verified against Crossref/PubMed · 📄 verified against publisher or archive copy · ⚠️ exists but the finding is disputed or failed replication · ❌ claim not supported by any source found

## Entrainment mechanism

- ✅ **Oster, G. (1973).** Auditory beats in the brain. *Scientific American*, 229(4), 94–102. doi:[10.1038/scientificamerican1073-94](https://doi.org/10.1038/scientificamerican1073-94)
  The foundational description of binaural beats: separate tones to each ear, difference frequency perceived centrally. This is the mechanism behind the `ChannelMerger(2)` topology — it is a citation for *what a binaural beat is*, not for any therapeutic outcome.

- 📄 **McDonnell, W.M. (Lt. Col., US Army) (1983).** *Analysis and Assessment of the Gateway Process.* Prepared for the US Army Operational Group; declassified by CIA, released 2003.
  Source of the Gateway ✦ preset values. **Read the primary text before citing this document for anything.** Full released text retrieved and searched 2026-08-08 (~95 KB): it is an assessment *of* the Monroe Institute's Hemi-Sync, and describes its own mechanism as binaural beats verbatim — *"one frequency in the left ear which is 10 Hertz below another audible frequency played in the right ear… the brain chooses to 'hear' the difference between them, the 'beat' frequency."* Term counts: "Hemi-Sync" 20, "Monroe" 18, **"golden" 0, "inver-" 0.** It is frequently misrepresented online as documenting a *successor* to binaural beats. It documents the opposite.

- ❌ **"7.5 Hz sweet spot" and the Vasiliev hypnagogic window (6.5–8.5 Hz).**
  The preset values are traceable to the Gateway report and to Vasiliev's protocol description respectively. **No controlled study has been located** establishing that these specific bands produce the claimed receptivity advantage. Treat the presets as protocol reconstruction, not as validated parameters.

## Bilateral stimulation

- ✅ **Shapiro, F. (1989).** Eye movement desensitization: a new treatment for post-traumatic stress disorder. *Journal of Behavior Therapy and Experimental Psychiatry*, 20(3), 211–217. doi:[10.1016/0005-7916(89)90025-6](https://doi.org/10.1016/0005-7916%2889%2990025-6)

- ⚠️ **Christman, S.D., Garvey, K.J., Propper, R.E., & Phaneuf, K.A. (2003).** Bilateral eye movements enhance the retrieval of episodic memories. *Neuropsychology*, 17(2), 221–229. doi:[10.1037/0894-4105.17.2.221](https://doi.org/10.1037/0894-4105.17.2.221)
  **Contested.** The saccade-induced retrieval enhancement (SIRE) effect did not replicate reliably in ✅ **Roberts, B.R.T., Fernandes, M.A., & MacLeod, C.M. (2020),** *PLoS ONE*, 15(1), e0227790, doi:[10.1371/journal.pone.0227790](https://doi.org/10.1371/journal.pone.0227790) — a first experiment gave weak support, a second larger experiment showed significant evidence for a *null* effect. Their conclusion: the effect "is inconsistent" and "its presence is very sensitive to experimental design."

- ⚠️ **van den Hout, M.A., Engelhard, I.M., Rijkeboer, M.M., et al. (2011).** EMDR: eye movements superior to beeps in taxing working memory and reducing vividness of recollections. *Behaviour Research and Therapy*, 49(2), 92–98. doi:[10.1016/j.brat.2010.11.003](https://doi.org/10.1016/j.brat.2010.11.003)
- ⚠️ **van den Hout, M.A., et al. (2012).** Tones inferior to eye movements in the EMDR treatment of PTSD. *Behaviour Research and Therapy*, 50(5), 275–279. doi:[10.1016/j.brat.2012.02.001](https://doi.org/10.1016/j.brat.2012.02.001)
  **Both are negative for the auditory case.** Mindforge delivers bilateral stimulation through audio panning plus visual bars, so these are evidence *against* the strongest form of the tool's own design rationale. They are cited anyway. Note the frequently-seen miscitation "van den Hout 2011, *BRAT* 49(2), 147–151, 'Tones inferior…'" — that welds the 2012 title to the 2011 volume and does not exist.

## Subliminal suggestion

- ✅ **Merikle, P.M., Smilek, D., & Eastwood, J.D. (2001).** Perception without awareness: perspectives from cognitive psychology. *Cognition*, 79(1–2), 115–134. doi:[10.1016/S0010-0277(00)00126-8](https://doi.org/10.1016/S0010-0277%2800%2900126-8) · PMID 11164025
  Establishes that stimuli are perceived without awareness and that such perception biases subsequent conscious experience.

- ❌ **"Divided attention enhances subliminal priming" — NOT supported by the above.**
  This claim was the stated design rationale for Video Overlay mode and was attributed to Merikle et al. (2001) in both the README and the profile README. The paper is a review of *whether* unconscious perception occurs across four experimental paradigms; it makes no comparative claim about effect strength under divided versus focused attention. **The divided-attention premise currently has no supporting citation in this project.** It may be defensible from the attentional-load literature — that literature has not been searched. Until it is, Video Overlay's rationale is a hypothesis, not a finding.

## Safety

- ✅ **Fisher, R.S., Harding, G., Erba, G., Barkley, G.L., & Wilkins, A. (2005).** Photic- and pattern-induced seizures: a review for the Epilepsy Foundation of America Working Group. *Epilepsia*, 46(9), 1426–1441. doi:[10.1111/j.1528-1167.2005.31405.x](https://doi.org/10.1111/j.1528-1167.2005.31405.x) · PMID 16146439
  Basis for the Phase 4 photosensitive consent modal. A companion expert-consensus paper (Harding first author, PMID 16146438) sits in the same issue and gives the ≥3 Hz / ≥20 cd·m⁻² / ≥0.006 steradian hazard thresholds.
  ⚠️ **Outstanding:** the modal's specific figures — susceptibility peaking at 15–25 Hz within a 1–65 Hz range — have **not** been verified against the article full text. The article exists at the cited location and the ≥3 Hz consensus threshold checks out; those two numbers do not yet. Verify before repeating them.
