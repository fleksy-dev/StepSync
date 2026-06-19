# StepSync model — GitHub Release asset

This folder holds the **optional high-accuracy model** that the app downloads on
demand (the small model is bundled in the app under `assets/models/`).

Upload the `.onnx` file as an asset to a **GitHub Release** (this folder is
git-ignored on purpose — do not commit the large file to the repo).

## Files
| File | Size | sha256 |
|------|------|--------|
| `beat_this_full_int8.onnx` | 23.3 MB | `a870f6da3825623ef9d5ccb9321472d4bf7de1c938a80baeec652fcc6d08e2f0` |

(Bundled in-app, for reference: `beat_this_small_int8.onnx` — 4.7 MB —
sha256 `763cc4d671a016958614c0c98aa949a4c31a6769523c44c5c4c0e2f8fa5b920c`.)

## What it is
"Beat This!" beat/downbeat tracker (full variant, transformer_dim 512), exported
to ONNX and dynamically int8-quantized for on-device inference. Input:
log-mel spectrogram `(1, 1500, 128)` (22050 Hz, n_fft 1024, hop 441, 128 mel,
log1p(1000·x), 50 fps). Output: beat & downbeat logits `(1, 1500)`.

## License
Model weights © 2024 Institute of Computational Perception, JKU Linz — MIT
License. See `LICENSE-beat_this.txt`. Original: https://github.com/CPJKU/beat_this

## After uploading
The app references the release URL + sha256 to download and verify the file. Fill
the URL into the app's model manifest once the release tag exists, e.g.:
`https://github.com/<you>/StepSync/releases/download/<tag>/beat_this_full_int8.onnx`
