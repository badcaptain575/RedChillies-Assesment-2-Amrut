# Assessment 2: Auralis Nova Key Visual

Advertising images for **Auralis Nova**, a fictional wireless headphone from the fictional brand **Auralis**. Made in ComfyUI with the FLUX.1 [dev] image model, then enlarged 4x. No stock photos or input images were used.

---

## 1. Project overview

The brief asks for one cinematic ad image where the headphones are the main subject and there is empty space for text. This repo has **three colour versions**. Rose Gold is the main submission. Blue and Black are alternatives.

Each colour has its own folder, and each folder holds three files: the 1280 x 720 image, the 4x enlarged image (5120 x 2880), and a text file with the prompt.

| Colour | Folder | Role |
|---|---|---|
| Rose Gold | `Auralis Nova Rosegold` | **Main submission** |
| Blue | `Auralis Nova Blue` | **Main submission** |
| Black | `Auralis Nova Black` | **Main submission** |

None of the images contain text, logos or watermarks. The brand name is not in the prompts on purpose, because AI image models usually spell it wrong. The empty space is there so the brand name and copy can be added afterwards.

```text
README.md

├── Auralis Nova Rosegold/   (720 image, upscaled image, prompt .txt)
├── Auralis Nova Blue/       (720 image, upscaled image, prompt .txt)
└── Auralis Nova Black/      (720 image, upscaled image, prompt .txt)
workflow/
└── Redchilles Assesment 2 - (Amrut).json
```

---

## 2. Dataset structure

Not applicable. The images are generated from a text prompt. There is no dataset.

---

## 3. Installation steps

1. Use ComfyUI on a GPU with 24 GB of memory or more. This project used one NVIDIA L4 (24 GB) on Jarvis Labs.
2. Download the FLUX.1 [dev] model file (about 17 GB):
   ```bash
   mkdir -p ComfyUI/models/checkpoints
   wget -c -O ComfyUI/models/checkpoints/flux1-dev-fp8.safetensors \
     "https://huggingface.co/Comfy-Org/flux1-dev/resolve/main/flux1-dev-fp8.safetensors"
   ```
3. Download `4x-UltraSharp.pth` (Kim2091/UltraSharp) and put it in `ComfyUI/models/upscale_models/`.
4. Start ComfyUI, drag `workflow/auralis_nova_flux_dev.json` onto the screen, and press `R` to refresh the model lists.

No extra custom nodes are needed.

---

## 4. Training instructions

Not applicable. No model was trained. FLUX.1 [dev] was used as it is.

---

## 5. Prediction instructions (how to generate an image)

1. Open the workflow file in ComfyUI.
2. In **Load Checkpoint**, pick `flux1-dev-fp8.safetensors`. In **Load Upscale Model**, pick `4x-UltraSharp.pth`.
3. Paste a prompt (below, or from the text files) into the **CLIP Text Encode (Prompt)** box. Leave the **NEG** box empty. FLUX ignores negative prompts, so unwanted things have to be avoided by how the prompt is worded.
4. Click **Run**. The workflow makes a 1280 x 720 image, enlarges it 4x to 5120 x 2880, and saves it.
5. Run several times and keep the cleanest result. The seed is random each time.

### Settings used

| Setting | Value | What it does |
|---|---|---|
| Image size | 1280 x 720 | Size before enlarging |
| Steps | 30 | Number of refinement rounds |
| FluxGuidance | 3.0 | How closely the image follows the prompt |
| Seed | Random | Different result every run. The seeds of the final images were not saved |
| Sampler / scheduler / CFG / denoise | euler / simple / 1.0 / 1.00 | Left at the values used in the workflow |
| Enlarging | 4x-UltraSharp, 4x | 1280 x 720 becomes 5120 x 2880 |

### Prompts

**Rose Gold**
```text
Luxury hero product shot, a pair of polished silver titanium wireless over-ear headphones with soft cream leather cushions floating in mid-air, upright as if worn on an invisible head, three-quarter front view, perfectly symmetrical, both ear cups identical in size and angle, headband forming one smooth continuous arc, correct realistic proportions, accurate real-world product geometry, crisp specular highlights on the metal, plain smooth ear cups with no logo and no markings, positioned on the right third of the frame, headphones fill about 55 percent of the frame height, smooth soft white to light grey gradient background, soft studio light, a faint blurred reflection and shadow far below, the left half of the frame is empty soft grey-white, 85mm lens, ultra-sharp, photorealistic
```
The prompt says "silver titanium", but the model produced a rose gold finish. The folder is named after the result, not the prompt.

**Blue**
```text
Luxury hero product shot, a pair of premium wireless over-ear headphones in deep midnight navy anodized aluminium with navy fabric cushions, floating in mid-air, upright as if worn on an invisible head, three-quarter front view, perfectly symmetrical, both ear cups identical in size, shape and angle, headband forming one smooth continuous arc with identical left and right arms, one single smooth cushion on each ear cup, correct realistic proportions, accurate real-world product geometry, smooth plain outer ear cup surfaces with no logo, no markings and no buttons, positioned on the right third of the frame, headphones fill about 60 percent of the frame height, soft slate blue to pale grey gradient background with a gentle glow behind the product, crisp cool rim light on the edges, one single soft clean shadow directly beneath the headphones with a faint matching reflection in the same spot, the left half of the frame is empty smooth gradient, 85mm lens, sharp focus, ultra-detailed, photorealistic
```

**Black**
```text
Luxury cinematic hero product shot, a pair of premium wireless over-ear headphones in matte graphite aluminium with black leather cushions, floating in mid-air, upright as if worn on an invisible head, three-quarter front view, perfectly symmetrical, both ear cups identical in size, shape and angle, headband forming one smooth continuous arc with identical left and right arms, one single smooth cushion on each ear cup, correct realistic proportions, accurate real-world product geometry, smooth plain outer ear cup surfaces with no logo, no markings and no buttons, crisp white rim light along the metal edges, positioned on the right third of the frame, headphones fill about 60 percent of the frame height, deep charcoal gradient background with a soft halo of light behind the product, glossy dark floor, one single soft shadow directly beneath the headphones with a sharp faint matching reflection in the same spot, the left half of the frame is empty smooth dark gradient, 85mm lens, shallow depth of field, ultra-detailed, photorealistic
```

---

## 6. Model used

| Item | Value |
|---|---|
| Image model | FLUX.1 [dev], fp8 version (`flux1-dev-fp8.safetensors`, from Comfy-Org/flux1-dev on Hugging Face, about 17 GB) |
| Enlarging model | 4x-UltraSharp (`4x-UltraSharp.pth`) |
| Tool | ComfyUI |
| Hardware | Jarvis Labs, 1x NVIDIA L4, 24 GB |
| Licence | FLUX.1 [dev] is non-commercial. It was used here only for this assessment. |

---

## 7. Image preprocessing

- **Before generating:** nothing. There is no input image.
- **After generating:** one 4x enlargement with 4x-UltraSharp (1280 x 720 to 5120 x 2880). No retouching, colour changes, fixes or text were added.

---

## 8. Evaluation results

Checked against the brief:

| Requirement | Result |
|---|---|
| Minimum 720 px | Pass. 1280 x 720 originals and 5120 x 2880 enlarged versions |
| Landscape | Pass (16:9) |
| PNG or high-quality JPEG | Pass (PNG) |
| Headphones are the main subject | Pass. They fill about 55 to 60 percent of the image height |
| Empty space for text | Pass, but see the first limitation below |
| No accidental text, watermarks or signatures | Pass. The hinges, sliders and ear cup edges were checked zoomed in on the 1280 x 720 images, which is where FLUX most often adds fake text |
| No visible flaws | Mostly pass. See limitations |

How the final images were chosen: several images were generated for each colour. Images were rejected for uneven ear cups, bent headbands, double shadows, and stray marks or letters on the headband and hinges.

---

## 9. Known limitations

- **Product placement:** The headphones appear near the centre rather than on one side, leaving less useful space for advertising copy.
- **Visual concept:** Immersive sound is not shown directly; the images rely on materials and lighting.
- **Image defects:** The upscale can look over-sharp. The Black version has mismatched floor shadows and a tiny speck; the Rose Gold version has faint texture on the left hinge.
- **Colour mismatch:** The Rose Gold result came from a silver titanium prompt.
- **Reproducibility and licence:** Final seeds were not saved, so exact images cannot be reproduced. FLUX.1 [dev] is non-commercial and was used only for this assessment.
- **Fictional brand:** Auralis and Auralis Nova are made-up names.
