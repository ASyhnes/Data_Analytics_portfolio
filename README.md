# Astuces et Mémos SQL

## Additionner une Somme d'Objets Nuls

Dans certaines situations, il peut être nécessaire de compter le nombre d'objets qui n'ont pas de valeur assignée (NULL) dans une base de données SQL. Par exemple, pour connaître le nombre d'objets invendus ou non attribués, on peut utiliser une requête SQL qui additionne une somme conditionnelle d'objets nuls.

### Exemple de Requête

Pour comptabiliser le nombre d'objets nuls dans une colonne spécifique, vous pouvez utiliser la requête SQL suivante :

```sql
SUM(CASE WHEN X.XXXXXX IS NULL THEN 1 ELSE 0 END) AS sommeDesObjetNULL

# Astuces et Mémos SQL

## Utilisation des Common Table Expressions (CTE) pour Simplifier les Requêtes Complexes

Les Common Table Expressions, ou CTEs, sont des constructions temporaires qui permettent de créer des requêtes temporaires nommées dans le cadre d'une requête SQL. Elles servent à décomposer les requêtes complexes en parties plus simples et réutilisables, améliorant ainsi la lisibilité et facilitant le débogage.

### Qu'est-ce qu'une CTE ?

Une CTE est essentiellement une vue temporaire que vous définissez au sein d'une requête SQL. Elle est particulièrement utile pour simplifier des requêtes complexes en les divisant en blocs logiques plus petits.

### Exemple d'Utilisation des CTE

Imaginons que vous souhaitez trouver les 10 produits les plus vendus. Au lieu d'écrire une requête directe complexe, vous pouvez utiliser une CTE pour rendre la requête plus claire :

```sql
WITH VentesParProduit AS (
    SELECT
        produit_id,
        SUM(quantite) AS total_vendu
    FROM ventes
    GROUP BY produit_id
)
SELECT p.nom, v.total_vendu
FROM VentesParProduit v
JOIN produits p ON v.produit_id = p.id
ORDER BY v.total_vendu DESC
LIMIT 10;

