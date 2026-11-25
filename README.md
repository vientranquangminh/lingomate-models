# Lingo Mate models

Speech recognition models that the Lingo Mate app downloads on the phone, so speech is
recognised on the device and audio never leaves it.

The files are published as **GitHub Release assets**. The app's Offline packs screen
downloads them from the URLs set in Firebase Remote Config (`asr_models`) and checks each
file against its SHA-256 before using it.

## Releases

| Tag | File | Model | Size | SHA-256 |
|-----|------|-------|------|---------|
| `whisper-base-v1` | `ggml-base.bin` | Whisper base (multilingual), whisper.cpp format | _xxx MB_ | `_sha256_` |

Download URL pattern:

```
https://github.com/<owner>/lingo-mate-models/releases/download/<tag>/<file>
```

## Versioning

- One tag per model version, for example `whisper-base-v1`, `whisper-small-q5_1-v1`.
- Assets of a published release never change. A new or updated model gets a new tag.
- After publishing a release, update `asr_models` in Remote Config with the new URL, size
  and SHA-256. Phones pick it up on their next start.

## Adding a model

1. Download the model from the upstream source below and keep its file name.
2. Compute its checksum: `shasum -a 256 <file>` (macOS) or `sha256sum <file>` (Linux).
3. Draft a new release with a new tag, attach the file and publish.
4. Add a row to the table above.

## Sources and licences

| File | Source | Licence |
|------|--------|---------|
| `ggml-*.bin` | [ggerganov/whisper.cpp](https://huggingface.co/ggerganov/whisper.cpp), converted from [OpenAI Whisper](https://github.com/openai/whisper) | MIT |
| `silero_vad.onnx` | [snakers4/silero-vad](https://github.com/snakers4/silero-vad) | MIT |

The models are redistributed unchanged under their original MIT licences. All credit goes
to their authors.
