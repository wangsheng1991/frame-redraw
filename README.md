# frame-redraw

**An open, cross-platform enhancer for images and video frames — and an honest answer to "what can I do without an NVIDIA card, a Windows install, or a subscription".**

Status: `v0.0` — scaffold. Nothing here claims a result we have not measured yet. The first runnable lane lands with `v0.1`; see [Roadmap](#roadmap).

## What this is

A command-line workbench that takes an image or a frame and returns a better one, with the recipe saved next to the output. Every lane prints what model it used, what it cost in time, and which licence the weights carry.

Lanes (planned):

| Lane | Job | Backend | Runs on |
|---|---|---|---|
| `upscale` | 2× / 4× resolution | Real-ESRGAN (ONNX) | macOS Intel/ARM, Linux, Windows (CPU) |
| `restore` | denoise, deblur, old-photo repair | TBD — permissive weights only, see [MODELS.md](MODELS.md) | CPU |
| `redraw` | lighting / material style change at the same composition | hosted API (optional), local fallback | CPU or hosted |
| `bench` | run the same input through every lane, write timing + hashes | — | CPU |

## What this is not

- **Not DLSS.** It does not patch games, does not ship NVIDIA code, does not touch a game's rendering pipeline, and cannot make a game run faster. `DLSS` is a trademark of NVIDIA Corporation; this project is independent and unaffiliated.
- **Not a drop-in Topaz replacement today.** Topaz Video AI does temporal models we do not have. Where we are worse, the comparison table says so.
- **Not a wrapper around someone else's binary.** If a step needs a proprietary tool, it is documented as a manual step, not bundled.

## Install (planned, `v0.1`)

```sh
python3 -m venv .venv && . .venv/bin/activate
pip install -r requirements.txt
python -m frame_redraw upscale in.jpg -o out.png --scale 4 --recipe recipe.json
```

`requirements.txt` will hold `onnxruntime`, `numpy`, `pillow` only. No PyTorch, no CUDA, no NVIDIA SDK — that is the whole point: it has to run on the laptop that is already on the desk.

## Why an open project at all

The "DLSS 5 visual enhancer" results are dominated by Windows-only C++ tools that patch games. That is a real answer to a different question. The question we can answer is narrower and honest: *my screenshot / my footage looks soft or flat — what can I run right here, for free, without a 12 GB GPU?*

Open source is what makes that claim checkable: the code, the weights list, the licences and the recipes are all in the repository.

## Roadmap

- [ ] `v0.1` — `upscale` lane with Real-ESRGAN ONNX, tile-based, real timing on an Intel i9-9880H (macOS) published in `BENCH.md`
- [ ] `v0.1` — `bench` lane: one input, every lane, `recipe.json` + SHA-256 of input and output
- [ ] `v0.2` — `restore` lane (denoise / deblur) with permissive weights only
- [ ] `v0.2` — `redraw` lane bridge to the hosted API, opt-in, no key in the repository
- [ ] `v0.3` — video: frame extract → lane → re-encode, with the caveat that there is no temporal model and therefore no flicker-free guarantee
- [ ] `v1.0` — comparison page against paid tools, measured on the same files, published with the fixtures

## Licence

Apache-2.0 for the code. Model weights keep their own licences and are never redistributed here — [MODELS.md](MODELS.md) lists them with links and the reason each one is allowed. If a licence forbids commercial or server-side use, the model does not go in the registry.
