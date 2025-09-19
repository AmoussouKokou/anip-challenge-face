Anip challenge

# Tâche 1 — Reconnaissance faciale robuste (matching 1-à-1)

Ce projet livre **un seul notebook** (`T1_face_matching.ipynb`) qui va de bout-en-bout :
1) lecture des images (train/test)  
2) détection + alignement des visages  
3) extraction d'embeddings (modèle pré-entraîné ArcFace/AdaFace via `insightface`)  
4) évaluation sur un split dev (ROC/EER + simulation de matching)  
5) **matching 1-à-1** sur le **test** avec l’algorithme **Hongrois**  
6) export du **CSV de soumission** : `outputs/tache1_submission.csv`

## Arborescence minimale

tache1_face_matching/
├─ T1_face_matching.ipynb
├─ src/
│ ├─ face_io.py
│ ├─ detect_align.py
│ ├─ embedder.py
│ ├─ matching.py
│ └─ metrics_dev.py
├─ configs/
│ └─ config.yaml
├─ data/
│ ├─ train/ # XXXX_0.jpg et XXXX_1.jpg
│ └─ test/ # 2000 images à apparier
├─ outputs/
│ └─ (sera rempli par le notebook : tache1_submission.csv, figures)
├─ weights/ # (optionnel si léger tuning)
├─ requirements.txt
└─ .gitignore


## Installation rapide

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt
```
