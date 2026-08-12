# Results

Final run on Google FLEURS Kazakh (`kk_kz`) test data using pretrained `openai/whisper-small`.

- Evaluated speech: **10.13 minutes**
- Utterances: **37**
- Raw WER: **80.25%**
- Basic-normalized WER: **69.57%**
- Basic-normalized CER: **21.30%**
- Word substitutions: **368**
- Word deletions: **60**
- Word insertions: **27**
- GPU: **NVIDIA Tesla T4**

Substitutions were the dominant word-level error type. The notebook also analyzes Kazakh-specific Cyrillic character confusions and morphology-like candidates. These linguistic categories are treated as exploratory hypotheses rather than proven causes.

The metrics apply only to this small FLEURS subset and should not be generalized to all Kazakh speech, especially spontaneous dialogue, noisy audio, regional accents, or Kazakh–Russian code-switching.

AI assistance was used for experiment design, code review, and report structure. All reported predictions, metrics, and examples come from the actual notebook run.
