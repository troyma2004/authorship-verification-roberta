# Authorship Verification with a RoBERTa Ensemble

Predicting whether two English texts were written by the same author using four fine-tuned RoBERTa cross-encoders, pair-order consistency, and an ensemble conditioned on text length.

I implemented **Solution C in its entirety** for the University of Manchester's COMP34812 Natural Language Understanding coursework in 2026. This was part of Group 35's submission, with group members Kanav Gupta, Xiao Ma, and Yangsong Zhou. This repository presents my Solution C implementation.

## Archive status

This is an archive of the implementation and surviving experiment artifacts. **The trained weights, training/development datasets, and ensemble-search code are no longer available. The published inference notebook cannot run as distributed.** The files under `models/` preserve metadata, configurations, and tokenizers; they do not include trained checkpoints.

The notebooks retain the training and inference implementations. Their frozen ensemble weights and thresholds belong to the original trained checkpoints: they should not be treated as validated settings for newly trained models. This archive has not been rerun to reproduce the reported result.

## Approach

- **Anchor model:** RoBERTa-base cross-encoder, with both text orders used during training and their probabilities averaged at inference.
- **Hard-negative continuation:** focal loss and extra weight for different-author pairs with high lexical overlap or URL/email/number-related features. The lexical-overlap rule uses a 2.5× weight; the special-feature rule uses 2×, taking the larger weight when both apply.
- **Symmetry continuation:** a consistency penalty between predictions for the two text orders.
- **Long-text specialist:** a continuation of the hard-negative model, trained on long pairs with a 384-token window instead of 256.

The first three models are combined using separate weights and classification thresholds for 12 buckets, defined by total word count and the difference between the two text lengths. The long-text model is blended into long and extra-long buckets. These ensemble settings were tuned on the development set. Raw text is preserved without lowercasing or URL/email/number normalisation.

## Recorded result

The saved inference output covers **5,993 development pairs**:

| Metric | Value |
| --- | ---: |
| Accuracy | 82.98% |
| Macro F1 | 0.8280 |

| Actual / predicted | Same author | Different authors |
| --- | ---: | ---: |
| Same author | 2,797 | 259 |
| Different authors | 761 | 2,176 |

These metrics are consistent with the saved confusion counts. The development set was also used for checkpoint selection, threshold tuning, ensemble weighting, and specialist blending. **This is a tuned development result, not an independent test score.** The archived prediction CSVs contain no labels or verified test scores.

## Repository contents

| Path | Contents |
| --- | --- |
| `train_Group_35_C.ipynb` | Training implementation and partial saved training output |
| `demo_Group_35_C.ipynb` | Inference implementation, frozen ensemble settings, and saved development output |
| `models/` | Surviving model metadata, configurations, and tokenizers; no trained weights |
| `outputs/demo_predictions.csv` | 20 archived demo predictions |
| `outputs/coursework_predictions.csv` | 5,985 archived coursework predictions |
| `data/README.md` | Input schema and dataset availability |
| `MODEL_CARD.md` | Technical details, evaluation provenance, and limitations |
| `ARCHIVE_NOTES.md` | Preservation choices, environment record, and reproducibility boundaries |

The notebooks were written for Google Colab with PyTorch and Hugging Face Transformers. Reading the implementation and saved outputs does not require the missing datasets or checkpoints; executing the full workflow does. No fresh-environment or end-to-end reproduction is claimed.

## Development tools

Generative AI tools, including Gemini, ChatGPT, and Claude, assisted with debugging, boilerplate, evaluation formatting, and documentation editing during the coursework.
