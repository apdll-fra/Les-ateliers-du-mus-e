# Explications — TP Git

## 1. Tests de la version finale

Les tests suivants ont été effectués sur la branche main.

| Étape/version testée | Action | Résultat attendu | Résultat constaté |
|---|---|---|---|
| Main finale | Ouvrir ou actualiser la page | Compteur à 0 et confirmation masquée | Compteur à 0, confirmation invisible. Test réussi. |
| Main finale | Cliquer une fois sur Réserver une place | Compteur à 1 et confirmation lisible avec le nom de l'atelier | Le message affiche « Fabriquez un objet inutile » et 1 place. Test réussi. |
| Main finale | Effectuer trois réservations au total | Compteur et confirmation à 3 places | Les deux indiquent 3 places. Test réussi. |
| Main finale | Cliquer sur Recommencer | Compteur à 0 et confirmation masquée | Le compteur revient à 0 et la confirmation disparaît. Test réussi. |
| Main finale | Réserver après remise à zéro | Compteur à 1 et confirmation visible | Le compteur repart à 1 et le message réapparaît. Test réussi. |
| Main finale | Tester l'affichage à 390 px | Texte et boutons lisibles sans défilement horizontal | Tout reste lisible, sans défilement horizontal. Test réussi. |

## 2. Problème rencontré et correction hotfix

**Avant le hotfix — commit 4412d07 :**

Après avoir fusionné les évolutions A et B, j'ai remarqué que le message de confirmation était presque invisible. Sa couleur était #17223b, identique à celle du fond de page. La fonctionnalité marchait, mais le texte n'était pas lisible.

**Après le hotfix — commit 2bf61d5 :**

J'ai créé la branche hotfix/lisibilite-confirmation depuis main. Dans style.css, j'ai remplacé la couleur du texte de confirmation par #ffffff. J'ai ensuite testé le site et vérifié que la confirmation était lisible tout en conservant son fonctionnement.

## 3. Questions Git

### Question 1 — Base et branches

Le point de départ commun des branches evolution-a et evolution-b est le commit "67aeb4f9f79876bb333c5589458647676896aea7", identifié par depart-cc.

J'ai utilisé "git rev-parse depart-cc" pour récupérer son identifiant, puis git branch -v pour vérifier que main, evolution-a et evolution-b etaient bien sur ce même commit avant les modifications.

La branche hotfix/lisibilite-confirmation a été créée depuis main après la fusion des deux évolutions, au commit 4412d07.

La quatrième branche, feature/nom-atelier-confirmation, a été créée depuis main après l'intégration du hotfix, au commit 2bf61d5.
(Ia utilisé pour retenir les commit)

### Question 2 — Fusion et fonctionnement

Une fusion Git réussi ne garanti pas le fonctionnement du site car des modification effectué par A peut ne pas prendre en compte le travail de B comme on l'a vu lorsqu'on a echanger les couleurs du fond et de la police, l'ajout de la confirmation n'a pas pris en compte l'échange de couleur car il n'utilisais pas la variable de couleur défini.

### Question 3 — Commit et publication

Après un commit local, il faut faire push pour envoyer les commits sur le dépôt distant GitHub.
Par exemple, j'ai créé le commit "d39b17a" pour ajouter le nom de l'atelier dans la confirmation. Ce commit a ensuite été intégré dans main et publié sur GitHub.
J'ai vérifié sa présence dans l'historique de la branche main sur GitHub.