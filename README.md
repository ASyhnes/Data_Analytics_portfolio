# Astuces et Mémos SQL

## Additionner une Somme d'Objets Nuls

Dans certaines situations, il peut être nécessaire de compter le nombre d'objets qui n'ont pas de valeur assignée (NULL) dans une base de données SQL. Par exemple, pour connaître le nombre d'objets invendus ou non attribués, on peut utiliser une requête SQL qui additionne une somme conditionnelle d'objets nuls.

### Exemple de Requête

Pour comptabiliser le nombre d'objets nuls dans une colonne spécifique, vous pouvez utiliser la requête SQL suivante :

```sql
SUM(CASE WHEN X.XXXXXX IS NULL THEN 1 ELSE 0 END) AS sommeDesObjetNULL
