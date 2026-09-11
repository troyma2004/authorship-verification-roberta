# Data interface

The notebooks were written for the COMP34812 authorship-verification CSV files. The original training, development, and AV test inputs were recovered locally in September 2026. Their raw texts are not redistributed in this repository.

| Recovered file | Rows | Labels |
| --- | ---: | --- |
| `train.csv` | 27,643 | 13,950 different-author pairs; 13,693 same-author pairs |
| `dev.csv` | 5,993 | 2,937 different-author pairs; 3,056 same-author pairs |
| AV `test.csv` | 5,985 | None provided |

The development counts agree with the notebook's saved evaluation. The recovered test input has the same row count as `outputs/coursework_predictions.csv`; equal counts alone do not establish prediction correctness or row-by-row correspondence.

## Input schema

| Column | Meaning |
| --- | --- |
| `text_1` | First English text |
| `text_2` | Second English text |
| `label` | Required for training/evaluation: `1` means same author; `0` means different authors. Omitted for unlabelled inference. |

For the Colab workflow, place a CSV you are permitted to use under `/content/data/`. The training implementation expects `train.csv` and `dev.csv` there. The inference notebook defaults to `dev.csv`; change `INPUT_CSV_NAME` to your actual filename. An unlabelled inference file needs only `text_1` and `text_2`.

A surviving 20-pair demo input was inspected during archive preparation. Its raw texts are not included. The corresponding historical binary output is retained at [`../outputs/demo_predictions.csv`](../outputs/demo_predictions.csv). It is distinct from the full coursework prediction file.
