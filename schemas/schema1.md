   +-------------------+
   |  Fichier image    |   (ex: "data/train/0123_0.jpg")
   +-------------------+
              |
              v
   +-------------------+
   | cv2.imread(path)  |
   | (lecture image)   |
   +-------------------+
              |
              v
   +-------------------+
   | Conversion BGR→RGB|
   +-------------------+
              |
              v
   +-------------------+
   | app.get(img_rgb)  |
   | InsightFace       |
   | (détection visages|
   |  + embeddings)    |
   +-------------------+
              |
   +-----------------------------+
   | Plusieurs visages possibles |
   |   - bounding box            |
   |   - score de détection      |
   |   - embedding (vecteur 512) |
   +-----------------------------+
              |
              v
   +------------------------------------+
   | Sélection du visage le + probable  |
   |  f = max(faces, key=lambda score)  |
   +------------------------------------+
              |
              v
   +-----------------------------+
   | f.normed_embedding          |
   | Vecteur 512D, norme = 1     |
   | (empreinte du visage)       |
   +-----------------------------+
              |
              v
   +-------------------+
   | Résultat final :  |
   | np.ndarray(512,)  |
   | ex: [0.012, -0.03, ...] |
   +-------------------+
