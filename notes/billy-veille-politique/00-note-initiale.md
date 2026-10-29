# Billy — Veille info : orientation politique de la couverture médiatique

> Noté le 29/10/2026 — à coder ce soir sur Billy.

## Objectif
Pour chaque information remontée par la veille, indiquer :
1. **Quels médias l'ont traitée** (gauche, centre, droite…).
2. **Le déséquilibre de couverture** : l'info a-t-elle été beaucoup plus reprise
   par la gauche ou par la droite ? (ou couverture équilibrée)
3. Repérer les **angles morts** : sujets traités presque uniquement d'un côté.

## Pistes de conception (à valider ce soir)
1. **Liste de médias classés** : un fichier (JSON) qui associe chaque média à
   une orientation, ex. `{ "liberation.fr": "gauche", "lefigaro.fr": "droite" }`.
   - Échelle à 5 niveaux : extrême gauche / gauche / centre / droite / extrême droite.
   - S'appuyer sur des classements existants et documenter la source
     (classement forcément discutable → le rendre modifiable).
2. **Regrouper les articles par sujet** : plusieurs articles = une même info
   (titres proches, mots-clés communs, même lien source).
3. **Calcul par info** :
   - nombre d'articles par orientation ;
   - pourcentage gauche / centre / droite ;
   - un indicateur : « Couverture équilibrée », « Surtout reprise à gauche »,
     « Surtout reprise à droite », « Angle mort gauche/droite ».
4. **Affichage** : une barre colorée gauche ↔ droite sous chaque info + la liste
   des médias qui l'ont traitée.

## Questions ouvertes
- Où Billy récupère-t-il les articles aujourd'hui (flux RSS, API, saisie manuelle) ?
- Quel seuil pour dire « beaucoup plus reprise » (ex. > 70 % d'un côté) ?
- Pondérer selon l'audience du média (un gros média compte plus) ou non ?
- Où est le code de Billy ? (absent des dépôts GitHub actuels)
