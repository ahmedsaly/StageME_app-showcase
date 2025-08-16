# StageME — Blinded Multi-Reviewer Staging for Hair/Skin Microscopy (Showcase)

> A lab-grade workflow to **pair multi-stain microscopic images**, review them **blindly and in randomized order**, capture **multi-reviewer staging** with comments & final decisions, and export **audit-ready Excel/PDF** reports.

<img width="2878" height="1556" alt="image" src="https://github.com/user-attachments/assets/0d41e256-58c1-45b3-bbda-985850718052" />


---

## About this repo

This repository is a **showcase** of StageME’s capabilities using **videos/GIFs only**.  
It does **not** include production source code (proprietary to the employer).

```
StageME_app-showcase/
├─ README.md
└─ demo_videos/
   ├─ main_features.mkv
   └─ extended_features.mp4
```

---

## 🎯 Scientific objective — what “staging” means and why it matters

In hair/skin research, **staging** classifies a sample’s biological state in the **hair follicle cycle** (e.g., *Anagen → Catagen → Telogen*, with sub-stages and dystrophic variants) based on **histological/morphological evidence**.  
Researchers typically inspect **paired stains**—for example:

- **Ki67** (cell proliferation)  
- **Masson–Fontana** (melanin/pigmentation)

…and may also consult **auxiliary imagery** (e.g., macroscopic photos or other channels). StageME makes this process **faster, more consistent, and less biased** by:

- **Randomizing** the order of image pairs and optionally **hiding filenames** (reduces label/anchoring bias).  
- Enabling **independent multi-reviewer** assessments (Researcher 1 → Researcher 2 → Team Lead adjudication).  
- Preserving a **traceable audit trail** of decisions (reviewer ID, class, comments, “final” flag).  
- Producing **structured exports** (Excel/PDF) that are easy to share, analyze, and reuse (e.g., for QC or training ML models).

---

## 🧪 What StageME does

- **Auto-pair multi-stain images** from the same sample (e.g., *Ki67* ↔ *Masson–Fontana*) based on filenames.  
- **Handle duplicates & unmatched cases**  
  - If multiple images map to one sample, StageME shows them and lets you pick the **best representative**.  
  - If auto-match fails, you can **ignore**, **classify solo**, or **manually match**.  
- **Bias controls**  
  - **Randomize** viewing order; **toggle/hide filenames**.  
- **Rich review tools**  
  - **Zoom**, **reset**, **brightness**, **contrast**.  
  - Attach up to **4 additional images** per sample (e.g., macroscopic image or other stains/channels).  
- **Multi-reviewer capture**  
  - Enter **Name/ID** once; for each pair select **Classification**, mark **Final?** if applicable, and add **Comments**.  
  - Saved entries are persisted and listed for subsequent reviewers (no re-work).  
- **Exports**  
  - **Excel**: grouped columns per reviewer (1st/2nd/3rd…), includes image paths and references to additional images.  
  - **PDF**: per-sample pages with image panels/thumbs and a **metadata table** (Reviewer/Classification/Final/Comments).

---

## 🧭 Workflow

1. **Select project root** → choose a **staging type** (e.g., microscopic HF, macroscopic HF, etc.).  
   - On first run, specify the two main stain folders (e.g., **Ki67** and **Masson–Fontana**).  
   - On later runs, connecting to the **project folder** is enough; prior data auto-loads.  
2. Choose **Random order** (recommended) or **Ordered by name**.  
3. StageME **auto-matches** stain pairs by name.  
   - If duplicates exist, select the **best representative**.  
   - For unmatched images, choose **solo**, **ignore**, or **manual pair**.  
4. Review each pair: **zoom**, **brightness/contrast**, **toggle names**, and optionally attach **aux images**.  
5. Save your entry (**Ctrl+S**): **Name/ID**, **Class**, **Final?**, **Comments**.  
6. Browse **Pre-saved** entries (current + previous sessions). Clear/adjust if needed.  
7. **Export** for sharing or analysis (**Excel** and/or **PDF**).

---

## 🖼️ Demos (what each GIF shows)

### `demo_videos/main_features.mkv`
- Project setup → choose **staging type** → pick **random order**.  
- **Automatic pairing** of Ki67 / Masson–Fontana with optional **hidden filenames**.  
- Reviewer workflow: **zoom**, **brightness/contrast**, **comments**, **mark final**, **save** (JSON persisted).  
- **Pre-saved list** showing accumulated entries across reviewers.  
- **Exports**: Excel (grouped reviewer columns) and PDF (image panels + metadata table).


<img src="demo_videos/main_features_1.gif" width="800">

<img src="demo_videos/main_features_2.gif" width="800">




### `demo_videos/extended_features.mp4`
- **Duplicate detection** dialog → choose the **best representative** image.  
- **Unmatched handling**: **classify solo**, **don’t show**, or **find match manually** (file dialog).  
- Continue staging; **subsequent reviewers** see prior pairings/entries and **don’t need to re-match**.


<img src="demo_videos/extendedFeatures.gif" width="800">

---

## ✅ Supported staging categories (examples)

*(Exact naming/coding can be tailored to lab conventions.)*

- **Microscopic Hair Follicle (HF)**: *Anagen (A), Early Catagen (EC), Mid Catagen (MC), Late Catagen (LC), Dystrophic Anagen (DA), Dystrophic Catagen (DC), Degenerative (D), Not Specified (NS).*  
- **Macroscopic Hair Follicle (HF)**: *Anagen (A), Catagen (C), Dystrophic (DY), Degenerative (D).*  
- **Microscopic Hair/Scalp (HS)**: *A, EC, MC, LC, DA, DC, Miniaturized (MI), NS.*  
- **Androgenetic HS**, **Alopecia Areata HS** (with appropriate class sets and tooltips).

---

## 📦 Data captured & outputs

- **Per-image/pair entries** (persisted): Reviewer **Name/ID**, **Classification**, **Final?**, **Comments**, and links to **paired** & **additional** images.  
- **Excel**: tidy, analysis-ready spreadsheet with grouped reviewer columns, image paths, and auxiliary references.  
- **PDF**: shareable report per sample (images + metadata table).  
- **Intended downstream uses**: QC/audit, inter-rater analysis, and as a **labeled dataset** slice for training/validating **AI models**.

---

## ⌨️ Controls & helpful tips

- **← / →** navigate pairs  
- **Ctrl + S** save entry  
- **1** cycle classification options  
- Use **Zoom / Reset**, **Brightness / Contrast**, and **Show/Hide names** to control the viewing context.  
- For the most unbiased review, prefer **Random order** and **Hide names**.

---

## 🛠️ Tech used in the real app

- **PyQt5** (desktop UI)  
- **OpenCV / Pillow** (image I/O & transforms)  
- **pandas / openpyxl** (Excel export)  
- **ReportLab** (PDF export)  
- Packaged with **PyInstaller**

*(This showcase does not include the production code.)*

---

## 🚀 Roadmap / next steps

- **Inter-rater agreement** in exports (e.g., Cohen’s κ) + disagreement views for fast adjudication.  
- **Notifications** (email/Teams/Slack) when Reviewer 1 completes a batch.  
- **Dataset export for ML** (balanced splits, stratified by stage; JSON schema).  
- **Caching/tiling** for large images and network drives; optional thumbnails.  
- **Configurable parsers** for varied naming schemes; batch rename helpers.  
- **Role-based views** (trainee vs. lead) and **approval workflow**.  
- **Merge additional lab workflows** into the same UI.

---

## 🔒 IP & attribution

This repository contains **only media** (GIFs) and documentation to demonstrate StageME’s design and capabilities.  
The production code is **proprietary** to the employer and is **not included**.
