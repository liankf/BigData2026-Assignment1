# Assignment 1: SVD for fine-tuning LLMs

## Files
- assignment1_q1_q3.ipynb: baseline, rank comparison, training time and rank-16 component comparison.
- assignment1_q4.ipynb: original Layer 0/7/15 query-projection SVD and plots.
- results/: Q1/Q2 and Q3 result tables, Q4 50%-energy summary, and three complete 2,048-value spectra.

## Run on Kaggle
Enable GPU T4 x2 and Internet; attach a Hugging Face read secret named HF_TOKEN with approved Llama access. The notebooks install their dependencies.
For Q1/Q2 choose RUN_STAGE="q1_q2"; for four fresh Q3 runs choose "q3". The current "q3_remaining" reuses the measured v11 default and trains only quarter/half/bottom. Run Q4 independently. Set CURRENT_NOTEBOOK_VERSION to the actual new execution version before Save & Run All. Keep the course model/data/training/evaluation defaults.

## Measured results and sources
Baseline/r16: Kaggle v11; r64: v12; r256: v13; Q4: v14; Q3 quarter/half/bottom: v15. Q3 default reuses v11. Optimized code v16/v17 was QuickSaved without new GPU measurements. Accuracies use 1,000 examples per task; times cover successful training loops only. Full model weights remain in Kaggle Output.

The rank-256 retry changed the CUDA allocator after an OOM. Q3 v11/v15 used different PyTorch versions. Results are single-seed observations; training-data fingerprints were not saved. The report explains these limitations.

Code is adapted from the [course implementation](https://github.com/nycubigdata-2026fall/BigData2026-Assignment1/tree/b1521186a8a516a4e81482d5e6ad5f587d9aae52), based on [PiSSA](https://arxiv.org/abs/2404.02948).
Model: meta-llama/Llama-3.2-1B, revision 4e20de362430cd3b72f300e6b0f18e50e7166e08.
