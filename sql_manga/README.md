# enter dans mysql depuis une commande docker :

docker exec -it mysql_dev mysql -u root -proot tp_manga

# task_1

SELECT num_manga, titre, prix_base, annee FROM mangas ORDER BY titre;

# task_2

SELECT titre, annee, prix_base
FROM mangas
WHERE annee >= 2010
ORDER BY annee ASC;