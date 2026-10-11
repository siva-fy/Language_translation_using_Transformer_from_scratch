# Transformer from scratch · English → French

An educational TensorFlow notebook implementing an encoder–decoder Transformer
for English-to-French translation. It explores attention, causal masking,
sequence preparation and training on paired sentences.

## Repository guide

- [`Transformer_language _translation.ipynb`](Transformer_language%20_translation.ipynb)
  is the actual training notebook. Its filename contains a space.
- [`eng_-french.csv`](eng_-french.csv) contains the paired text used by the notebook.
- `EB11_E20CSE184_full_paper.docx` contains the accompanying project write-up.

## Open and inspect

```bash
git clone https://github.com/siva-fy/Language_translation_using_Transformer_from_scratch.git
cd Language_translation_using_Transformer_from_scratch
```

Open the notebook in Jupyter or Google Colab. It imports TensorFlow, pandas,
NumPy and Matplotlib. For a local environment, install those packages plus
Jupyter in a virtual environment compatible with the notebook's TensorFlow 2.x
code. This repository does not currently provide a requirements file or a
validated dependency lockfile.

Before running all cells:

1. In Colab, upload `eng_-french.csv` to `/content/`. Locally, change the
   `file_path` cell from `/content/eng_-french.csv` to the local CSV path.
2. Check the checkpoint configuration. The notebook uses the legacy
   `/tmp/checkpoint/` weight-saving path; your TensorFlow/Keras version may
   require a different checkpoint format or filename.
3. Review training cost: the notebook requests up to 50 epochs with early
   stopping. Run cells incrementally before a full training session.

## Training and evaluation

The notebook shuffles the data and uses a 70% training / 20% validation / 10%
test split. Training tracks sparse categorical cross-entropy and token accuracy.

Token accuracy is not a standalone measure of translation quality. Historical
notebook results should not be interpreted as a reproducible translation
benchmark: the shuffle is not seeded, dependency versions are not locked, and
the documentation update did not rerun training. A stronger evaluation would
record the exact split, environment, held-out translation metrics and qualitative
error examples.

## Acknowledgements

The original project README credits [Attention Is All You Need](https://arxiv.org/abs/1706.03762)
by Vaswani et al. for the architecture and the [Tatoeba Project](https://tatoeba.org/eng/downloads)
for English–French sentence pairs, distributed in the
[TensorFlow translation dataset](http://storage.googleapis.com/download.tensorflow.org/data/fra-eng.zip).
Those acknowledgements are retained here.

For an offline, testable evaluation example, see
[Retrieval Eval Lab](https://github.com/siva-fy/retrieval-eval-lab).
