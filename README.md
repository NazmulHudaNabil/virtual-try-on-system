# 👗 Virtual Try-On System
 
A computer vision project that lets you digitally change clothing on any person photo using AI segmentation and inpainting — runs completely free on Google Colab.

##  Demo
https://github.com/user-attachments/assets/33a57524-a512-4a81-bd10-765c8fc5da7c


---
 
## 🧠 How It Works
 
```
Upload Image → Preprocess (512×512) → CLIPSeg Segmentation → SD Inpainting → Result
```
 
1. **Upload** a photo of a person
2. **Select** Upper Body or Lower Body
3. **Describe** the clothing you want — *"black leather jacket"*, *"blue jeans"*
4. The AI segments the clothing region and replaces it with your description
---
 
## 🔧 Tech Stack
 
| Component | Tool | Purpose |
|-----------|------|---------|
| Segmentation | [CLIPSeg](https://huggingface.co/CIDAS/clipseg-rd64-refined) | Zero-shot text-guided clothing mask |
| Inpainting | [Stable Diffusion Inpainting](https://huggingface.co/runwayml/stable-diffusion-inpainting) | AI clothing generation |
| UI | [Gradio](https://gradio.app) | Clean interactive interface |
| Runtime | Google Colab (T4 GPU) | Free GPU execution |
 
---
 
## 🚀 Getting Started
 
### Run on Google Colab (Recommended)
 
1. Open the notebook in Google Colab
2. Set runtime to **T4 GPU** → `Runtime → Change runtime type → T4 GPU`
3. Run all cells in order (Cell 1 → Cell 6)
4. First run downloads models (~2 GB, one time only)
5. Gradio launches with a public shareable link
### Local Setup
 
```bash
git clone https://github.com/your-username/virtual-tryon
cd virtual-tryon
pip install diffusers transformers accelerate torch torchvision pillow gradio numpy opencv-python-headless xformers
jupyter notebook virtual_tryon_free.ipynb
```
 
---
 
## 📁 Project Structure
 
```
virtual-tryon/
│
├── virtual_tryon_free.ipynb   # Main notebook (all 6 cells)
├── README.md                  # This file
└── sample_outputs/            # Example result images
```
 
---
 
## 📓 Notebook Structure
 
| Cell | Purpose |
|------|---------|
| Cell 1 | Install all dependencies |
| Cell 2 | Imports & device configuration |
| Cell 3 | Load CLIPSeg + Stable Diffusion models |
| Cell 4 | Pipeline functions (preprocess, segment, inpaint) |
| Cell 5 | Main orchestrator connecting all steps |
| Cell 6 | Gradio UI with dark theme |
 
---
 
## 🎯 Features
 
- ✅ Upload any person photo
- ✅ Upper body and lower body selection
- ✅ Prompt-based clothing editing (*"red hoodie"*, *"white formal shirt"*)
- ✅ Segmentation mask preview
- ✅ Quick-pick example prompts
- ✅ Clean dark-themed Gradio UI
- ✅ 100% free — no API keys, no paid credits
---
 
## 🧩 Pipeline Details
 
### Segmentation — CLIPSeg
CLIPSeg is a zero-shot segmentation model. We pass a text prompt like *"upper clothing"* and it returns a probability heatmap. We threshold at 0.4 and apply Gaussian blur to smooth mask edges for natural blending.
 
### Inpainting — Stable Diffusion
`runwayml/stable-diffusion-inpainting` fills only the masked region with AI-generated clothing matching the prompt, while preserving the face, background, and body pose.
 
---
 
## ⚙️ Requirements
 
- Python 3.9+
- CUDA GPU recommended (runs on CPU but slow)
- ~4 GB VRAM for GPU inference
- ~2 GB disk for model weights
---
 
## 📌 Notes
 
- Images are internally resized to 512×512 for Stable Diffusion compatibility
- First run takes 2–3 minutes for model download; subsequent runs are fast
- For best results, use well-lit front-facing photos
---
 
## 📄 License
 
MIT License — free to use, modify, and distribute.
 
---
 
*Built as a Computer Vision exam project using CLIPSeg + Stable Diffusion Inpainting.*
