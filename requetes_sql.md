# Requêtes SQL

## Requêtes portant sur la base de donnée des résistats allemands au nazisme 


Cette requête permet d'avoir toutes les personnes dont le nom contient "Fried". C'est le WHERE qui permet de faire cette sélection, pour n'avoir que les personnes, dont le nom contient "Fried". 

    SELECT p.name
    FROM person p
    WHERE name LIKE '%Fried%';

Cette seconde requête permet de selectionner les personnes qui ont une date de naissance et un lieu de naissance. Les "--" permettent de mettre des commentaires, qui ne font pas partie de la requête. Il me sont utiles, afin de me souvenir à quoi servent quelles commandes. 

    SELECT p.name, b.date, gp.name
    FROM person p, birth b, geographical_place gp
    --on met un WHERE de jointure pour avoir que la bonne date 
    WHERE p.fk_birth=b.pk_birth
    -- AND est une condition de jointure 
    AND b.fk_geographical_place=gp.pk_geographical_place


Cette requête-ci permet également de mettre en lien les personnes avec leur date de naissance et leur lieu de naissance, mais cette fois-ci, en gardant tout de même les lignes dont l'information n'est pas complète (où il manque par exemple le lieu de naissance). 

    SELECT p.name, b.date, gp.name
    FROM person p left join birth b ON p.fk_birth=b.pk_birth
    LEFT JOIN geographical_place gp ON b.fk_geographical_place=gp.pk_geographical_place;