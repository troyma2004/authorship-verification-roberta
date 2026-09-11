# Archive scope and provenance

Prepared in September 2026 from the surviving Group 35 Solution C coursework artifacts. The original submission is retained separately by the author.

## What this repository preserves

- The Python code cells of the submitted training and inference notebooks, unchanged.
- Historical text outputs from the notebooks, including a partial training log and the final development confusion counts.
- Four sets of saved model/tokenizer configurations and inference metadata. There are no trained parameter files.
- Two historical binary-prediction CSV files, identified separately in `outputs/README.md`.

Notebook introductions were replaced with archive notices. Transient Colab widget state, widget display outputs and download HTML/JavaScript were removed for readable static notebook rendering. This does not constitute a fresh execution. Documentation was rewritten around the surviving evidence; outdated PDFs and the inaccessible model-download link are omitted.

## Reproducibility boundaries

The trained weights and the original training/development data are no longer available. The ensemble-fitting/search code is not among the surviving artifacts. The inference constants were selected for the original checkpoints and should not be assumed suitable for newly trained models.

The training code declares `AUTO_PACKAGE_BUNDLES` but does not implement bundle export. It also uses historical `transfomer_roberta_*` directory names for three models, whereas the inference notebook and retained metadata folders use `transformer_roberta_*`. The notebooks retain their historical Colab paths and input defaults. These details are preserved as part of the submitted code, not advertised as an automated training-to-inference workflow.

## Evaluation evidence

The final-ensemble classification figures are derived from the saved development confusion counts: TP 2,797, TN 2,176, FP 761 and FN 259 (5,993 pairs). Development data also informed model selection, bucket weights, thresholds and specialist blending. These figures are not an independent test evaluation.

AUC, EER, log loss and Brier score values appearing in earlier coursework prose have been omitted because the surviving Solution C artifacts do not substantiate them. Per-example development probabilities are unavailable. The extra-metrics code remains visible in the archived notebook, without claims that its output has been recovered.

Saved inference metadata also records individual-model selected epochs and thresholded classification metrics. These are historical metadata records; they were not recomputed when preparing the archive.

## Environment record

The notebooks target Google Colab with Python, PyTorch, Hugging Face Transformers, NumPy and related libraries listed by their import/install cells. Saved Hugging Face model configs record Transformers 5.3.0. This single recorded version is not a complete tested environment or dependency lockfile.

No new training or neural inference was performed during archive preparation.
