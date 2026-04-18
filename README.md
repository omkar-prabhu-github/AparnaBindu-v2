# 🪷 Aparna Bindu v2

**A hybrid AI-powered Kolam classification and design platform — SIH Finalist Project**

Aparna Bindu is a full-stack application that preserves and celebrates the ancient South Indian art of **Kolam** (rangoli) through deep learning classification and interactive design tools. This is **Version 2**, featuring a fully functional CNN-ViT hybrid classification backend and a premium redesigned frontend.

---

## ✨ Features

### 🧠 AI Classification Engine
- Upload any Kolam image and get instant classification
- **CNN-ViT Hybrid Model** achieving **88% accuracy** (up from 80% in v1's CNN-only approach)
- Classifies across 13 traditional Kolam categories: Butterfly, Cow, Creeper, Elephant, Fish, Flower, Footprint, Geometric, Kambi, Loops, Om, Peacock, and more
- Real-time inference via FastAPI backend

### 🎨 Interactive Kolam Designer
- Design your own Kolam patterns using a hex-code grid system
- Visual grid overlay with intuitive controls
- Export and share your creations

### 🖼️ Kolam Gallery
- Browse 2800+ curated Kolam designs across 13 categories
- Lazy-loaded pagination (25 images per batch) for smooth performance
- Lightbox zoom viewer with subtle backdrop blur
- Responsive masonry-style grid layout

### 🏗️ Premium UI/UX
- Traditional amber/orange theme with glassmorphism effects
- Smooth `framer-motion` animations throughout
- Fully responsive across mobile, tablet, and desktop
- Pinned footer with consistent layout structure

---

## 🏆 Our SIH Journey

This project was built for the **Smart India Hackathon (SIH)**. Here's our journey:

| Phase | Model | Accuracy | Details |
|-------|-------|----------|---------|
| **v1.0** | CNN Only | 80% | Standard Convolutional Neural Network for baseline classification |
| **v2.0** | CNN-ViT Hybrid | 88% | CNN extracts local geometric features, Vision Transformer (ViT) captures global topology and symmetry |

Our hybrid architecture and polished UI earned us a spot as **SIH Finalists**, competing against brilliant teams across the nation.

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|-----------|---------|
| **React 19** | UI framework |
| **TypeScript** | Type-safe development |
| **Vite 7** | Build tool & dev server |
| **Tailwind CSS 4** | Utility-first styling |
| **Framer Motion** | Animations & transitions |
| **React Router v7** | Client-side routing |
| **Lucide React** | Icon library |

### Backend
| Technology | Purpose |
|-----------|---------|
| **Python** | ML model & API server |
| **PyTorch** | Deep learning framework |
| **timm** | Pre-trained model architectures (ConvNeXt, ViT) |
| **FastAPI** | REST API server |
| **Uvicorn** | ASGI server |
| **Pillow** | Image preprocessing |

---

## 🚀 Getting Started

### Prerequisites
- **Node.js** v18+
- **Python** 3.10+
- **Git LFS** (for downloading the model weights)

### 1. Clone the repository

```bash
git clone https://github.com/omkar-prabhu-github/AparnaBindu-v2.git
cd AparnaBindu-v2
```

### 2. Install & run the frontend

```bash
npm install
npm run dev
```

The frontend will start at `http://localhost:5173`

### 3. Set up the classification backend

```bash
cd model
python -m venv venv

# Windows
venv\Scripts\activate
# macOS/Linux
source venv/bin/activate

pip install -r requirements.txt
```

### 4. Start the API server

```bash
cd model
python server.py
```

The backend will start at `http://localhost:8000`

### 5. Use the app
- Open `http://localhost:5173` in your browser
- Navigate to **Classify Kolam** to upload and classify images
- Navigate to **Design a Kolam** to create patterns
- Browse the **Gallery** for 2800+ curated designs

---

## 📁 Project Structure

```
AparnaBindu-v2/
├── public/
│   └── kolam_gallery/         # 2800+ curated Kolam images (13 categories)
│       ├── butterfly/
│       ├── cow/
│       ├── creeper/
│       ├── elephant/
│       ├── fish/
│       ├── flower/
│       ├── footprint/
│       ├── geometric/
│       ├── kambi/
│       ├── loops/
│       ├── om/
│       └── peacock/
├── src/
│   ├── components/
│   │   ├── About.tsx           # SIH journey & team page
│   │   ├── Background.tsx      # Animated background
│   │   ├── ClassGallery.tsx    # Category detail view with pagination
│   │   ├── ClassifyKolam.tsx   # AI classification interface
│   │   ├── KolamDesigner.tsx   # Interactive designer tool
│   │   ├── KolamGallery.tsx    # Gallery dashboard
│   │   ├── PulliKolam.tsx      # Pulli Kolam specific page
│   │   ├── header.tsx          # Navigation header
│   │   ├── footer.tsx          # Site footer
│   │   └── home.tsx            # Landing page
│   ├── data/
│   │   ├── class-images.json   # Image inventory per category
│   │   └── gallery-data.json   # Category metadata
│   ├── App.tsx                 # Router & app shell
│   ├── index.css               # Global styles
│   └── main.tsx                # Entry point
├── model/
│   ├── kolam_hybrid_model.py   # CNN-ViT hybrid architecture definition
│   ├── kolam_dataset.py        # Dataset loader & augmentation
│   ├── predict_single_image.py # Single image inference pipeline
│   ├── prepocesses.py          # Data preprocessing utilities
│   ├── server.py               # FastAPI classification server
│   ├── requirements.txt        # Python dependencies
│   └── kolam_convnext_vit_best(early).pth  # Trained model weights (~323MB, Git LFS)
├── package.json
├── vite.config.ts
├── tsconfig.json
└── README.md
```

---

## 🏛️ Architecture

```
┌─────────────────┐     ┌──────────────────────┐     ┌─────────────────┐
│   React Frontend │────▶│   FastAPI Backend     │────▶│  PyTorch Model  │
│   (Vite + TS)   │◀────│   (Uvicorn @ :8000)  │◀────│  CNN-ViT Hybrid │
└─────────────────┘     └──────────────────────┘     └─────────────────┘
        │                        │                          │
   Gallery / Designer     Image Upload /              ConvNeXt (local)
   Classify UI            Preprocessing               + ViT (global)
```

**Classification Pipeline:**
1. **Data Ingestion** — User uploads a Kolam image through the React UI
2. **Preprocessing** — Image is resized, normalized, and converted to tensor format
3. **Hybrid Inference** — CNN extracts fine geometric details; ViT captures global pattern topology
4. **Result Delivery** — Predicted class and confidence score returned to the frontend

---

## 👥 Team

| Name | Role |
|------|------|
| **Vishal** | Team Leader |
| **Omkar** | Team Member |
| **Vaishnavi** | Team Member |
| **Amruth** | Team Member |
| **Nakul** | Team Member |
| **Niranjan** | Team Member |

---

## 📄 License

This project was developed as part of the Smart India Hackathon. All rights reserved.

---

<p align="center">
  <i>Preserving tradition, inspiring creativity.</i><br>
  <b>Aparna Bindu</b> — Where ancient art meets modern AI.
</p>
