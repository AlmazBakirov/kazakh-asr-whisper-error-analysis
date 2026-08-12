# Kazakh ASR Error Analysis with Whisper

Test-task solution for **“Where ASR breaks on Kazakh”**.

## Goal

Evaluate a pretrained multilingual ASR model on Kazakh speech and analyze where recognition fails. The focus is on real measurements, error types, Kazakh-specific failure modes, limitations of the evaluation, and what should be improved first.

## Experiment design

- **Model:** `openai/whisper-small`
- **Dataset:** Google FLEURS, Kazakh configuration `kk_kz`
- **Split:** `test`
- **Audio:** at least **10 minutes** of Kazakh speech
- **Training:** none; pretrained Whisper is evaluated as-is
- **Metrics:** raw WER, normalized WER, CER
- **Error analysis:** substitutions, deletions, insertions, Kazakh-specific character confusions, morphology-like candidates, worst utterances
- **Environment:** Google Colab GPU

The notebook collects complete utterances until cumulative audio duration is at least 600 seconds, so the final duration may be slightly above 10:00.

## How to run

1. Open `kazakh_asr_whisper_10MIN_FINAL.ipynb` in Google Colab.
2. Select **Runtime → Change runtime type → GPU**.
3. Run **Runtime → Run all**.
4. The notebook saves outputs into `results/` and creates `kazakh_asr_results.zip`.

## Generated outputs

After a successful run the notebook produces files including:

- `predictions.csv` — reference and Whisper transcription for each utterance
- `errors.csv` — utterances containing recognition errors
- `word_errors.csv` — token-level edit operations
- `metrics.json` — WER/CER and runtime statistics
- `technical_error_counts.csv` — substitution/deletion/insertion counts
- `kazakh_character_error_rates.csv` — descriptive character-level analysis
- `worst_15_examples.csv` — highest-WER real examples
- `report_draft.md` — detailed data-grounded report

## Evaluation choices

Text normalization lowercases text, removes punctuation and normalizes whitespace, but does **not** merge Kazakh-specific letters, spell-correct outputs, or convert number words to digits. This avoids artificially hiding meaningful ASR errors.

The experiment intentionally uses one model and one corpus subset. The purpose is deeper analysis of actual failure cases rather than a broad model leaderboard.

## Limitations

The final WER/CER values apply only to the evaluated FLEURS subset. They should not be generalized to all Kazakh speech, especially spontaneous dialogue, noisy recordings, regional accents, call-center audio, or Kazakh–Russian code-switching.

## AI assistant disclosure

An AI assistant was used to help design the experiment, write/review evaluation code, structure the error analysis, and prepare the report template. All predictions, metrics, error examples, and quantitative conclusions in the final submission come from the actual notebook run.
