# Weights registry

Rule: **if the licence forbids commercial use, server-side use, or redistribution in any form we cannot honour, the model does not ship.** This file is the reason a model is in the registry or out of it — not a wish list.

## Allowed (planned for the registry)

| Model | Lane | Licence | Why it is in | Note |
|---|---|---|---|---|
| Real-ESRGAN (x4plus, ONNX export) | upscale | BSD-3-Clause (code); weights released by the same project | permissive, runs on CPU via onnxruntime, our own measured output | ONNX exports in the wild are community re-exports — pin one, hash it, and state the source |
| SeedVR2 | upscale / restore (video) | Apache-2.0 | one-step restoration, no NDA gate | needs a GPU to be useful; the CLI must say "CPU: slow, not recommended" rather than pretend |

## Excluded, with the reason

| Model | Licence problem | What we do instead |
|---|---|---|
| CodeFormer, StableSR | S-Lab Licence 1.0 — non-commercial | not bundled; document the manual step |
| SUPIR | forbids use behind a paid service | not bundled |
| FLUX.2 klein 9B | the 9B checkpoint is non-commercial (4B is Apache-2.0) | if a redraw lane ships weights, they are the 4B one |
| Qwen-Image-2.1 | research-only terms | never bundled |

## Verification checklist for a new entry

1. Open the licence file at the source, not a mirror.
2. Record the exact version/tag and the SHA-256 of the file we actually load.
3. State the commercial answer in one sentence, with the licence text that supports it.
4. If it is ambiguous, it is out. Ambiguity is what a takedown is made of.

*This file is a technical record, not legal advice. If a model's licence changes upstream, the entry is removed in the same commit.*
