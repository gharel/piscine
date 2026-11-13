# Calculateur piscine au sel

Page web unique pour doser les produits d'une piscine au sel avec électrolyseur, selon le volume du bassin et les mesures du jour : TAC, pH, stabilisant, sel, anti-phosphates et chlore libre. Chaque résultat affiche le détail de son calcul.

En ligne : https://gharel.github.io/piscine/

## Utilisation

Ouvrez `index.html` dans un navigateur (en ligne ou en local, hors connexion). Saisissez le volume, puis vos mesures. Les saisies restent dans le navigateur (localStorage).

Deux versions, au choix en haut de la page :

- **Simple** : volume et mesures seulement. Les cibles et produits sont les valeurs conseillées, rappelées sous chaque mesure. Chaque carte donne la dose et le produit.
- **Avancée** : en plus, la température, les cibles, le choix et la concentration des produits, la production de l'électrolyseur, la dose de l'étiquette anti-phosphates, le tableau des valeurs recommandées et le détail de chaque calcul.

## Valeurs recommandées

| Paramètre | À viser | Plage correcte |
|---|---|---|
| TAC | 80 à 90 mg/L | 80 à 120 mg/L (8 à 12 °f) |
| pH | 7,2 | 7,0 à 7,4 |
| Stabilisant | 30 à 40 mg/L | 20 à 50 mg/L |
| Sel | 4 à 5 g/L | selon la notice ; 1,5 à 2 g/L en basse salinité |
| Phosphates | 0 ppb après traitement | moins de 100 ppb |
| Chlore libre | 2 mg/L | 1 à 3 mg/L, et au moins 5 % du stabilisant |

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
