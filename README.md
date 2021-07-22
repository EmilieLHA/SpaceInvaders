# Space Invaders

Un projet vraiment amusant. Je n'ai pas utilisé canva mais uniquement manipulé des éléments du DOM.

## Partie Html
La particularité de ce petit jeu est qu'il est presque à 100% en JS.
La page html/css ne sert qu'a créé une "grille" de 500px qui sera ensuite renseignée en JS. L'ensemble est stylisé en flexbox.

## Partie JS

### Création de la grille globale
Le principe est que chaque case de la grille est un div qui se génère en JS.
J'ai créé des div de 25px, j'ai donc sur la largeur de la grille 20 cases et je choisi d'en mettre 12 en hauteurs. J'ai donc 240 div à créer dans ma boucle.

Afin de permettre à mes aliens de "rebondir" quand ils touchent le bord du cadre, j'utilise un attribut de donnée: data-left et data-right pour les cases tout à fauche et tout à droite.

### Identification des cases Aliens
Je souhaite réaliser 3 lignes de 12 cases aliens. Je créé donc un tableau qui regroupe les index correspondants dans un tableau regroupant toutes les div créées au dessus.

J'ajoute ensuite à ces cases la *classe alien* pour leur mettre une image d'identification en fond.

De la même façon je positionne en bas de la grille le tireur grâve à la *classe tireur*


### Déplacement du tireur
Le principe est d'effacer le tireur en retirant la classe, de modifier sa position de 1 lorsque le joueur appuie sur la fleche et de redéfinir la classe sur la div correspondante.

### Fonction bouger les aliens

Je commence par la partie simple, ligne 119 du code. A la fréquence d'un invervale défini ligne 152, nous allons retirer la classe alien aux div en cours pour la remettre à une autre div défini en fonction de la direction.

Cette direction est fonction de la position actuelle du bloc alien.

#### Gestion du mouvement au bord
Si un alien touche le bord droit alors la direction est de 20 pour sauter 20 cases et permettre ainsi un saut de ligne. Idem si on est tout à gauche.
Il faut ensuite repartir en sens inverse en fonction du côté où on se trouve, on maîtrise cet aspect grâve à la variable booleenne descendreRight/Left.

On met ici un setTimeout pour permettre à la fonction de se terminer et à tous les aliens de sauter la ligne avant de partir en sens inverse. Sinon le bloc alien rebondirait à l'infini sans jamais descendre.

### Création du laser
Ligne 193, au moment où j'appuie sur la touche espace, je créé un intervale qui créé l'animation de déplacement du lazer, je "tire".
Toutes les 100ms, la div qui représente le lazer va partir de la position du tirer et sauter une ligne grâce -= width, jusqu'à rencontrer un alien.
On filtre ensuite le tableau allInvaders pour supprimer l'alien shooté.



