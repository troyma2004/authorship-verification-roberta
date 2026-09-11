# Historical prediction files

These files are retained coursework outputs, not newly generated predictions.

| File | Rows | Meaning |
| --- | ---: | --- |
| `demo_predictions.csv` | 20 | Historical small-demo output; identical to the Category C output in the original demo submission archive. |
| `coursework_predictions.csv` | 5,985 | Original full coursework prediction output. |

Both contain one `prediction` column with binary values (`1`: same author; `0`: different authors), in the input order expected by the original submission. The exact input-to-output correspondence has not been recomputed for this archive because the trained weights are unavailable. No labels or independent test scores are supplied.

The inference notebook's saved development run contains 5,993 examples; neither prediction CSV is that development evaluation. The development confusion matrix and its scope are recorded in [`../MODEL_CARD.md`](../MODEL_CARD.md).
