# Data interface

The notebooks were written for the COMP34812 authorship-verification CSV files. Original text datasets are not distributed in this archive. The original training and development files are no longer available to the author.

| Column | Meaning |
| --- | --- |
| `text_1` | First English text |
| `text_2` | Second English text |
| `label` | Required for training/evaluation: `1` means same author; `0` means different authors. Omitted for unlabelled inference. |

The supplied training implementation expects `train.csv` and `dev.csv` in its historical Colab workspace. The inference notebook defaults to `dev.csv`; an unlabelled run originally used a test file with the first two columns.

A surviving 20-pair demo input was inspected during archive preparation. Its raw texts are not included. The corresponding historical binary output is retained at [`../outputs/demo_predictions.csv`](../outputs/demo_predictions.csv). It is distinct from the full coursework prediction file.
