# Super-Resolution Using Simple CNNs (SRCNN)

Ce projet implémente un modèle SRCNN (Super-Resolution Convolutional Neural Network) pour améliorer la résolution des images basse résolution. La super-résolution est utilisée dans divers domaines comme l'imagerie médicale, la surveillance et le multimédia.

## Objectifs
1. Préparer des ensembles de données avec des images basse et haute résolution.
2. Entraîner un modèle SRCNN pour reconstruire des images haute résolution.
3. Évaluer les performances avec les métriques PSNR et SSIM.

## Méthodologie
### Datasets
- **Set5, Set14, DIV2K, BSD500, T91** : Utilisés pour l'entraînement, la validation et les tests.
- Les images basse résolution sont générées par interpolation bicubique à partir des versions haute résolution.

### Modèle SRCNN
- Architecture en 3 étapes :
  1. Extraction de caractéristiques (64 filtres, 9x9).
  2. Mappage non linéaire (32 filtres, 1x1).
  3. Reconstruction (1 filtre, 5x5).
- Optimisé avec l'algorithme Adam et une fonction de perte MSE.

### Entraînement
- Taux d'apprentissage initial : \(10^{-4}\), ajusté dynamiquement.
- Entraînement sur GPU pour accélérer le traitement.

### Évaluation
- **PSNR** : Qualité globale.
- **SSIM** : Similarité structurelle.

## Résultats
| Dataset  | PSNR (dB) | SSIM   |
|----------|-----------|--------|
| Set5     | 22.08     | 0.7414 |
| Set14    | 26.49     | 0.8255 |
| BSD500   | 12.05     | 0.0173 |
| T91      | 28.00     | 0.8454 |
| DIV2K    | 18.60     | 0.7501 |

## Conclusion
Le modèle SRCNN améliore significativement la qualité des images basse résolution. Cependant, les performances sur des datasets complexes restent limitées. Des explorations futures pourraient inclure des réseaux résiduels ou des techniques de régularisation.
