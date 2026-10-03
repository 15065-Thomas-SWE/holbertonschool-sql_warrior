# enter dans mysql depuis une commande docker :

docker exec -it mysql_dev mysql -u root -proot tp_manga

# task_1
Afficher tous les mangas avec leur numéro, leur titre, leur prix de base et leur année.
Trier les résultats par titre.

SELECT num_manga, titre, prix_base, annee FROM mangas ORDER BY titre;

# task_2
Afficher les mangas sortis à partir de 2010.
Afficher uniquement le titre, l’année et le prix de base.
Trier les mangas par annee dans un ordre ascendant.

SELECT titre, annee, prix_base
FROM mangas
WHERE annee >= 2010
ORDER BY annee ASC;

# task_3
Afficher les clients habitant à Lyon ou à Bordeaux.
Afficher le prénom, le nom et la ville.

SELECT prenom, nom, ville
FROM clients
WHERE ville = 'Lyon' 
OR ville = 'Bordeaux';

# task_4
Afficher les mangas dont le titre contient « Tome 1 ».
Affiche uniquement le num_manga et le titre.
Trier les résultats par num_manga.

SELECT num_manga, titre
FROM mangas
WHERE titre LIKE '%Tome 1%'
ORDER BY num_manga;

# task_5
Calculer le nombre total de mangas, le prix moyen et le prix maximum.
Arrondir le prix moyen à 2 décimales.
Utilisez des alias afin d’obtenir les mêmes intitulés de colonnes que ceux affichés dans la section Résultat attendu.

-- Statistiques globales sur les mangas
SELECT
    COUNT(*) AS nombre_total_de_mangas,  
    ROUND(AVG(prix_base), 2) AS prix_moyen, 
    MAX(prix_base) AS prix_max 
FROM mangas;

# task_6
Compter le nombre de mangas par genre.
Afficher le genre ainsi que le nombre de mangas correspondants.
Trier les résultats du genre le plus représenté au moins représenté.
Les noms des colonnes doivent correspondre exactement à ceux indiqués dans la section Résultat attendu (pensez à utiliser les bons alias).

SELECT g.signification AS genre,
COUNT(*) AS nombre_de_manga_par_genre
FROM mangas AS m
JOIN genres_manga AS g 
ON g.code_genre = m.code_genre
GROUP BY g.code_genre, g.signification
ORDER BY nombre_de_manga_par_genre DESC,g.code_genre ASC;  

# task_7

# task_8

# task_9

# task_10

# task_11

# task_12

# task_13

# task_14

# task_15

# task_16

# task_17

# task_18

# task_19

# task_20
