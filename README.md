# VDE Inference Examples

Single-file inference examples for VDE acceleration on FLUX.1, Qwen-Image, Wan2.1, and Z-Image.

## Files

- `VDE4FLUX/inference_flux1.py`
- `VDE4QwenImage/inference_qwenimage.py`
- `VDE4Wan2.1/inference_wan.py`
- `VDE4Z-Image/inference_z-image.py`
- `VDE4Z-Image/inference_z-image-turbo.py`

Each script supports normal inference and VDE inference. Add `--vde` to enable VDE, then tune `--stable-step` and `--interval`.

## Quick Checks

```bash
python scripts/check_python_syntax.py VDE4FLUX/inference_flux1.py VDE4QwenImage/inference_qwenimage.py VDE4Wan2.1/inference_wan.py VDE4Z-Image/inference_z-image.py VDE4Z-Image/inference_z-image-turbo.py
python scripts/check_runtime_env.py --target flux
```

## Examples

```bash
bash VDE4FLUX/run_inference_flux1.sh
bash VDE4QwenImage/run_inference_qwenimage.sh
bash VDE4Wan2.1/run_inference_wan.sh
bash VDE4Z-Image/run_inference_z-image.sh
bash VDE4Z-Image/run_inference_z-image-turbo.sh
```

Override model locations with environment variables or command-line arguments:

```bash
FLUX_MODEL=/path/to/FLUX.1-dev bash VDE4FLUX/run_inference_flux1.sh
QWENIMAGE_MODEL=/path/to/Qwen-Image QWENIMAGE_DIFFUSERS_SRC=/path/to/diffusers/src bash VDE4QwenImage/run_inference_qwenimage.sh
WAN21_CKPT_DIR=/path/to/Wan2.1-T2V-1.3B WAN21_REPO_ROOT=/path/to/Wan2.1 bash VDE4Wan2.1/run_inference_wan.sh
ZIMAGE_MODEL=/path/to/Z-Image-Turbo ZIMAGE_DIFFUSERS_SRC=/path/to/diffusers/src bash VDE4Z-Image/run_inference_z-image.sh
ZIMAGE_TURBO_MODEL=/path/to/Z-Image-Turbo ZIMAGE_REPO_SRC=/path/to/Z-Image/src bash VDE4Z-Image/run_inference_z-image-turbo.sh
```

Use `scripts/check_runtime_env.py --target <name>` before a full run to verify the required Python packages and local paths. Valid targets are `flux`, `qwenimage`, `wan`, `zimage`, and `zimage-turbo`.

By default, the release scripts use public model identifiers where the underlying loader supports them. Some models may require accepting the upstream license or logging in to Hugging Face before download.

## Notes

- Image/video outputs are ignored by `.gitignore`.
- Local model weights are not included.
- For Wan2.1 and native Z-Image-Turbo, install the corresponding upstream repository dependencies before running the scripts.
