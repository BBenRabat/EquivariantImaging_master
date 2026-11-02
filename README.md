# Mémoire de Fin d'Études : Self-Supervised Learning with Equivariant Imaging (EI) for Dynamic MRI Reconstruction Inverse Problem

Ce dépôt contient le rapport de mon mémoire de fin d'études de Master en Data Science (Heriot-Watt University), portant sur l'apprentissage auto-supervisé pour la reconstruction d'IRM dynamiques à partir de mesures sous-échantillonnées.

👉 [**Télécharger ou lire le mémoire complet (PDF)**](SSLEI.pdf)

## 🎯 Objectif du projet

Les méthodes actuelles de pointe en imagerie par résonance magnétique (IRM) reposent sur l'apprentissage supervisé, qui nécessite des données de référence (*ground-truth*) souvent longues et coûteuses à acquérir, ou sujettes à des artéfacts de mouvement. Ce projet a cherché à résoudre le problème inverse de la reconstruction d'IRM dynamiques de manière **entièrement auto-supervisée**, en s'affranchissant du besoin de données ground-truth grâce aux principes de l'imagerie équivariante (EI).

## 🛠️ Approche technique & Contribution

Mon travail s'est appuyé sur la bibliothèque open-source [**DeepInverse**](https://github.com) (PyTorch). Dans le cadre de ce mémoire, j'ai développé et intégré :

* **Extension 3D / Dynamique** : Adaptation des modèles unrollés Plug-and-Play (PnP-ADMM) avec des réseaux de neurones 3D (DnCNN) et mise en place d'une stratégie de découpage en patchs temporels pour s'affranchir des limitations mémoires GPU.

* **Nouvelle transformation temporelle** : Introduction d'une symétrie temporelle (retournement de séquence / *time-flip*) orthogonale aux plans spatiaux pour exploiter la consistance de l'imagerie dynamique.

* **Intégration de pertes robustes (REI & RUEI)** : Implémentation et évaluation de fonctions de pertes basées sur des estimateurs de type SURE pour gérer les bruits de mesure inconnus dans le domaine de Fourier (*k-space*).

## 📈 Résultats clés

* **Performance proche du supervisé** : Les modèles robustes auto-supervisés (REI/RUEI) atteignent des performances très proches des réseaux pleinement supervisés, avec un gain de plus de $7\text{ dB}$ par rapport à la rétroprojection linéaire basique.

* **Validation sur données cliniques** : Évaluation quantitative et qualitative sur le dataset d'imagerie cérébrale QTIM ($1202$ volumes NIfTI) avec simulation de masques d'accélération cartésiens et de bruits gaussiens à différents niveaux $\sigma$.

* **Démonstration de l'apport temporel** : Mise en évidence qu'intégrer la transformation de symétrie temporelle améliore systématiquement la reconstruction, en particulier aux niveaux de bruit faibles.

*(Optionnel : Insérez ici une belle image de vos résultats côte à côte)*
