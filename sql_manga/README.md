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

SELECT COUNT(*) AS nombre_total_de_mangas,  
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
INNER JOIN genres_manga AS g 
ON g.code_genre = m.code_genre
GROUP BY g.code_genre, g.signification
ORDER BY nombre_de_manga_par_genre DESC,g.code_genre ASC;  

# task_7
Calculer le montant de chaque facture.
Le montant d’une ligne se calcule ainsi : prix_base × coefficient du type de location.
Afficher le numéro de facture et le montant total.
Les noms des colonnes doivent correspondre exactement à ceux indiqués dans la section Résultat attendu (pensez à utiliser les bons alias).

SELECT l.num_facture,
SUM(m.prix_base * t.coefficient) AS depenses
FROM table_location AS l
INNER JOIN mangas AS m         
ON m.num_manga = l.num_manga
INNER JOIN types_location AS t 
ON t.code_type = l.code_type
GROUP BY l.num_facture
ORDER BY l.num_facture;

# task_8
Afficher le nombre de clients et le total d’enfants par ville.
Trier par ville.
Les noms des colonnes doivent correspondre exactement à ceux indiqués dans la section Résultat attendu (pensez à utiliser les bons alias).
Résultat attendu

SELECT ville,
COUNT(*) AS nombre_de_clients,
SUM(enfants) AS nombre_d_enfants 
FROM clients
GROUP BY ville
ORDER BY ville;

# task_9
Afficher les mangas avec leur mangaka.
Afficher le titre du manga, le prénom, le nom et le pays du mangaka.
Trier par titre de manga.

SELECT m.titre, k.prenom, k.nom, k.pays
FROM mangas AS m
INNER JOIN mangakas AS k 
ON k.code_mangaka = m.code_mangaka
ORDER BY m.titre;

# task_10
Afficher le détail des locations.
Afficher le numéro de facture, le client (nom et prenom), le manga (titre), le type de location (libelle) et la date de retour.

SELECT l.num_facture, c.prenom, c.nom, m.titre, t.libelle, l.date_retour
FROM table_location AS l
INNER JOIN factures AS f 
ON f.num_facture = l.num_facture  
INNER JOIN clients AS c 
ON c.code_client = f.code_client  
INNER JOIN mangas AS m   
ON m.num_manga = l.num_manga
INNER JOIN types_location AS t 
ON t.code_type = l.code_type
ORDER BY c.code_client, l.num_facture, l.num_manga;

# task_11
Afficher les 5 clients ayant généré le plus de chiffre d’affaires.
Afficher le code client, le prénom, le nom, le nombre de locations et le total dépensé par client.

SELECT c.code_client, c.prenom, c.nom,
COUNT(*) AS nombre_de_location,
ROUND(SUM(m.prix_base * t.coefficient), 2) AS total_depenses
FROM table_location AS l
INNER JOIN factures AS f
ON f.num_facture = l.num_facture 
INNER JOIN clients AS c
ON c.code_client = f.code_client
INNER JOIN mangas AS m ON m.num_manga = l.num_manga 
INNER JOIN types_location t ON t.code_type = l.code_type 
GROUP BY c.code_client, c.prenom, c.nom
ORDER BY total_depenses DESC
LIMIT 5;

# task_12

# task_13

# task_14

# task_15

# task_16

# task_17

# task_18

# task_19

# task_20
