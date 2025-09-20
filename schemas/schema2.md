             +--------------------+
             | data/train/        |
             | (images XXXX_0/1)  |
             +--------------------+
                       |
                       v
        +-----------------------------------+
        | read_train_pairs(TRAIN_DIR)       |
        | → [(id, img0, img1), ...]         |
        +-----------------------------------+
                       |
                       v
        +-----------------------------------+
        | split_train_dev(pairs)            |
        | → train_pairs, dev_pairs          |
        +-----------------------------------+
                       |
                       v
        +-----------------------------------+
        | Construire dev_images, dev_labels |
        | ex: ["001_0.jpg","001_1.jpg", ...]|
        |     ["001","001", ...]            |
        +-----------------------------------+
                       |
                       v
        +-----------------------------------+
        | embed_paths(dev_images)           |
        | → dev_embeddings (vecteurs 512D)  |
        +-----------------------------------+
                       |
                       v
   +---------------------------------------------+
   | Évaluation 1 : pair_scores_dev              |
   | - construit paires positives/négatives      |
   | - calcule similarités cosinus               |
   | - produit y_true (0/1), y_score (scores)    |
   +---------------------------------------------+
                       |
                       v
   +---------------------------------------------+
   | ROC Curve, AUC, EER                         |
   | - AUC proche de 1 = bon modèle              |
   | - EER faible (<0.1) = bon modèle            |
   +---------------------------------------------+

                       +----------------+
                       |
                       v
   +---------------------------------------------+
   | Évaluation 2 : simulate_matching            |
   | - crée matrice de similarité S              |
   | - matching parfait (algo Hongrois)          |
   | - compare paires trouvées vs vérité terrain |
   | - calcule accuracy                          |
   +---------------------------------------------+
