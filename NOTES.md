# Nettoyage de plans DXF

Outil web autonome (un seul fichier `index.html`, aucune installation). Il lit des plans DXF cadastraux et recale les éléments par rapport à la limite rouge.

## Fonctionnement
1. Déposer des fichiers `.dxf` ou un dossier : le plan s'affiche tel quel (colonne « Avant »), rien n'est modifié.
2. Régler les types à traiter, puis cliquer sur **Nettoyer**.
3. Contrôler la colonne « Après », puis télécharger le plan ou le ZIP de tous les plans.

## Règles
- Limite rouge = polyline fermée de couleur 1 ou de layer `parcelle` / `limit` (la plus grande).
- Bornes (blocs INSERT, layer ou bloc contenant « born ») posées sur la limite rouge ET sur une seguia, un sentier ou un chemin : ramenées au centre (milieu entre les deux rives, ou sur l'axe si une seule ligne). Le sommet de la limite rouge suit la borne.
- Seguia, sentier, chemin, piste, oued, chaaba (détectés par le nom du layer) : coupés à N mètres au-delà de la limite rouge (N réglable par type).
- Le reste du fichier DXF n'est pas modifié.

## Limites connues
- Lignes (LINE) et polylines légères (LWPOLYLINE) seulement ; les arcs/bulges sont ignorés.
- Les textes ne sont pas dessinés dans l'aperçu (ils restent intacts dans le fichier).

## Fichier de test
`P2923-PLAN.dxf` (parcelle 2923, Agoudim, échelle 1/200).

## À faire
- Tester sur des plans avec sentier et chemin.
- Vérifier le cas « chemin public L.V » et « chemin de 3 m » (layers à confirmer).
