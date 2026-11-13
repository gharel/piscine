# Calculateur piscine au sel

Page web unique pour doser les produits d'une piscine au sel avec électrolyseur, selon le volume du bassin et les mesures du jour : pH, stabilisant, sel, anti-phosphates et chlore libre. Chaque résultat affiche le détail de son calcul.

En ligne : https://gharel.github.io/piscine/

## Utilisation

Ouvrez `index.html` dans un navigateur (en ligne ou en local, hors connexion). Saisissez le volume, puis vos mesures. Les cibles sont pré-remplies et modifiables. Les saisies restent dans le navigateur (localStorage).

## Calculs

V = volume en m³. 1 mg/L dans 1 m³ = 1 g ; 1 g/L dans 1 m³ = 1 kg.

| Paramètre | Calcul |
|---|---|
| Sel | kg = (cible − mesure) × V, en sacs de 25 kg |
| Stabilisant (acide cyanurique 99 %) | g = (cible − mesure) × V ÷ 0,99 |
| Chlore libre | g de chlore actif = écart × V ; électrolyseur : heures = g ÷ production (g/h) ; choc : g ÷ teneur en chlore actif. Le dichlore ajoute 0,9 mg/L de stabilisant par mg/L de chlore. Minimum conseillé : 5 % du stabilisant. |
| pH | Modèle des carbonates : l'acide (ou le carbonate de sodium) nécessaire est la variation d'alcalinité des carbonates et du stabilisant entre le pH mesuré et le pH visé, à carbone total constant. Constantes corrigées selon la température (Plummer et Busenberg 1982) et la salinité (Davies). Produits : bisulfate de sodium, acide chlorhydrique, acide sulfurique ; carbonate de sodium pour le pH plus. |
| Anti-phosphates | mL = dose de l'étiquette × (V ÷ volume de l'étiquette) × (écart ÷ taux de l'étiquette). Par défaut 75 mL pour 10 m³ et 500 ppb. |
| Valeur trop haute | Part d'eau à renouveler = 1 − cible ÷ mesure |

Valeurs indicatives : la notice des produits et de l'électrolyseur prime.
