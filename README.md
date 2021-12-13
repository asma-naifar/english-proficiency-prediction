# 1 ére partie : explanation : regular expressions - used pattern for tags (BLOCK 1)

## generateCleanFile(filename)
Cette fonction permet de récupérer toutes les lignes qui se trouvent entre la balise "B" et de supprimer le retour à la ligne pour chaque fichier et génrer a la fin un seul fichier avec une seul ligne 
## generateCleanline(filename)
Cette fonction permet à chaque ligne de chaque fichier de supprimer toutes les balises et leurs données qui nous intérsesse pas grace à la fonction 'removeAllInternalTags' afin de génerer un fichier avec une ligne épurée 
## détails plus important (probléme que nous avons a recontré)
Tant que nous avons utilisé notre algorithme qui permet de se débarrasser de toutes les balises qui ne nous intéresse pas pour chaque ligne, nous avons trouvé un problème, c'est qu'il y a des balises qui sont ouvertes mais ne sont pas fermées dans la même ligne, donc c'est pourquoi nous avons pensé mettre tout le texte du fichier sur la même ligne

# 2 éme partie : Traitement du jeu de données Sac de mots (BoW)

    A bag-of-words is a representation of text that describes the occurrence of words within a document. It involves two things:

        A vocabulary of known words.
        A measure of the presence of known words.

    It is called a bag-of-words , because any information about the order or structure of words in the document is discarded. The model is only concerned with whether known words occur in the document, not where in the document. The complexity comes both in deciding how to design the vocabulary of known words (or tokens) and how to score the presence of known words.

## 2.1 Faire le lien entre les fichiers et leurs scores
## extractScore(filename)
Cette fonction permet de récupérer le score qui se trouve dans la balise "SST_level" pour chaque fichier

## 2.2 Créer du vocabulaire

## createVectorizer(filename)
Dans un premier temps, nous avons creé la fonction de génération du vocabulaire
## word_extraction(line)
Ensuite nous avons crée la fonction qui permert de supprimer les mots qui nous intéresse pas sur la phrase ...

## 2.3 Diviser notre base de données en ensembles d'entraînement et de test de manière aléatoire (60% entrainement et 40% test)

## 2.4 Créer sac de vocabulaire à partir de l'ensemble de données d'entraînement
Dans cette partie nous avons appliqué la méthode word_extraction pour chacun des fichiers d'entrainement et des test afin de génerer des fichiers propres (entrainement et test). Ensuite tokeniser et construire du vocabulaire à partir de la base d'entrainement et enfin encoder les fichiers et les convertir en un tableau

## 2.5 faire un dataframe qui est une structure de données permettant de stocker des données en deux dimensions : lignes et colonnes.
    - Nous avons crée dataframe pour les données d'entraînement (input) "x_train" qui ont comme lignes "nom de fichier" et les colonnes " vocabulaires", ensuite nous avons fait la méme choses pour (output) qui ont comme lignes "nom de fichier" et un seul colonne "Score"

    - Nous avons fait de même pour les données de test. on récupère même les données de test (output) afin de faire les comparer avec les (output) qu'on va prédire

# 3 éme partie : # Entraîner le classificateur pour prédire le score SST
    Dans cette partire, tout d'abord, nous avons utilisé différents classificateurs classiques pour prédire notre sortie.
## La classification naïve bayésienne
   un type de classification bayésienne probabiliste simple basée sur le théorème de Bayes avec une forte indépendance des hypothèses 
## La régression logistique 
   La régression logistique ou modèle logit est un modèle de régression binomiale. Comme pour tous les modèles de régression binomiale, il s'agit de modéliser au mieux un modèle mathématique simple à des observations réelles nombreuses
## eXtreme Gradient Boosting
   Le boosting est une alternative solide à l'ensachage. Au lieu d'agréger les prédictions, les boosters transforment les apprenants faibles en apprenants forts en se concentrant sur l'endroit où les modèles individuels (généralement les arbres de décision) ont mal tourné. Dans Gradient Boosting, les modèles individuels s'entraînent sur les résidus, la différence entre la prédiction et les résultats réels. Au lieu d'agréger les arbres, les arbres boostés par gradient apprennent des erreurs au cours de chaque tour de boost

Aprés nous avons remarqué que à chaque fois ça donne une prédiction différente par exemple la regression et svc
on peut dire que ce sont très proche avec une légère différence. Avec le XGBoost nous obtenons souvent une prédiction forte que les autres classifieurs

# 4 éme partie : la précision et Matrice de confusion 
Nous avons fait un résumé des résultats de prédictions sur un problème de classification sous la fomre matrice de confusion. Les prédictions correctes et incorrectes sont mises en lumière et réparties par classe

# 5 éme partie : Construction du réseau de neurones

Nous avons utilisé un modèle à 3 couches :
- premiere couche 32 neurone en utilisant la fonction "relu" et 
 comme taille des données d'entrée  --> la taille du vocabulaire

- Deuxième couche 16 neurones en utilisant la fonction "relu"

- la derniere couche 9 neurone  est de la même taille que nos données de sortie

# 6 éme partie : Word2vec
algorithme de word embedding Il a été développé par une équipe de recherche de Google, Word2Vec possède deux architectures neuronales, appelées CBOW et Skip-Gram.
- CBOW reçoit en entrée le contexte d’un mot, c’est à dire les termes qui l’entourent dans une phrase, et essaye de prédire le mot en question
- Skip-Gram fait exactement le contraire : elle prend en entrée un mot et essaye de prédire son contexte
