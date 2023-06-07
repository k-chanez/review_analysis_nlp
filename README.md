# review_analysis_nlp

[ Importation des bibliothèques nécessaires ]

re : pour les expressions régulières (utilisées pour le nettoyage des données).

numpy : pour les opérations mathématiques sur des tableaux multidimensionnels.

sklearn.metrics.confusion_matrix : pour calculer la matrice de confusion.

matplotlib.pyplot : pour tracer les graphiques.

tensorflow.keras.models.Sequential : pour créer un modèle de réseau de neurones séquentiel.

tensorflow.keras.layers : pour les différentes couches du modèle (Embedding, LSTM, Dense).

tensorflow.keras.preprocessing.text.Tokenizer : pour tokenizer les textes.

tensorflow.keras.preprocessing.sequence.pad_sequences : pour le padding des séquences.

nltk : pour le traitement du langage naturel.

pandas : pour la manipulation des données.

sklearn.model_selection.train_test_split : pour diviser les données en ensembles d'entraînement et de test.

tensorflow.keras.models.load_model : pour charger un modèle pré-entraîné.

sklearn.metrics.precision_score, sklearn.metrics.recall_score : pour calculer la précision et le rappel.

numpy.asarray, numpy.zeros : pour la manipulation des tableaux.

sklearn.metrics.f1_score : pour calculer le score F1.

Lecture du fichier CSV contenant les critiques de films à l'aide de pandas.

Vérification des valeurs nulles dans les données.

Affichage de la forme (shape) et des 10 premières lignes des données.


[pre-processing ]

1.Définition d'une fonction pour supprimer les balises HTML des textes.

2.Définition d'une fonction pour prétraiter le texte :

- Suppression des balises HTML à l'aide de la fonction définie précédemment.
- Suppression des ponctuations et des chiffres.
- Suppression des caractères isolés.
- Suppression des espaces multiples.
- Prétraitement des critiques de films en appliquant la fonction de prétraitement à chaque critique.

3.Conversion des étiquettes de sentiment de "positive" et "negative" en valeurs binaires (1 et 0).

4. Division des données en ensembles d'entraînement, de validation et de test (70%, 10%, 20% respectivement).

5. Création d'un tokenizer avec une limite de 5000 mots et ajustement sur les données d'entraînement.

6. Conversion des textes en séquences numériques à l'aide du tokenizer.

7. Ajout du padding aux séquences pour qu'elles aient toutes la même longueur.

8. Chargement des embeddings pré-entraînés (GloVe) à partir de fichier glove.2B et création d'une matrice d'embedding. disponibke sur  : https://www.kaggle.com/datasets/danielwillgeorge/glove6b100dtxt 

[Définition de l'architecture du modèle LSTM ]

- Ajout d'une couche d'embedding avec la matrice d'embedding pré-entraînée.
- Ajout de deux couches LSTM avec des dropout pour éviter le surapprentissage.
- Ajout d'une couche Dense de sortie avec une fonction d'activation sigmoïde.
- Compilation du modèle avec l'optimiseur Adam et la fonction de perte mean_squared_error.

- Entraînement du modèle sur les données d'entraînement avec une taille de batch de 140 et 16 epochs. Validation du modèle sur les données de validation.

- Évaluation des performances du modèle sur les données de test en calculant le score de perte et d'exactitude.

- Prédiction du modèle sur les données de test et calcul de la matrice de confusion et du score F1.

- Affichage des scores de test et d'exactitude, ainsi que des scores de validation et d'exactitude.

- Tracé des courbes d'exactitude et de perte du modèle pendant l'entraînement et la validation.

- Sauvegarde du modèle entraîné et chargement du modèle sauvegardé.

- Utilisation du modèle chargé pour prédire le sentiment de certaines critiques personnalisées.

- Prédiction du sentiment sur les données de test (X_test) à l'aide du modèle chargé et stockage des prédictions dans y_pred.

[ Prédiction d'un avis  personnalisé ]

- Application des fonctions de prétraitement sur l'avis négatif.
- Conversion de l'avis en séquence numérique à l'aide du tokenizer.
- Ajout du padding à la séquence.
- Prédiction du sentiment sur l'avis à l'aide du modèle chargé et stockage de la prédiction dans y_pred.

- Si la prédiction est inférieure à 0.5, attribution de la valeur 'avis négatif'. Sinon, attribution de la valeur 'avis positif'.
Affichage de la prédiction et de la valeur correspondante.

[ Dépendances ]

voir le script install.py afin de pouvoir importer les différentes librarires utilisés et bibliotheque 
