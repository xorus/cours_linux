Administration Linux TP1
---
## 1/ Que fait ce script ?

Le script commence par une boucle (`while`, `do` ... `done`)
Le script commence par demander à l'utilisateur de choisir une entrée de menu. Il demande un chiffre.
Ensuite, le script passe ce chiffre dans un switch, (`case` ... `esac`). Chaque cas est indiqué par exemple par `1)` ... `;;`. `*)` correspond au choix par défaut si aucun autre choix n'est valable.

### Option 0 :

Fait exit pour arrêter l’exécution du script

### Option 1 : 

Utilise la commande `pwd` pour afficher le répertoire courant

### Option 2 :

Liste les fichiers du dossier courant en utilisant la commande `ls`

### Option 3 :

Affiche un message `Nom du fichier:` (avec `echo`)

Puis demande à l'utilisateur (via la commande `read`) une entrée. Cette entrée est sauvegardée dans la variable `file`.

On appelle ensuite la fonction `ls -l` (liste des fichiers détaillée) sur le fichier demandé (on donne la valeur de la variable `file` en argument de la commande)
L'option -n à echo permet de ne pas avoir de retour à la linge 

### Option 4 :

Affiche un message puis lit un nom de dossier puis fait un `cd` dans ce dernier

### Option 5 :

Affiche les n premières lignes d'un fichier, cette partie du script demande d'abord le nom de fichier puis le nombre de lignes. Elle appelle ensuite la commande `head` sur le fichier `file` en précisant en argument le nombre le lignes `-$n` (ex pour le fichier test et 5 lignes : `head -5 test`

## 2/ Parties de script à réaliser

### Option 6 : tri d'un fichier de nombres dans l'ordre décroissant

```bash
# en haut du script vers les entrées de menu
echo '[6] tri d''un fichier numérique dans l''ordre décroissant'

# plus bas dans le script, après le ;; correspondant au 5)
6) echo -n 'Nom du fichier:'; read file
sort -gr $file
;;
```

Contenu du fichier `nombres`

```
25
12
80
4290
50
33
```

Exécution :

![Résultat d’exécution](http://i.imgur.com/DAzvboe.png)

### Option 7: 

Concaténation de deux fichiers 

```bash
# en haut du script vers les entrées de menu
echo '[7] concaténation de deux fichiers'

# plus bas dans le script, après le ;; correspondant au 6)
7) echo -n 'Fichier 1:'; read fic1
echo -n 'Fichier 2:'; read fic2
cat $fic1 $fic2
;;
```

Contenu de `a.txt`

> bonjour

Contenu de `b.txt`

> le monde

Exécution :

![Exécution](http://i.imgur.com/L9YSzuZ.png)

### Option 8: nombre d’occurrences d'un mot dans un fichier

```bash
# dans le menu
echo '[8] nombres d''occurrences d''un mot dans un fichier'

# dans les choix
8) echo -n 'Fichier : '; read fic
echo -n 'Mot à chercher : '; read word
echo -n 'Nombre d''occurences trouvées : '
cat $fic | grep -oi $word | wc -l
;;
```

`-o` : affiche les mots matchés ligne par ligne

`-i` : insensible à la casse

Contenu de `lorem.txt`

> Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla malesuada tincidunt diam, non dictum risus molestie ut. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas id urna luctus, luctus mi eu, tristique ipsum. Curabitur laoreet mauris eget sem euismod maximus. Maecenas arcu odio, mattis eget est eget, sollicitudin sollicitudin tortor. Fusce eu orci nisl. Nullam sit amet nunc at mi molestie convallis eget in ex. Nunc tortor ipsum, pulvinar non cursus sed, ornare ac turpis. Donec egestas, magna non luctus maximus, sem enim sodales tellus, aliquam tempor leo elit sed leo. Nulla facilisi. Curabitur hendrerit nunc sed libero semper luctus. Vestibulum et maximus nulla. Curabitur quis quam et metus malesuada gravida nec at dui. In accumsan dolor et sapien consectetur, eget varius urna egestas.

Exécution :

![Exécution](http://i.imgur.com/4CTRGCl.png)


