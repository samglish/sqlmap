# sqlmap
Tester si l’URL est vulnérable (avec un paramètre GET)
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

