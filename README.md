# Calculateur piscine au sel

Page web unique pour doser les produits d'une piscine au sel avec électrolyseur, selon le volume du bassin et les mesures du jour : pH, chlore libre, sel, stabilisant, anti-phosphates et TAC. Chaque mesure se saisit dans l'unité de la trousse d'analyse, et chaque résultat affiche le détail de son calcul.

En ligne : https://gharel.github.io/piscine/

## Utilisation

Ouvrez `index.html` dans un navigateur (en ligne ou en local, hors connexion). Saisissez le volume, puis vos mesures. Les saisies restent dans le navigateur (localStorage).

Un interrupteur « Mode avancé » en haut de la page choisit l'affichage :

- **Mode simple** (par défaut) : le volume et un formulaire court de six mesures (pH, chlore, sel, stabilisant, phosphates, TAC), avec l'unité au choix et la cible rappelée sous chacune, puis la liste des actions dans l'ordre de traitement (le TAC avant le pH). Les cibles et produits sont ceux du mode avancé, réglés par défaut sur les valeurs conseillées.
- **Mode avancé** : une carte par paramètre avec la température, les cibles, le choix et la concentration des produits, la production de l'électrolyseur, la dose de l'étiquette anti-phosphates, le tableau des valeurs recommandées, l'explication du TAC et le détail de chaque calcul.

## Valeurs recommandées

| Paramètre | À viser | Plage correcte |
|---|---|---|
| pH | 7,2 | 7,0 à 7,4 |
| Chlore libre | 2 mg/L | 1 à 3 mg/L, et au moins 5 % du stabilisant |
| Sel | 4 à 5 g/L (4 000 à 5 000 ppm) | selon la notice ; 1,5 à 2 g/L en basse salinité |
| Stabilisant | 30 à 40 mg/L | 20 à 50 mg/L |
| Phosphates | 0 ppb après traitement | moins de 100 ppb |
| TAC | 80 à 90 mg/L | 80 à 120 mg/L (8 à 12 °f) |

## Unités

Chaque mesure (sauf le pH) a un choix d'unité, celle affichée par la trousse d'analyse. Changer d'unité convertit la mesure et la cible ; les calculs se font en unité de base, et le détail du calcul montre la conversion.

| Paramètre | Unités proposées | Base des calculs |
|---|---|---|
| Chlore libre | mg/L, ppm (identiques) | mg/L |
| Sel | ppm (par défaut), g/L, ppt (‰), % | g/L : 1 g/L = 1 000 ppm = 1 ppt = 0,1 % |
| Stabilisant | mg/L, ppm (identiques) | mg/L |
| Phosphates | ppb, ppm, mg/L | ppb : 1 ppm = 1 mg/L = 1 000 ppb |
| TAC | mg/L, ppm, °f, °dH | mg/L de CaCO₃ : 1 °f = 10 mg/L, 1 °dH = 17,85 mg/L |

Les saisies enregistrées avant l'arrivée des unités sont relues dans leurs anciennes unités (sel en g/L).

## Calculs

V = volume en m³. 1 mg/L dans 1 m³ = 1 g ; 1 g/L dans 1 m³ = 1 kg.

| Paramètre | Calcul |
|---|---|
| TAC | Monter : bicarbonate de sodium, g = écart × 1,68 × V. Baisser : acide, mol = écart ÷ 50,04 × V, en plusieurs fois avec aération (le pH revient sans que le TAC remonte). |
| Sel | kg = (cible − mesure) × V, en sacs de 25 kg |
| Stabilisant (acide cyanurique 99 %) | g = (cible − mesure) × V ÷ 0,99 |
| Chlore libre | g de chlore actif = écart × V ; électrolyseur : heures = g ÷ production (g/h) ; choc : g ÷ teneur en chlore actif. Le dichlore ajoute 0,9 mg/L de stabilisant par mg/L de chlore. Minimum conseillé : 5 % du stabilisant. |
| pH | Modèle des carbonates : l'acide (ou le carbonate de sodium) nécessaire est la variation d'alcalinité des carbonates et du stabilisant entre le pH mesuré et le pH visé, à carbone total constant. Constantes corrigées selon la température (Plummer et Busenberg 1982) et la salinité (Davies). Produits : bisulfate de sodium, acide chlorhydrique, acide sulfurique ; carbonate de sodium pour le pH plus. |
| Anti-phosphates | mL = dose de l'étiquette × (V ÷ volume de l'étiquette) × (écart ÷ taux de l'étiquette). Par défaut 75 mL pour 10 m³ et 500 ppb. |
| Valeur trop haute | Part d'eau à renouveler = 1 − cible ÷ mesure |

Valeurs indicatives : la notice des produits et de l'électrolyseur prime.
