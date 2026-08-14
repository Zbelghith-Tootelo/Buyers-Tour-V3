# Buyers Tour — Prototype "Tour de visites" Immocontact

Prototype cliquable du flow **Tour de visites** pour Immocontact / Touchbase Real Estate.
Données mockées, aucune dépendance — HTML/CSS/JS statique.

## Aperçu du flow

1. **Liste des tours** (à venir / passés, recherche)
2. **Contact acheteur** — recherche dans les contacts ou création d'une fiche
3. **Construction du tour** — date/heure, ajout de destinations (Nom / Adresse / #MLS / Cart MLS Matrix / Arrêt / Pause), réordonnancement par glisser-déposer, statuts de confirmation, temps de trajet estimés et alertes de conflit
4. **Optimisation & carte** — aperçu du tour et des trajets possibles
5. **Envoi des demandes de visites** aux courtiers inscripteurs

Version responsive incluse (maquettes mobiles 430px) : menu en grille, barre de navigation retour/titre/menu.

## Lancer en local

```bash
node server.js
# ouvre http://localhost:5190
```

ou n'importe quel serveur statique à la racine du projet.

## Structure

- `index.html` — coquille de l'app (sidebar, headers desktop/mobile)
- `css/styles.css` — design tokens Immocontact + styles
- `js/app.js` — écrans, état, données mockées
- `assets/` — logo, icônes et images exportées du Figma officiel

Design source : fichier Figma *Immocontact* (page Tour de visites).
