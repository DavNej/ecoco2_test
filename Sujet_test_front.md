A faire en VueJS.

Le but du projet est d'afficher une liste de sources de news (Le monde, AFP, etc) à partir d'une API gratuite.
L'utilisateur peut choisir une source de news parmi la liste, et une sélection de news venant de cette source s'affiche ensuite.

Il faut d'abord se créer une clé d'api sur le site newsapi.org

Etape 1 - Récupérer les sources :
doc:  https://newsapi.org/docs/endpoints/sources

Afficher un formulaire avec un sélecteur pour afficher la liste des sources (nom).


Etape 2 - Afficher les news d'une source:
doc : https://newsapi.org/docs/endpoints/top-headlines
Lorsqu'on clique sur un élément, on affiche en dessous une liste de news avec le titre, l'image, le contenu, et un lien pour accéder à la news complète.
La liste de news s'affiche sous la forme d'une grille qui s'adapte à la taille de l'écran.

Etape 3 - Style des news :
Afficher les news dans des "card" (à la material design), faire ressortir visuellement le titre, améliorer le style graphique pour rendre l'ensemble plus présentable.

Etape 4 - Bonus :
Filtrer le résultat pour n'afficher que les 10 premiers éléments dans le select des sources.
Pour chacun de ces éléments, afficher dans le nom le nombre de news dispo pour cette source (par exemple: reuters - 2 news)
