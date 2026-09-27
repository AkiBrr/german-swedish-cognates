# German-Swedish Historical Cognate Discovery

Independent computational research project on historical lexical relations between German and Swedish, combining historical linguistics with NLP methods.

## Overview

This project investigates whether Swedish words that resemble German words are genuinely inherited cognates, borrowings from (Middle Low) German, shared third-language loans, or accidental look-alikes -- and whether this can be detected automatically at the scale of full-language lexicons.

The work is split into two connected parts.

Part 1 (Paper 1): Does derivational morphology add evidence beyond phonology and semantics for distinguishing inherited cognates from integrated Swedish borrowings?

Part 2 (Phase 2): An automatic discovery and ranking pipeline for historical word relations across the full Swedish and German lexicons (about 51k and 96k entries respectively).

## Methodology highlights

- Strict frozen-protocol discipline: thresholds, features, models, splits and labels are never retrofitted after seeing a held-out result. A failed gate is recorded as a failure; any redesign becomes a new, separately versioned pipeline stage.
- - No expert human annotators were available, so historical and morphological labels are produced via multiple independent, label-blind LLM runs plus blind adjudication of disagreements -- explicitly reported as LLM inter-run agreement rather than human inter-annotator agreement.
  - - A hand-built gold set of 150 Swedish-German pairs across five relation classes (inherited, Swedish borrowing, shared third-language loan, accidental similarity, uncertain), split with grouping to avoid leakage across related lemma families.
    - - A multi-stage retrieval-and-classification architecture: candidate retrieval (part-of-speech match plus gloss and lemma similarity, fused by reciprocal rank fusion) feeding a relatedness gate, feeding a conditional classifier -- iterated across several gate versions as earlier ones failed open-set generalization checks.
      - - Every reported precision and recall number is on a fresh, previously unseen holdout, with uncertain cases explicitly excluded from precision calculations rather than folded in either direction.
       
        - ## Status
       
        - Active research. Paper 1's confirmatory morphology gate did not pass reliability checks, so morphology's independent contribution is reported as exploratory rather than established. Phase 2's discovery pipeline is on its fourth gate iteration, with the most recent precision-first ranker in blind third-pass adjudication.
       
        - ## Why this repo exists
       
        - This is independent work, unrelated to my day job, done for its own sake out of interest in historical linguistics and NLP. Code and data will be added incrementally as pipeline stages are finalized.
