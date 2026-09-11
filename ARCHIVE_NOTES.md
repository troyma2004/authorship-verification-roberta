# Archive scope and provenance

Prepared in September 2026 from the Group 35 Solution C coursework artifacts, then expanded after recovery of the original checkpoints and data. The original submission is retained separately by the author.

## What this repository preserves

- The submitted training and inference implementations, with archive/recovery notices and dependency setup pinned to the recorded Transformers version.
- Historical text outputs from the notebooks, including a partial training log and the final development confusion counts.
- Four sets of saved model/tokenizer configurations and inference metadata, plus a manifest for all four recovered trained checkpoints. The checkpoint bundle has been prepared separately; release upload is pending.
- Two historical binary-prediction CSV files, identified separately in `outputs/README.md`.

Notebook introductions were replaced with archive/recovery notices. Transient Colab widget state, widget display outputs and download HTML/JavaScript were removed for readable static notebook rendering. Both notebooks' install cells now pin Transformers 5.3.0, as recorded in the saved model configs. These are release-preparation changes; model training and ensemble logic remain the coursework implementation. They do not constitute a fresh execution. Documentation was rewritten around the available evidence; outdated PDFs and the old model-download link are omitted.

## September 2026 recovery

All four safetensors checkpoints were recovered from the author's local coursework directory. Each file is 498,612,800 bytes and contains 201 tensors with 124,647,170 parameters. Static checks verified file hashes and tensor headers, and confirmed that the accompanying model configurations, tokenizers, and inference metadata match the previously retained artifacts. The recovered `config_resolved.json` files differ from the repository copies only in historical output/checkpoint paths; their shared hyperparameters agree. File hashes in [`models/model_manifest.json`](models/model_manifest.json) describe the files inside the prepared `models.zip` bundle, including those original resolved paths.

The recovered data contains 27,643 labelled training pairs, 5,993 labelled development pairs, and 5,985 unlabelled AV test pairs. Counts and schemas were inspected without publishing text examples. Development labels match the recovered course development reference in row order. The coursework prediction CSV has the same number of rows as the test input; this does not verify its predictions or their row-by-row correspondence.

Raw course datasets, course handouts, papers, and the separately supplied multi-task scorer/baselines are not included in the public repository. The latter are not presented as part of the author's Solution C implementation. Recovery adds the original checkpoints and stronger artifact provenance; it does not add an independent test score or a new model run.

## Reproducibility boundaries

The recovered checkpoints and their metadata support the intended inference workflow described in the README. Original training/development data is retained locally rather than redistributed. The ensemble-fitting/search code is not among the recovered artifacts. The inference constants were selected for the original checkpoints and should not be assumed suitable for newly trained models.

The training code declares `AUTO_PACKAGE_BUNDLES` but does not implement bundle export. It also uses historical `transfomer_roberta_*` directory names for three models, whereas the inference notebook and retained metadata folders use `transformer_roberta_*`. The notebooks retain their historical Colab paths and input defaults. These details are preserved as part of the submitted code, not advertised as an automated training-to-inference workflow.

For a newly trained model, the documented manual metadata structure is `{"config": <config_resolved.json contents>, "threshold": <selected threshold>}` in `inference_metadata.json`, alongside the model's `hf_model/` directory. Creating this file and aligning directory names does not reproduce the missing ensemble search. The release bundles already contain the original inference metadata.

## Evaluation evidence

The final-ensemble classification figures are derived from the saved development confusion counts: TP 2,797, TN 2,176, FP 761 and FN 259 (5,993 pairs). Development data also informed model selection, bucket weights, thresholds and specialist blending. These figures are not an independent test evaluation.

AUC, EER, log loss and Brier score values appearing in earlier coursework prose have been omitted because the surviving Solution C artifacts do not substantiate them. Per-example development probabilities are unavailable. The extra-metrics code remains visible in the archived notebook, without claims that its output has been recovered.

Saved inference metadata also records individual-model selected epochs and thresholded classification metrics. These are historical metadata records; they were not recomputed when preparing the archive.

## Environment record

The notebooks target Google Colab with Python, PyTorch, Hugging Face Transformers, NumPy and related libraries listed by their import/install cells. Saved Hugging Face model configs record Transformers 5.3.0. This single recorded version is not a complete tested environment or dependency lockfile.

No new training or neural inference was performed during archive preparation or checkpoint recovery. The full notebook workflow has not been rerun in a fresh environment.
