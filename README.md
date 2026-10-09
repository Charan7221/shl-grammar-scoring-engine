# SHL Grammar Scoring Engine 2026

## Project Overview

An automated grammar scoring system developed for the SHL Hiring Assessment 2026. The system processes spoken English audio recordings and predicts a continuous grammar proficiency score between 0 and 5.

## Methodology

- **Audio preprocessing:** Librosa for waveform loading, resampling, and acoustic feature extraction.
- **Speech recognition:** Faster-Whisper for converting spoken audio into text.
- **Grammar analysis:** Linguistic features and LanguageTool-based grammar analysis where available.
- **Feature engineering:** 55 acoustic and linguistic features.
- **Machine learning:** CatBoost regression, compared with ExtraTrees.
- **Optimization:** CatBoost hyperparameter tuning with five-fold cross-validation.

## Dataset

- Training recordings: 769
- Testing recordings: 216
- Audio format: WAV

The competition audio files are not included in this repository.

## Model Performance

| Metric | V1 | V2 |
|---|---:|---:|
| Training RMSE | 0.208816 | 0.138468 |
| Out-of-fold RMSE | 0.704620 | 0.694009 |
| Out-of-fold Pearson | 0.822992 | 0.829263 |
| Kaggle leaderboard score | 0.6455 | 0.6400 |

V2 achieved a better validation RMSE and Kaggle leaderboard score. The substantial difference between training and validation errors indicates possible overfitting.

## Project Files

- `notebook54ecd4478f.ipynb` — Original end-to-end audio processing and baseline model.
- `shl-grammar-scoring-v2-final.ipynb` — Optimized CatBoost training and prediction pipeline.

V2 uses engineered features produced by V1. To reproduce the pipeline, attach the official SHL competition dataset and the required engineered-feature data.

## Limitations

Automatic transcription can normalize grammatical mistakes in spontaneous speech. Grammar-checking tools may not capture every error, and the small training dataset limits generalization. Cross-validation metrics are estimates and do not guarantee leaderboard performance.

## Technologies

Python, Kaggle, Librosa, Faster-Whisper, LanguageTool, CatBoost, scikit-learn, Pandas, NumPy, Matplotlib.

## Assessment

SHL Hiring Assessment 2026 — Grammar Scoring Engine for Spoken Audio.
