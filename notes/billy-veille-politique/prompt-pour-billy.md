# Prompt à coller dans la session Billy (ce soir, sur l'ordi)

D'abord, récupère les fichiers préparés :
```
git clone https://github.com/bonnevillearthur-dev/KARTER.git
cd KARTER && git checkout ccr-14f7eb97-571jcf
```
Les fichiers sont dans `notes/billy-veille-politique/`.

---

On ajoute un **second volet à la veille : la veille politique**, séparée de
la veille financière (on ne casse rien de l'existant).

Lis d'abord ces deux fichiers :
- `README.md` : le cahier des charges (indicateurs, seuils, affichage, inspiré
  de Ground News / Blindspot) ;
- `medias.json` : ~35 médias français avec orientation, propriétaire et
  catégorie de propriétaire.

Ensuite, avant de coder :
1. Montre-moi comment la veille financière récupère ses articles aujourd'hui.
2. Propose un plan pour la veille politique qui réutilise ce mécanisme.
3. Pose-moi les questions de la section 7 du README.

On code seulement une fois que j'ai validé le plan. Commence par une première
version simple : récolte RSS + % gauche/centre/droite par sujet.
