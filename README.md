# Image-Detailed-Description-GEnerator-AI-model-


---

# 🧠 Image Detailed Description Generator

> A multimodal AI pipeline that generates rich, multilingual, audio-augmented visual descriptions using BLIP-2, YOLOv5, LLaMA, NLLB, and LoRA fine-tuning.

---

## 📌 Project Summary

This project combines powerful vision-language models with user-guided fine-tuning and translation capabilities to generate **semantic, natural-language image descriptions**. It enables:

* **Object detection** with YOLOv5
* **Caption generation** with BLIP-2
* **Descriptive language enrichment** using LLaMA
* **Multilingual translation** using Facebook NLLB
* **Speech output** with Google TTS
* **LoRA fine-tuning** via PEFT for interactive improvement

---

## 🧰 Tech Stack

| Area                     | Library / Model                               |
| ------------------------ | --------------------------------------------- |
| Object Detection         | `YOLOv5m` via Ultralytics                     |
| Captioning               | `BLIP-2` (Salesforce/blip2-flan-t5-xl)        |
| Language Enhancement     | `LLaMA 2` GPTQ (7B model from TheBloke)       |
| Multilingual Translation | `facebook/nllb-200-distilled-600M`            |
| Text-to-Speech           | `gTTS`                                        |
| UI                       | `Gradio`                                      |
| Fine-tuning              | `PEFT + LoRA`                                 |
| Embedding & Memory       | `torch`, `accelerate`, `optimum`, `auto-gptq` |

---

## 🔄 Pipeline Overview

```
   │
   ├─> 🎯 YOLOv5 — detect and count objects
   │
   ├─> 🧠 BLIP-2 — generate initial caption
   │
   ├─> ✍️ (Optional) Fine-tune BLIP-2 on user correction using LoRA
   │
   ├─> 💬 LLaMA 2 — convert caption into a detailed paragraph
   │
   ├─> 🌐 NLLB — translate into selected target language
   │
   └─> 🔊 gTTS — generate audio of translated description
```

---

## 🚀 Features

* ✅ **Interactive fine-tuning**: Real-time BLIP-2 updates with your caption corrections
* 🖼️ **YOLOv5 integration**: Object names + counts enrich the prompt
* 🧾 **Prompt engineering**: Combined caption + object summary into rich prompts
* 🌍 **7-language multilingual support**: French, German, Hindi, Arabic, Malayalam, etc.
* 🔊 **Speech synthesis**: Translated text into `.mp3` audio via gTTS
* 📊 **BLEU and ROUGE evaluation ready** (support for metrics included)

---

## 🔬 Models Used

### 🧠 BLIP-2 (Vision-Language Model)

* `Salesforce/blip2-flan-t5-xl` used for generating the **initial caption**.
* Supports LoRA-based on-the-fly fine-tuning with `peft`.

### 🧭 YOLOv5 (Object Detector)

* Pretrained `yolov5m.pt` model from Ultralytics
* Used to identify and count key objects for prompt augmentation.

### 🧾 LLaMA 2 (Refiner)

* 7B GPTQ quantized model from TheBloke repo
* Takes YOLO objects + BLIP caption and rewrites as a **descriptive paragraph**.

### 🌍 NLLB-200 (Translator)

* `facebook/nllb-200-distilled-600M`
* Translates refined captions to user-selected languages using token ID forcing.

### 🔊 Google TTS

* `gTTS` converts translated text to **spoken audio** (`caption_audio.mp3`).

---

## 💻 Installation

```bash
git clone https://github.com/niya-benny/Image-Detailed-Description-GEnerator-AI-model-
cd Image-Detailed-Description-GEnerator-AI-model-

pip install transformers sentencepiece bitsandbytes accelerate
pip install torch torchvision torchaudio
pip install ultralytics gtts optimum auto-gptq gradio peft evaluate rouge_score textstat
```

Download YOLOv5m:

```bash
wget https://github.com/ultralytics/yolov5/releases/download/v6.0/yolov5m.pt
```

---

## 📒 Notebook Reference

See [`img.ipynb`](img.ipynb) for full working pipeline:

* Upload → Detection → Captioning → Prompt → Generation → Translation → Audio

You can run this in Colab, Jupyter, or VS Code with minimal config.

---

## 📸 Sample Use Case


---

## 👩‍💻 Author

* GitHub: [niya-benny](https://github.com/niya-benny)


