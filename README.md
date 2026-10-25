<h1 align="center">🎬 Video-in-Video Steganography · Deep Learning</h1>

<p align="center">A convolutional autoencoder hides an entire video — and its audio — inside another video, then reveals it.</p>

<p align="center">
  <img src="https://img.shields.io/badge/model-CNN%20autoencoder-ff6f00" alt="Autoencoder">
  <img src="https://img.shields.io/badge/reveal%20accuracy-%3E95%25%20(val)-brightgreen" alt="Accuracy">
  <img src="https://img.shields.io/badge/repo-docs%20only-lightgrey" alt="Docs only">
</p>

<p align="center"><img src="https://github.com/user-attachments/assets/e8df4c41-08ed-4fc3-9aab-8a7b36d21a10" width="760" alt="Cover, stego, secret and revealed frames"></p>

> Final-year engineering project. **Code, trained weights and data aren't in this repo.** This page
> documents the method and results. [Details →](#status--known-issues)

## Why

Image and audio steganography can only hide a little data before quality suffers. Video has far more
capacity, so a learned encoder can hide a whole video in another one.

## Approach

| | Video | Audio |
|---|---|---|
| **Data** | 644 cover + 644 secret clips, 15 s at 30 fps → 300 frames each (≈ 386 k frames) | Self-recorded 10 s mono clips, 80/10/10 split |
| **Pre-processing** | 224 × 224 frames, normalised | Stereo → mono, trim/pad to cover length |
| **Model** | Prep → hide → reveal CNN autoencoder | Encode → conceal (3×3 convs) → decode |
| **Result** | Reveal accuracy **> 95 %** on validation; hiding loss falls more slowly | Converges, with training and validation curves close |

```mermaid
flowchart LR
    S["Secret frame"] --> P["Prep network"]
    C["Cover frame"] --> H["Hiding network"]
    P --> H
    H --> ST["Stego frame"]
    ST --> R["Reveal network"]
    R --> RS["Recovered secret"]
```

<table>
  <tr>
    <td width="50%"><img src="https://github.com/user-attachments/assets/48978160-e1ed-436a-b9fa-d455c27b6df5" alt="Video model"><br><sub>Video model architecture</sub></td>
    <td width="50%"><img src="https://github.com/user-attachments/assets/bf16fb2e-e8b5-4c56-a241-798a90400319" alt="Audio model"><br><sub>Audio model architecture</sub></td>
  </tr>
  <tr>
    <td><img src="https://github.com/user-attachments/assets/030d3456-1137-441f-a015-97de24eb7ea1" alt="Train/val loss"><br><sub>Training vs validation</sub></td>
    <td><img src="https://github.com/user-attachments/assets/0fb228b5-c050-484b-8992-3d52232ccce7" alt="Audio result"><br><sub>Audio result</sub></td>
  </tr>
</table>

<details>
<summary><b>Encoder / decoder flowcharts and accuracy curve</b></summary>
<br>
<img src="https://github.com/user-attachments/assets/2cd489fe-b376-4a11-b9cd-a3bab08d6522" width="480" alt="Encoder">
<img src="https://github.com/user-attachments/assets/4c3c56b5-bbc8-4f0e-b47d-eb29bac0bdf5" width="480" alt="Decoder">
<img src="https://github.com/user-attachments/assets/1f66e630-f261-4a85-9f40-2b9b2382d25d" width="560" alt="Accuracy">
</details>

**Hardware used:** RTX 3050-class GPU, 16 GB RAM, 512 GB SSD.

## Status & known issues

| Issue | Effect |
|---|---|
| **No code, weights or dataset in the repo** | Results can't be reproduced |
| "Accuracy" used for a reconstruction task | PSNR and SSIM are the standard metrics and should be reported |
| Frame-by-frame hiding | No temporal consistency, so possible flicker between frames |
| No compression test | H.264 re-encoding may destroy the hidden video |
| GUI mentioned but not shown | The section is empty |

## Roadmap

- [ ] Publish the training/inference notebook and a small sample set
- [ ] Report PSNR and SSIM for stego and revealed frames
- [ ] Test robustness to H.264; add a temporal (3D-conv) model
