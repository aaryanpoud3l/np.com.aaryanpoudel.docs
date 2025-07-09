---
title: "OSS Application Playground"
date: 2025-07-09T21:02:00+00:00
categories: ['Blogs']
tags: ["blog"] 
---
### Music Generation

#### Ace-step:
- Open Source. [Github](https://github.com/ace-step/ACE-Step)
- Tried on M1 Air 8GB. During generation, ran into out of memory error as the swap usage exceeded 9GB

Setup:
```sh
git clone https://github.com/ace-step/ACE-Step.git
cd ACE-Step
python -m venv .venv
source .venv/bin/activate

pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
# Or, for Nvidia 
# pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126

pip install -e .

acestep --port 7865
```

#### Suno.ai
- Paid proprietary music gen
- Created great songs but I think it's free tier is for non commercial use

---

### Tools

#### Comfy UI
- [Download](https://www.comfy.org/download)
