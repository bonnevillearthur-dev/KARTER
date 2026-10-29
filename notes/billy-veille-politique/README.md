# Billy — Volet 2 : veille politique (cahier des charges)

> Préparé le 29/10/2026. À coder sur Billy, en **second volet**, à côté de la
> veille financière existante (qu'on ne touche pas).

## 1. L'idée en une phrase
Pour chaque info politique, montrer **qui la diffuse** (orientation et
propriétaire des médias) et **avec quelle insistance**, pour lire l'info en
fonction de qui la pousse.

Modèle : **Ground News** (fonction « Blindspot »). C'est sans doute le site
auquel tu pensais : il n'existe pas de « Blindpost ».

## 2. Ce que Ground News fait (et qu'on reprend)
| Élément | Chez Ground News | Chez Billy |
|---|---|---|
| Orientation des médias | Moyenne de 3 notateurs externes (AllSides, Ad Fontes, Media Bias/Fact Check), échelle à 7 niveaux | Notre fichier `medias.json`, échelle à 7 niveaux, modifiable |
| Note par article | L'article hérite de l'orientation de son média (l'article n'est pas analysé lui-même) | Pareil : simple et honnête |
| Répartition | Barre gauche / centre / droite en % | Pareil |
| Blindspot | Info couverte de façon très déséquilibrée par un camp | « Angle mort » : >= 70 % d'un camp (seuil réglable) |
| Propriété | Catégorie du propriétaire (indépendant, milliardaire, État, groupe…) | Propriétaire nommé + catégorie |

## 3. Fiche d'une info (ce que Billy affiche)
```
Titre de l'info
[██████ gauche 55 % | ███ centre 25 % | ██ droite 20 %]   12 articles
Étiquette : « Surtout reprise à gauche »
Propriétaires : Milliardaires 40 % · État 25 % · Indépendants 20 % · Groupes 15 %
Insistance : 3 unes / 12 articles · 1er article : Mediapart, 08h12
Médias : Libération, Mediapart, Le Monde, franceinfo, Le Figaro…
```

## 4. Les indicateurs
1. **Nombre d'articles par camp** : gauche (extrême gauche + gauche + centre
   gauche), centre, droite (centre droit + droite + extrême droite).
2. **% par camp** et étiquette :
   - >= 70 % d'un camp → « Angle mort de la gauche » / « … de la droite »
     (le camp opposé n'en parle presque pas) ;
   - 55–70 % → « Surtout reprise à gauche / à droite » ;
   - sinon → « Couverture équilibrée ».
3. **Répartition par type de propriétaire** (catégories de `medias.json`).
4. **Insistance** (« l'importance qu'ils lui donnent ») :
   - nombre d'articles par média sur le sujet ;
   - présence en une / dans le flux principal (si la source le permet) ;
   - durée : nombre de jours où le sujet reste couvert.
5. **Qui a sorti l'info en premier** (média et heure du 1er article).

## 5. Étapes techniques (dans l'ordre)
1. **Récolte** : flux RSS des médias de `medias.json` (le champ `rss` est à
   compléter / vérifier). Repartir de ce que fait déjà la veille financière.
2. **Rattachement au média** : nom de domaine de l'article → fiche du média.
3. **Regroupement par sujet** : mots-clés communs + titres proches (au début :
   similarité de titres ; plus tard : demander à Claude de regrouper).
4. **Calcul** des indicateurs de la section 4.
5. **Affichage** : un onglet « Veille politique » séparé de la veille financière.

## 6. Points de vigilance
- **Les classements gauche/droite sont subjectifs.** Afficher la méthode et
  rendre `medias.json` modifiable. Ne jamais présenter ça comme une vérité.
- **La propriété des médias change souvent** (rachats). Les fiches marquées
  `"a_verifier": true` doivent être vérifiées avant mise en service. Sources
  utiles : la carte « Médias français : qui possède quoi ? » du Monde
  diplomatique / Acrimed, les mentions légales de chaque site.
- Le nombre d'articles dépend de la taille du média : un gros média publie
  plus. À terme, envisager de compter **1 média = 1 voix** en plus du compte
  brut.

## 7. Questions à trancher avec Billy
1. Comment la veille financière récupère-t-elle ses articles aujourd'hui ?
2. Seuils 55 % / 70 % : ok ?
3. Compte brut, 1 média = 1 voix, ou les deux ?
4. Fréquence de mise à jour (toutes les heures ? matin et soir ?).
