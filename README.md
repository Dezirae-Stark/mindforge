# Mindforge

A suite of single-file browser tools for consciousness research, subconscious work, and consensual psi experimentation. No installation, no account, no data sent anywhere. Each tool is a single HTML file that runs entirely in your browser.

---

## Tool Suite

| Tool | Purpose | Protocol Basis |
|------|---------|----------------|
| [Mindforge](#mindforge--self-directed-entrainment) | Self-directed brainwave entrainment and subliminal suggestion | Monroe Institute / CIA Gateway / Vasiliev |
| [Telehypnosis Pro](#telehypnosis-pro--remote-mental-suggestion) | Operator console for two-person mental suggestion research | Vasiliev / Braud-Schlitz IONS |
| [Ganzfeld](#ganzfeld--consensual-telepathy-protocol) | Two-person ganzfeld psi session manager | Honorton / IONS replication series |
| [Coherence](#coherence--heart-brain-trainer) | Heart-brain coherence breathing trainer | HeartMath Institute / McCraty |
| [Presentiment](#presentiment--pre-stimulus-awareness-trainer) | Pre-stimulus anticipatory response trainer | Radin / Bierman IONS |
| [Remote Viewing](#remote-viewing--sriarvprotocol-manager) | SRI/ARV session log and protocol manager | Targ & Puthoff SRI / SAIC |

---

## Mindforge — Self-Directed Entrainment

**Live tool:** https://dezirae-stark.github.io/mindforge/

**Brainwave entrainment · Bilateral stimulation · Subliminal suggestion · Ericksonian session protocol**

A single-file web tool for self-directed subconscious reprogramming. Runs entirely in your phone or desktop browser with no installation. Combines four complementary mechanisms in sequence to lower or route around the conscious critical faculty and deliver new suggestions to the subconscious.

### What it does

Your conscious mind acts as a gatekeeper — evaluating, criticizing, and filtering every idea before it can influence your behavior. Mindforge uses four layers to get around that gate:

1. **Ericksonian pattern interrupt** — a 60-second pre-session overload that suspends the critical faculty before the main session begins, using rapid bilateral stimulation at 4 Hz deep theta to create cognitive saturation
2. **Binaural beat entrainment** — true stereo binaural via `ChannelMerger(2)`, 300 Hz carrier (Monroe Institute / CIA Gateway specification), progressive frequency descent from alpha into theta
3. **Bilateral stimulation** — alternating visual edge flashes and/or pink noise between left/right ear, engaging cross-hemispheric signaling (EMDR mechanism, Shapiro 1987)
4. **Subliminal suggestion** — text flashed at 16–200ms with optional Ericksonian presupposition embedding and parallel Web Speech API voice delivery

### Presets

| Preset | Protocol |
|--------|---------|
| **Gateway ✦** | CIA Gateway Process specifications: 300 Hz carrier, α→7.5 Hz descent, 60s interrupt, combined audio+visual bilateral, 30 min |
| **Schumann ✦** | Schumann resonance target: 12→7.83 Hz descent, 45s interrupt, 25 min |
| **Deep Work** | 10→6→4 Hz descent, 60s interrupt, 25 min |
| **Sleep Onset** | No interrupt; 8→4→3 Hz descent, gentle bilateral, 25 min. Operationalizes Vasiliev's hypnagogic approach |
| **Gentle Entry** | No interrupt; slow 12→10→8 Hz descent; 100ms flash duration; 15 min. Suitable for beginners |

### Key features

- **Hypnagogic window detection** — when frequency crosses through 6.5–8.5 Hz during descent, the display shows `⟁ hypnagogic window — peak receptivity` and suggestion delivery density automatically doubles. This targets the Vasiliev-identified peak receptivity interval.
- **Progressive frequency descent** — `linearRampToValueAtTime` schedules smooth, inaudible ramps from start → mid → end frequency across configurable intervals
- **Linguistic embedding** — raw suggestions are automatically wrapped in Ericksonian presupposition frames ("As you drift deeper, *suggestion*") before display, embedding the suggestion inside an already-accepted premise
- **Voice delivery** — simultaneous Web Speech API audio of each suggestion at 0.65× speed, soft female voice, dual-channel delivery
- **Variable interval delivery** — randomized ±40% interval variance prevents subconscious habituation to a predictable rhythm
- **Save/load presets** — all settings including suggestion text saved to `localStorage`, auto-restored on next open
- **End chime** — three ascending sine tones (396/528/660 Hz) to gently signal session completion

### Audio architecture

```
leftOsc  (carrier Hz)       → leftG  ─┐
                                       ├── ChannelMerger → masterG → destination
rightOsc (carrier + beat Hz) → rightG ─┘

noiseSource → noiseG ──────────────────── masterG → destination
noiseSource panned L/R alternating at bilateral rate
```

True stereo binaural via `ChannelMerger(2)`. Pink noise generated using Paul Kellett's IIR filter algorithm looped from a 5-second buffer. All frequency changes via `linearRampToValueAtTime` — sample-accurate and inaudible during transitions.

---

## Telehypnosis Pro — Remote Mental Suggestion

**Live tool:** https://dezirae-stark.github.io/mindforge/telehypnosis-pro.html

**Vasiliev protocol · IONS Braud-Schlitz · Operator console · Research grade · Blinded**

Operator console for two-person consensual remote mental suggestion experiments. Based on Dr. L.L. Vasiliev's hypnagogic receptivity research (*Experiments in Mental Suggestion*, 1962) and the Braud/Schlitz IONS DMILS (Direct Mental Interaction with Living Systems) series, which yielded d=0.11 across 655 sessions.

**Setup:** Both parties agree on a start time. The receiver opens Mindforge → Gateway or Sleep Onset preset for identical duration. The operator runs this tool.

### Features

**Pre-session coherence primer**
An optional integrated 5-minute heart coherence breathing overlay (5.5s inhale / 5.5s exhale) based on HeartMath research showing that sender HRV coherence correlates with receiver response amplitude. Dismissable with Skip after completing.

**Relationship field**
Dropdown with relationship type (romantic partner, close friend, family member, colleague, stranger) with inline effect-size hint drawn from Sheldrake morphic resonance and IONS proximity research — closer emotional bonds show stronger correspondence.

**Intention field (blinded)**
Write what you intend to transmit before the session. The field is sealed behind a [reveal] toggle. Research protocol note: write this before the session; do not reveal to receiver until after they have recorded their impressions.

**Intention framing guide**
Collapsible guide with specific framing approaches from Braud's DMILS protocol: single clear image over abstract concepts, positive-state focus, somatic sensation framing. Opens inline without leaving the page.

**Operator audio**
- Alpha binaural: 9 Hz default (range 8–14 Hz), 300 Hz carrier, sine wave — per Braud/Schlitz findings that relaxed-alert sender alpha (not deep trance) correlates with receiver response
- Optional gentle pink noise (mono, low volume)
- No bilateral stimulation (operator needs alert focus, not trance)

**Focus modes** — three, toggle between them:

| Mode | Description |
|------|-------------|
| **Yantra** | Animated SVG Sri Yantra: outer ring 60s CW rotation, inner triangles 45s CCW, pulsing bindu, radial glow filter. Holds attention without words. |
| **Photo** | Uploaded receiver photo in a dark oval frame with slow pulsing aura (~0.05 Hz breath rhythm). Receiver name overlaid dim. FileReader API — stays session-only, never written to localStorage. |
| **Void** | Near-black field with receiver name in barely-visible text. Slow radial pulse from center. Operator holds intention mentally — nothing displayed. |

**Session coordination and timer**
- Duration selector: 15 / 20 / 25 / 30 min
- Timer display: elapsed mm:ss
- Begin → locks focus interface, dims controls; End → opens post-session log

**Post-session record** (appears after session ends)
- Intention (pre-filled)
- Receiver's reported impressions
- Match rating: 0–5 scale (None / Vague / Partial / Strong / Exact)
- Free notes

**Session log**
- Persistent in `localStorage` (`thp-log`)
- Table: date | receiver | duration | match rating | notes
- JSON export for research records

---

## Ganzfeld — Consensual Telepathy Protocol

**Live tool:** https://dezirae-stark.github.io/mindforge/ganzfeld.html

**IONS ganzfeld · Honorton protocol · Sender/receiver consoles · Blinded rank-order judging · Statistics**

Full two-person ganzfeld session manager for consensual psi research. Based on the Honorton (1985) meta-analysis (28 studies, 32% direct hit rate vs 25% chance, effect size d=0.28), the Bem-Honorton autoganzfeld series, and IONS replications. Ganzfeld is the most replicated protocol in parapsychology.

**Setup:** Both parties run this tool simultaneously. Sender and receiver see only their own console. Receiver records impressions before seeing any targets. Judging is performed blind.

### How a session works

1. **Setup** — enter receiver/sender names, set duration (20/30/40 min), choose built-in or custom targets
2. **Sender console** — displays the randomly selected target (text from the 20-target built-in pool or a custom image/text) with a session timer. Sender focuses on transmitting the target.
3. **Receiver console** — dim overlay mode with pink noise for sensory reduction, textarea for impression notes
4. **Judging** — after session ends, receiver sees all 4 targets in Fisher-Yates shuffled order (labelled Option 1–4 only), with no indication which was the actual target. Receiver ranks all four by correspondence (1st = best match). Results revealed only after all 4 are ranked.
5. **Statistics** — running hit rate, z-score, p < 0.05 and p < 0.10 threshold markers across all logged sessions

### Pink noise (sensory reduction)
Paul Kellett IIR filter algorithm, looped mono buffer. Volume-adjustable. Provides uniform sensory masking that homogenizes the auditory environment — the ganzfeld ("whole field") condition is designed to reduce sensory variation so internally-generated impressions become relatively more salient.

### Built-in target pool
20 text targets covering elemental, natural, and archetypal categories (ocean, fire, mountain, forest, etc.). Fisher-Yates shuffle selects 4 for each session; one is randomly designated the target. Custom image or text target entry also supported.

### Statistics
- Direct hits (rank 1), expected 25%, displayed with hit rate %
- Z-score: `(hits - N×0.25) / sqrt(N×0.25×0.75)`
- p < 0.05 marker in green when Z > 1.96
- p < 0.10 trend marker in amber when Z > 1.645

### Research basis

> Honorton, C. (1985). Meta-analysis of psi Ganzfeld research: a response to Hyman. *Journal of Parapsychology*, 49, 51–91.
>
> Bem, D.J., & Honorton, C. (1994). Does psi exist? Replicable evidence for an anomalous process of information transfer. *Psychological Bulletin*, 115(1), 4–18.

---

## Coherence — Heart-Brain Trainer

**Live tool:** https://dezirae-stark.github.io/mindforge/coherence.html

**HeartMath protocol · 5.5s breathing pacer · HRV resonance · Pre-session primer**

Heart-brain coherence trainer based on HeartMath Institute research (McCraty, 2001) and the Braud/Schlitz IONS finding that sender heart coherence correlates with receiver physiological response amplitude. Use as a 5-minute pre-session primer before Mindforge, Telehypnosis Pro, or Ganzfeld sessions.

### How it works

The heart has its own intrinsic nervous system and sends more signals to the brain than it receives. Heart rate variability (HRV) coherence — a smooth, sine-like rhythm in the heart rate — creates measurable changes in autonomic nervous system balance, brain activity, and inter-system synchronization.

The HeartMath resonance frequency for HRV coherence is approximately 0.1 Hz (one complete breath cycle every ~10 seconds). The 5.5s inhale / 5.5s exhale rhythm produces a 0.0909 Hz cycle — the closest whole-second approximation of this resonance frequency.

Coherence onset typically occurs within 60–90 seconds of slow rhythmic breathing combined with a heart-focused emotional state (appreciation, gratitude, or care). The three intention prompts used in this tool are specifically these three states, which HeartMath research identifies as having the strongest physiological coherence effect.

### Presets

| Duration | Cycles | Use |
|----------|--------|-----|
| 3 min | ~18 cycles | Quick coherence reset; pre-session primer |
| 10 min | ~60 cycles | Standard coherence session |
| 20 min | ~120 cycles | Deep coherence; extended practice |
| Custom | — | 1–60 min slider |

### Features

- Animated breathing pacer with inhale/exhale phase display and color transition (blue-green spectrum)
- Rotating intention prompts on each breath cycle — appreciation, gratitude, care
- Elapsed time, remaining time, and cycle count display
- Self-reported coherence rating (1–5 stars) at session end
- Session log with date, duration, cycles, coherence rating, and notes
- Cumulative statistics: total sessions, average coherence rating
- `localStorage` persistence (`coh-log`, `coh-last`); JSON export

### Research basis

> McCraty, R., Atkinson, M., Tomasino, D., & Bradley, R.T. (2009). The coherent heart: heart-brain interactions, psychophysiological coherence, and the emergence of system-wide order. *Integral Review*, 5(2), 10–115.
>
> Braud, W., & Schlitz, M. (1991). Consciousness interactions with remote biological systems: anomalous intentionality effects. *Subtle Energies*, 2(1), 1–46.

---

## Presentiment — Pre-Stimulus Awareness Trainer

**Live tool:** https://dezirae-stark.github.io/mindforge/presentiment.html

**Radin/Bierman protocol · Pre-stimulus response · 20–40 trial sessions · Z-score scoring**

Pre-stimulus anticipatory response training based on Dean Radin's IONS presentiment experiments (2004–2023), which measured electrodermal activity in the seconds *before* an emotional image was randomly selected by computer — finding that the skin began responding to the emotional stimulus approximately 4–6 seconds before it appeared (d=0.21, p < 0.001 across 26 studies).

This tool runs a subjective behavioral analogue: you report your gut-sense (Calm / Mild / Activated) before each stimulus reveal, then the tool scores whether your pre-rating predicted the emotional valence.

### Trial structure

Each trial runs three phases:

```
Phase A: Fixation     (1–2 s)    — cross or blank, attention settling
Phase B: Pre-rating   (tap)      — Calm | Mild | Activated
         Gap          (1 s)      — the presentiment window
Phase C: Reveal       (4 s)      — stimulus displayed as NEUTRAL or EMOTIONAL
                                   with valence label and feedback (Correct / Partial / Miss)
```

Scoring:
- Calm before neutral → 1 pt (correct)
- Activated before emotional → 1 pt (correct)
- Mild before either → 0.5 pt (partial)
- Mismatch → 0 pt

Chance baseline: 0.5 pts/trial (random guessing).

### Session configuration

- **Trial count:** 20 / 30 / 40 trials
- **Inter-trial interval (ITI):** 2–8 second pause between trials (configurable)
- **Trial tones:** optional 400 Hz click (30ms, gain 0.05) at each phase transition via Web Audio API

### Progress display

Fixed trial bar visible throughout: `Trial N / M` | dot history (last 10 trials: ● hit / ∘ partial / · miss) | running score vs expected.

### Session complete statistics

Score, trials, chance baseline, z-score, hit rate %, calm→neutral hits, activated→emotional hits, mild rate, verdict (above / trending / below chance with color coding).

### Research basis

> Radin, D.I. (2004). Electrodermal presentiments of future emotions. *Journal of Scientific Exploration*, 18(2), 253–273.
>
> Bierman, D.J., & Radin, D.I. (1997). Anomalous anticipatory response on randomized future conditions. *Perceptual and Motor Skills*, 84(2), 689–690.

---

## Remote Viewing — SRI/ARV Protocol Manager

**Live tool:** https://dezirae-stark.github.io/mindforge/remote-viewing.html

**SRI coordinate RV · Associative RV (ARV) · 6-stage CRV · 0–7 correspondence rating**

Session manager and log for coordinate remote viewing (CRV) and associative remote viewing (ARV) practice, based on SRI International protocols developed by Russell Targ and Hal Puthoff (1972–1989) and continued by the SAIC Stargate program. Meta-analysis of the SRI/SAIC data by Utts (1995) found effect sizes of approximately d=0.40 for trained viewers.

### Session modes

**Coordinate RV (standard mode)**
Viewer receives only a random coordinate (e.g. `483921`) or session ID — no other information. The target has been assigned to that coordinate by the monitor before the session and is not revealed until judging. Viewer records impressions, sketches, and descriptors across the 6 CRV stages, then rates correspondence 0–7.

**Associative RV (ARV mode)**
Used for binary outcome prediction. Two different target objects are pre-assigned to YES and NO outcomes. Viewer remote-views as normal; the transcript is later judged for which target it better resembles, and the corresponding call (A=YES / B=NO) is recorded. ARV hit rate is tracked separately in the session log.

### CRV stage reference (collapsible guide built in)

| Stage | Name | Description |
|-------|------|-------------|
| 1 | **Ideogram** | First spontaneous mark or impression. Do not analyse. |
| 2 | **Sensory** | Sensory descriptors: textures, temperatures, colors, sounds, smells |
| 3 | **Dimensional** | Sizes, heights, distances, spatial relationships |
| 4 | **Aesthetic** | Emotional/aesthetic qualities, ambiance, feeling-tone of the site |
| 5 | **Emotional** | Functional activity at the site; any emotional response in the viewer |
| 6 | **AOL** | Analytical Overlay — record any analytical impressions here to quarantine them from earlier stages |

### Correspondence rating scale (0–7)

| Score | Label |
|-------|-------|
| 0 | No correspondence |
| 1 | Vague/marginal |
| 2 | Some elements match |
| 3 | Partial correspondence |
| 4 | Good correspondence |
| 5 | Strong correspondence |
| 6 | Very strong correspondence |
| 7 | Near-perfect match |

Color-coded in the session log (0=dim → 4=accent2 → 7=green).

### Session features

- Blind coordinate generation (random 6-digit ID)
- Timed session (elapsed display, optional auto-stop)
- Full transcript textarea with session notes
- Post-session reveal: enter actual target description after viewing
- ARV: A/B binary call with corresponding outcome field
- Three-step judging: reveal → rating → analysis (viewer / independent judge / self)

### Running statistics

- Average rating (displayed as 0–7 dot scale)
- Total sessions, Moderate+ (≥3) count with percentage
- ARV hit rate (shown when ARV sessions with known outcomes exist)
- This-month session count

### Research basis

> Targ, R., & Puthoff, H. (1974). Information transmission under conditions of sensory shielding. *Nature*, 251, 602–607.
>
> Utts, J. (1995). An assessment of the evidence for psychic functioning. *Journal of Scientific Exploration*, 9(4), 351–396.

---

## Combining the Tools

These tools are designed to complement each other in a research workflow:

**For single-subject work (solo practice):**
1. **Coherence** (3–5 min) — establish heart-brain coherence before the session
2. **Mindforge** — main entrainment session with your working suggestions
3. **Presentiment** — train pre-stimulus anticipatory sensitivity as a standalone practice

**For two-person psi research:**
1. **Coherence** (both parties, 5 min) — synchronize physiological state before session
2. **Ganzfeld** — consensual sender/receiver session with blinded judging and statistics
   *or* **Telehypnosis Pro** — Vasiliev-style mental suggestion session (operator + Mindforge receiver)

**For remote viewing practice:**
1. **Coherence** (3 min) — settle and center
2. **Remote Viewing** — coordinate session with CRV stage guide
3. **Presentiment** — cross-train pre-stimulus sensitivity between RV sessions

---

## Architecture & Privacy

All six tools share the same design principles:

- **Single HTML file, zero external dependencies** — no frameworks, no CDN calls, no fonts fetched from the network. Each file contains all CSS, JavaScript, and SVG inline.
- **No server communication** — nothing is transmitted anywhere. All session logs and settings are stored in browser `localStorage` only.
- **Works offline** — save any file to your device and open it with a browser. No internet connection required after the initial load.
- **Mobile-first** — designed for 375–520px viewport, fully usable on phone browsers.
- **Web Audio API** — all audio generated in-browser. No audio files are loaded. Pink noise generated algorithmically (Paul Kellett IIR filter). Binaural beats generated via dual oscillators with `ChannelMerger(2)`.

### localStorage keys

| Tool | Settings key | Log key |
|------|-------------|---------|
| Mindforge | `mf-last`, `mf-presets` | — |
| Telehypnosis Pro | `thp-last` | `thp-log` |
| Ganzfeld | `gz-last` | `gz-log` |
| Coherence | `coh-last` | `coh-log` |
| Presentiment | `pre-last` | `pre-log` |
| Remote Viewing | `rv-last` | `rv-log` |

All log entries are exportable as JSON from within each tool.

---

## Safety Notes

- **Epilepsy:** Mindforge and Ganzfeld include rhythmic visual stimuli (bilateral edge flashes, focus glow pulses). If you have photosensitive epilepsy or seizure sensitivity to flashing light, disable visual bilateral stimulation and use audio-only modes.
- **Driving / machinery:** Do not use Mindforge or Coherence during any activity requiring alertness. These tools are designed to shift you toward relaxed or trance-adjacent states.
- **Mental health:** If you are experiencing an acute psychotic episode, severe dissociation, or acute mental health crisis, these are not appropriate tools at this time.
- **Headphone volume:** Keep binaural audio volume low (0.2–0.3 range). Entrainment does not require loud audio. Extended high-volume sessions cause ear fatigue.
- **Delta/deep theta:** Very low frequencies (1–4 Hz) cause drowsiness approaching sleep. Do not use lying down where falling asleep poses any risk.
- **Consensual sessions only:** Telehypnosis Pro and Ganzfeld are designed for use with consenting adults who are aware they are participating in an experiment.

---

## Research References

### Entrainment & Altered States
- Oster, G. (1973). Auditory beats in the brain. *Scientific American*, 229(4), 94–102.
- Monroe, R.A. (1977). *Journeys Out of the Body*. Anchor Books.
- McDonnell, W.A. (1983). *Analysis and Assessment of the Gateway Process*. CIA declassified document, approved for release 2003.

### Vasiliev & Receptivity
- Vasiliev, L.L. (1963). *Experiments in Mental Suggestion*. Institute for the Study of Mental Images, London. (Original Russian 1962.)

### IONS Remote Influence (DMILS)
- Braud, W., & Schlitz, M. (1991). Consciousness interactions with remote biological systems: anomalous intentionality effects. *Subtle Energies*, 2(1), 1–46.
- Schlitz, M., & Braud, W. (1997). Distant intentionality and healing: assessing the evidence. *Alternative Therapies in Health and Medicine*, 3(6), 62–73.

### Ganzfeld
- Honorton, C. (1985). Meta-analysis of psi Ganzfeld research: a response to Hyman. *Journal of Parapsychology*, 49, 51–91.
- Bem, D.J., & Honorton, C. (1994). Does psi exist? Replicable evidence for an anomalous process of information transfer. *Psychological Bulletin*, 115(1), 4–18.

### Heart Coherence
- McCraty, R., Atkinson, M., Tomasino, D., & Bradley, R.T. (2009). The coherent heart. *Integral Review*, 5(2), 10–115.
- Childre, D., & Martin, H. (1999). *The HeartMath Solution*. HarperSanFrancisco.

### Presentiment
- Radin, D.I. (2004). Electrodermal presentiments of future emotions. *Journal of Scientific Exploration*, 18(2), 253–273.
- Bierman, D.J., & Radin, D.I. (1997). Anomalous anticipatory response on randomized future conditions. *Perceptual and Motor Skills*, 84(2), 689–690.

### Remote Viewing
- Targ, R., & Puthoff, H. (1974). Information transmission under conditions of sensory shielding. *Nature*, 251, 602–607.
- Utts, J. (1995). An assessment of the evidence for psychic functioning. *Journal of Scientific Exploration*, 9(4), 351–396.
- McMoneagle, J. (1997). *Mind Trek*. Hampton Roads Publishing.

### Bilateral Stimulation (EMDR)
- Shapiro, F. (1989). Eye movement desensitization: a new treatment for post-traumatic stress disorder. *Journal of Behavior Therapy and Experimental Psychiatry*, 20(3), 211–217.
- van den Hout, M.A., et al. (2011). Tones inferior to eye movements in the EMDR treatment of PTSD. *Behaviour Research and Therapy*, 49(2), 147–151.

### Subliminal Processing
- Merikle, P.M., Smilek, D., & Eastwood, J.D. (2001). Perception without awareness: perspectives from cognitive psychology. *Cognition*, 79(1-2), 115–134.
- Bandler, R. & Grinder, J. (1981). *Trance-Formations*. Real People Press.

---

## Mindforge — Full Documentation

The sections below cover Mindforge in depth.

### Table of Contents

1. [The Science](#the-science)
   - [Binaural Beats & Brainwave Entrainment](#binaural-beats--brainwave-entrainment)
   - [Bilateral Visual Stimulation](#bilateral-visual-stimulation)
   - [Subliminal Suggestion](#subliminal-suggestion)
   - [Receptivity Research: Vasiliev and the Hypnagogic State](#receptivity-research-vasiliev-and-the-hypnagogic-state)
   - [CIA Gateway Process Report (1983)](#cia-gateway-process-report-1983)
   - [Why Combine All Four](#why-combine-all-four)
2. [Quick Start](#quick-start)
3. [Writing Effective Suggestions](#writing-effective-suggestions)
4. [Frequency Selection Guide](#frequency-selection-guide)
5. [User Manual — Every Control Explained](#user-manual--every-control-explained)
6. [Session Recipes](#session-recipes)
7. [What to Realistically Expect](#what-to-realistically-expect)

---

## The Science

### Binaural Beats & Brainwave Entrainment

**The basic mechanism:**

Your brain generates electrical rhythms at different frequencies depending on your mental state. These rhythms are measurable by EEG (electroencephalography). The main bands:

| Band | Frequency | Associated State |
|------|-----------|--------------------|
| Delta (δ) | 0.5–4 Hz | Deep dreamless sleep, unconscious processing |
| Theta (θ) | 4–8 Hz | Deep relaxation, hypnagogic state, the trance threshold, vivid imagery, reduced critical faculty |
| Alpha (α) | 8–13 Hz | Calm, relaxed alertness, receptive, eyes-closed rest |
| Beta (β) | 13–30 Hz | Alert, analytical, normal waking thought |
| Gamma (γ) | 30–100 Hz | High-level binding, integration of information across brain regions |

**What binaural beats are:**

If you play a 300 Hz tone in your left ear and a 307 Hz tone in your right ear, your brain perceives a third tone — a beat — at the *difference* frequency: 7 Hz. This beat doesn't exist in the air. It's generated entirely inside your auditory cortex as it tries to reconcile two slightly different signals arriving from each ear.

This is called a binaural beat, first documented by physicist Heinrich Wilhelm Dove in 1839. The relevance to consciousness research was developed by Robert Monroe (founder of the Monroe Institute) in the 1970s, who coined the term Hemi-Sync for the resulting hemispheric synchronization effect.

**Entrainment:**

The brain has a tendency to synchronize its dominant electrical rhythm toward a rhythmic external stimulus — *frequency following response* or *neural entrainment*. When you hear a 7 Hz binaural beat continuously, your brain's electrical activity tends to shift toward that frequency — into theta. Theta is the state where the verbal, critical mind quiets, visual and imagistic thinking becomes more natural, hypnotic suggestion takes hold most readily, and the boundary between conscious and subconscious processing becomes permeable.

**Why headphones are required:**

Binaural beats *only work with headphones*. Each ear must receive its own independent frequency. Speakers mix the sounds before they reach you, destroying the effect.

**Research grounding:**

- Oster, G. (1973). Auditory beats in the brain. *Scientific American*, 229(4), 94–102.
- Wahbeh, H., Calabrese, C., & Zwickey, H. (2007). Binaural beat technology in humans: a pilot study to assess psychologic and physiologic effects. *Journal of Alternative and Complementary Medicine*, 13(1), 25–32.
- Becher, A.K., et al. (2015). Intracranial electroencephalography power and phase synchronization changes during monaural and binaural beat stimulation. *European Journal of Neuroscience*, 41(2), 254–263.

---

### Bilateral Visual Stimulation

**What it is:**

Bilateral stimulation is alternating left-right sensory input — in Mindforge's case, alternating flashes on the left and right edges of the screen combined with pink noise alternating between your left and right ear.

**Where it comes from:**

The clinical context for bilateral stimulation is EMDR (Eye Movement Desensitization and Reprocessing) — developed by psychologist Francine Shapiro in 1987. She noticed that moving her eyes rapidly from side to side while thinking about a distressing memory reduced its emotional intensity. Research showed that visual alternation can be replaced by auditory alternation with comparable results.

**Why it works (current theories):**

- **Working memory taxation:** Bilateral stimulation partially occupies working memory, reducing the vividness and emotional charge of whatever the mind is holding — making habituated patterns less "sticky"
- **Hemispheric communication:** Alternating left-right stimulation promotes cross-hemispheric signaling via the corpus callosum, facilitating integration of material previously isolated in one hemisphere
- **REM sleep analog:** The alternating pattern resembles REM sleep, during which the brain consolidates and processes memory

**Research grounding:**

- Shapiro, F. (1989). Eye movement desensitization. *Journal of Behavior Therapy and Experimental Psychiatry*, 20(3), 211–217.
- van den Hout, M.A., et al. (2011). Tones inferior to eye movements in the EMDR treatment of PTSD. *Behaviour Research and Therapy*, 49(2), 147–151.
- Christman, S.D., et al. (2003). Bilateral eye movements enhance the retrieval of episodic memories. *Neuropsychology*, 17(2), 221–229.

---

### Subliminal Suggestion

**What "subliminal" means:**

*Sub* (below) + *limen* (threshold). A subliminal stimulus falls below the threshold of conscious awareness — your eyes and brain register it, but conscious attention does not fully form around it.

The relevant threshold for visual stimuli is approximately 16–50 ms. Text flashed for 16ms is registered by the visual cortex at a pre-conscious level without the person being aware of what they read. Above approximately 200ms, text becomes fully readable.

**Does subliminal suggestion work?**

*What the research shows it can do:*
- Prime subsequent thoughts, feelings, and choices in directions consistent with the subliminal content
- Activate emotional associations connected to subliminal words without conscious awareness
- Influence motivation when the suggestion aligns with an existing goal

*What the research shows it cannot do:*
- Override a deeply resistant conscious position on its own
- Produce dramatic behavioral change in a single session
- Compel action the person genuinely does not want

Subliminal suggestion works best when: (1) congruent with a direction the person already wants to move, (2) delivered repeatedly over multiple sessions, (3) the critical faculty is already quieted by other means.

**The Ericksonian context:**

Mindforge implements Ericksonian *presupposition framing* when linguistic embedding is enabled — raw suggestions are wrapped in framing structures ("As you drift deeper, [suggestion]") that embed the suggestion inside a premise the censor is already accepting.

**Research grounding:**

- Merikle, P.M., Smilek, D., & Eastwood, J.D. (2001). Perception without awareness. *Cognition*, 79(1-2), 115–134.
- Dijksterhuis, A., & Aarts, H. (2010). Goals, attention, and (un)consciousness. *Annual Review of Psychology*, 61, 467–490.
- Bandler, R. & Grinder, J. (1981). *Trance-Formations*. Real People Press.

---

### Receptivity Research: Vasiliev and the Hypnagogic State

**Who was Vasiliev:**

Dr. Leonid Leonidovich Vasiliev (1891–1966) was a Soviet physiologist at Leningrad University who conducted systematic research into mental suggestion from the 1920s through the 1960s. His primary findings were published in *Experiments in Mental Suggestion* (1962; English translation 1963).

**The critical finding:**

Vasiliev's experiments consistently showed that the *hypnagogic state* — the threshold transition from waking to sleep — produced dramatically higher receptivity than any other state. Not sustained deep theta, not delta, not meditative alpha — but the specific *crossing* of the waking-to-sleep boundary, occurring at approximately the 7–8.5 Hz brainwave range.

His passive receiver principle: subjects instructed to stop trying and simply drift showed significantly higher response rates than those actively concentrating on receiving. Effort blocks the mechanism. Passive receptivity opens it.

His Faraday cage experiments placed subjects in electromagnetic shielding — and the effect persisted unchanged. This pointed to the mechanism being entirely the *receiver's internal brain state*, not a transmission medium.

**What this means for Mindforge:**

1. **The hypnagogic window feature** — when live frequency crosses through 6.5–8.5 Hz during descent, suggestion delivery density doubles. The display shows `⟁ hypnagogic window — peak receptivity`.
2. **The progressive descent** — guides the brain gradually through alpha into theta, targeting the crossing itself, not just the destination state.
3. **The passive receptivity instruction** — once the session begins, abandon all effort to participate consciously. Drift.
4. **The Sleep Onset preset** — descends to 3–4 Hz, approaching the boundary Vasiliev documented as yielding deepest receptivity before full sleep.

---

### CIA Gateway Process Report (1983)

**What it is:**

The Gateway Process Report is a declassified CIA document (*Analysis and Assessment of the Gateway Process*, 1983, approved for release 2003) produced by US Army Lt. Col. Wayne M. McDonnell. It was written as a briefing on the Monroe Institute's Hemi-Sync methodology following the Army's investigation.

**Key technical findings:**

- **Optimal carrier frequency: 300 Hz** — The Monroe Institute's research settled on 300 Hz as the carrier tone most effectively producing the entrainment effect. Mindforge defaults to 300 Hz carrier.
- **7.5 Hz as the Gateway sweet spot** — The report identifies 7.5 Hz as the frequency at which the consciousness barrier between waking awareness and deeper processing becomes most permeable. The Gateway ✦ preset targets this.
- **Schumann resonance coherence: 7.83 Hz** — The Earth's ionospheric electromagnetic resonance. Human brainwave patterns in the alpha-theta range appear to have co-evolved in this field. The Schumann ✦ preset targets 7.83 Hz.
- **Resonant frequency building** — Abrupt state changes are less effective than gradual descent that builds resonant coherence incrementally.

---

### Why Combine All Four

| Layer | Barrier | Technique |
|-------|---------|-----------|
| Gatekeeper readiness | Critical faculty at full alert | Pattern interrupt → overloads and suspends evaluation |
| Brainwave state | Mind too alert, critical faculty active | Frequency descent → α→θ, targeting hypnagogic window |
| Neural pattern rigidity | Habituated patterns resist new input | Bilateral stimulation (visual + audio) → loosens fixed states |
| Delivery channel | Conscious mind filters direct suggestion | Subliminal flash + embedding → below evaluation threshold |

Used together, they create a compounding condition: the pattern interrupt disrupts the gatekeeper before it knows the session has begun; the descent guides the brain to the precise state where suggestion is most effective; the bilateral stimulation loosens the grip of existing patterns during delivery; and the subliminal flashing installs new material without triggering the rejection response — with intensity automatically doubled when frequency crosses the hypnagogic window.

---

## Quick Start

1. **Open** https://dezirae-stark.github.io/mindforge/ on your phone or computer
2. **Put on headphones** (required for binaural beats — earbuds work fine)
3. **Write your suggestions** in the Subliminal Suggestions textarea, one per line
4. **Load the Gateway preset** for a fully configured starting point
5. **Set session duration** — 20–30 minutes is a reasonable starting point
6. **Tap "Begin Session"** — a 60-second pattern interrupt will run first (timer shows in orange), then the main session begins
7. **Close your eyes immediately** after the interrupt ends
8. **Stop trying** — do not concentrate, do not evaluate. Drift passively. The Vasiliev passive receptivity principle applies here.
9. The status display shows current phase and frequency band. `⟁ hypnagogic window` means peak receptivity — suggestion density doubles automatically.
10. End chime sounds when the session completes.

---

## Writing Effective Suggestions

**Core principles:**

**1. Present tense, not future**
- Weak: *"I will learn to think in images."*
- Stronger: *"I think in pure images and felt sensation."*
- Strongest: Drop the "I" entirely — *"Thought moves in images. The image is the meaning."*

**2. Positive framing only**
- Weak: *"I don't narrate my experience."*
- Stronger: *"Experience arrives directly, without translation."*

**3. Sensory and felt language over abstract**
- Abstract: *"I have improved mental clarity."*
- Sensory: *"My mind is still water. Thought settles without ripple."*

**4. Short and singular** — one idea per suggestion.

**5. Congruent with genuine desire** — the subconscious filters for authenticity.

**Example set — image-thinking practice:**

```
I think in pure images and felt sensation.
Thought flows without a speaker.
The image is the meaning.
My mind speaks in pictures and impression.
Experience arrives before words.
I see before I say.
The internal voice quiets. Images remain.
Whole knowing, no narrator.
Sensation first. Language second, if at all.
I am fluent in image.
```

**Example set — self-integration / inner stillness:**

```
I am complete without address.
No narrator is needed.
The self is whole, not divided.
What is, is known directly.
I rest in my own presence.
Stillness holds all of it.
No gap between knower and known.
I am home in myself.
```

---

## Frequency Selection Guide

| Preset | Freq | Best For |
|--------|------|----------|
| **δ Delta** | 2 Hz | Very deep states, approaching sleep. Hard to maintain awareness. |
| **θ Theta** | 4 Hz | Deep theta / gateway approach. Heavy trance, minimal critical faculty. |
| **θ Theta** | 6 Hz | Standard theta. Deep trance, hypnagogic threshold, vivid imagery. Primary working state. |
| **θ 7.5 ✦** | 7.5 Hz | CIA Gateway sweet spot. Maximum permeability per Monroe/Gateway research. |
| **Sch 7.83 ✦** | 7.83 Hz | Schumann resonance. Earth-ionosphere coherence frequency. |
| **α Alpha** | 10 Hz | Relaxed, receptive. Good starting state for beginners. |
| **β Beta** | 18 Hz | Alert and focused. Less useful for subconscious work. |
| **γ Gamma** | 40 Hz | High-level integration. Use at end of session to consolidate deep work. |

---

## User Manual — Every Control Explained

### Session Protocol

**Pre-Session Interrupt**
Runs for configured duration (default 60s) before the main session. Sets binaural beat to 4 Hz and fast bilateral at 3.5 cycles/second. The rapid bilateral at deep theta creates cognitive overload — the critical faculty cannot maintain its evaluative function. When it collapses, the main session begins into a temporarily unguarded state. Timer shows orange; status shows "suspending critical faculty…"

**Progressive Frequency Descent**
Ramps the binaural beat gradually from start → mid → end frequency using `linearRampToValueAtTime`. Default: 10 Hz → 7.5 Hz (6 min) → 4 Hz. The hypnagogic window activates when the live frequency crosses 6.5–8.5 Hz.

### Binaural Beats

**Carrier tone:** Default 300 Hz per Monroe Institute / Gateway Process research. Lower carriers feel warmer; higher feel brighter. Entrainment effect is not strongly dependent on carrier.

**Waveform:** Sine (smooth, comfortable) → Triangle (mild harmonics) → Sawtooth (buzzy, penetrating).

### Bilateral Stimulation

**Visual rate:** 0.2–5 cycles/second. Slower (0.2–0.5/s) feels contemplative; faster (3–5/s) more activating. Interrupt phase runs at 3.5/s automatically.

**Audio bilateral:** Pink noise alternating L/R in sync with visual pulses. Delivers the bilateral mechanism through two sensory channels simultaneously.

### Subliminal Suggestions

**Flash duration:**
- 16ms — True subliminal. Visual cortex registers; conscious mind does not.
- 33ms — Liminal. Sometimes glimpsed as a blur. Default.
- 50–100ms — May be briefly perceived as a flash.
- 200ms+ — Fully readable.

**Linguistic Embedding:** Wraps each suggestion in an Ericksonian presupposition frame. Available frames: "As you drift deeper," "Notice how," "You find that," "In this stillness," "With each breath," "Deeper now —". Raw suggestions also appear without frames 30% of the time.

**Voice Delivery:** Web Speech API simultaneous audio at 0.65× speed. Dual-channel delivery: visual flash + whispered suggestion simultaneously.

### Quick Presets

| Preset | Specs |
|--------|-------|
| **Gateway ✦** | 300 Hz carrier, α→7.5 Hz, 60s interrupt, audio+visual bilateral, 30 min |
| **Schumann ✦** | 300 Hz, 12→7.83 Hz, 45s interrupt, 25 min |
| **Deep Work** | 10→6→4 Hz, 60s interrupt, 25 min |
| **Sleep Onset** | No interrupt; 8→4→3 Hz, gentle bilateral, 25 min, no chime |
| **Gentle Entry** | No interrupt; 12→10→8 Hz, 100ms flash, 15 min |

---

## Session Recipes

### Gateway Protocol ✦ (recommended starting point)

| Setting | Value |
|---------|-------|
| Pattern interrupt | On, 60s |
| Descent | On, 10→7.5→7.5 Hz, 8 min to mid |
| Carrier | 300 Hz, Sine |
| Volume | 0.24 |
| Visual bilateral | On, 0.8/s, 80ms, Intensity 0.6 |
| Audio bilateral | On, 0.12 |
| Flash duration | 33ms |
| Interval | 7s, variable |
| Linguistic embedding | On |
| Duration | 30 min |

### Sleep Onset (Vasiliev hypnagogic approach)

Use lying down in a dark room. You may fall asleep. If you do, the work still happened.

| Setting | Value |
|---------|-------|
| Pattern interrupt | Off |
| Descent | On, 8→4→3 Hz |
| Carrier | 300 Hz, Sine |
| Volume | 0.14 |
| Visual bilateral | On, 0.5/s, 60ms, Intensity 0.3 |
| Audio bilateral | Off |
| Flash duration | 50ms |
| Interval | 10s |
| End chime | Off |
| Duration | 25 min |

---

## What to Realistically Expect

**Single session:** Subtle shift in mental tone — greater quietness, easier access to imagery. You may notice nothing consciously. Both are normal.

**After 5–10 sessions:** Suggestions delivered repeatedly may begin to surface as spontaneous thoughts or impulses in daily life.

**After 3–4 weeks consistent use (3–5 sessions/week):** Behavioral and perceptual shifts become more consistent. The internal dialogue may naturally quiet during certain activities.

**What this cannot do:**
- Produce results without consistent repetition
- Override genuinely contradictory beliefs without also working on those consciously
- Replace direct practice of the skill or behavior you are targeting
- Deliver change in a way that bypasses your own willingness

This tool creates conditions. You still do the work.

---

## Safety Notes

- **Epilepsy:** Bilateral visual flashes and rhythmic glow pulses are rhythmic light stimuli. Disable visual bilateral if you have photosensitive epilepsy.
- **Driving / machinery:** Do not use during any activity requiring alertness.
- **Mental health:** Not appropriate during acute psychotic episodes, severe dissociation, or acute mental health crisis.
- **Headphones volume:** Keep low. Entrainment does not require loud audio.
- **Delta and deep theta:** Can cause drowsiness approaching sleep. Do not use lying down where falling asleep poses risk.
- **Consensual sessions:** Telehypnosis Pro and Ganzfeld are for consenting adult participants only.
- **Children:** Not intended for use by minors without adult supervision.

---

## Technical Notes

All six tools are single HTML files with no external dependencies, no frameworks, no trackers, and no server communication. All configuration stored in browser `localStorage`.

**Browser requirements:** Any modern browser with Web Audio API support (Chrome, Firefox, Safari, Edge — mobile and desktop, ~2018 onward). Web Speech API for Mindforge voice delivery (Chrome/Edge have most reliable voice selection).

**Why single files:** Portability and privacy. Each tool can be saved to your device and used entirely offline.

---

*These tools are personal practice and research aids. They are not medical devices, do not diagnose or treat any condition, and make no clinical claims. The research sections describe findings in the scientific literature — they do not constitute proof that these specific implementations will produce any particular result for any specific person.*
