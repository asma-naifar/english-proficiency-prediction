# English proficiency prediction

# Sujet 
Le but de cette tâche est de prédire la maîtrise de l'anglais d'une personne sur la base d'une saisie de texte.

Vous utiliserez le Corpus NTIC JLE disponible ici : https://alaginrc.nict.go.jp/nict_jle/index_E.html

La source des données du corpus est constituée des transcriptions des échantillons de discours enregistrés sur 1 281 participants (1,2 million de mots, 300 heures au total) du test d'entretien oral de compétence en anglais. Chaque participant a obtenu un score SST (Standard Speaking Test) entre 1 (faible compétence) et 9 (forte compétence) sur la base de ce test.

Vous allez construire un algorithme d'apprentissage automatique pour prédire le score SST de chaque participant en fonction de sa transcription (n'utilisez pas la transcription de l'intervieweur !)

Voici de l'aide pour réussir cette tâche :

Pré-traiter le jeu de données : extraire la transcription du participant (toutes les balises <B><B/>). Dans la transcription des participants, vous pouvez supprimer toutes les autres balises et extraire uniquement les mots anglais.
Traiter le jeu de données : extraire des caractéristiques avec la technique Bag of Word (BoW)
Former un classificateur pour prédire le score SST
Calculez la précision de votre système (le nombre de participants classés correctement) et tracez la matrice de confusion.
Essayez d'améliorer votre système (par exemple, vous pouvez essayer d'utiliser GloVe au lieu de BoW).
Votre objectif est de battre 60 % de précision !

#Clarification
