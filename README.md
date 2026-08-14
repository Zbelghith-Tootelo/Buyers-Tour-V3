# Buyers Tour V3 — Prototype « Tour de visites » Immocontact

Prototype cliquable du flow **Tour de visites** pour Immocontact / Touchbase Real Estate.
Données fictives, aucune dépendance — HTML/CSS/JS statique.

L'historique complet est conservé : la V2 reste accessible au tag [`v2`](../../releases/tag/v2).

## Le modèle

Le tour n'a pas de champ `status` : il se déduit de ce qui est vrai. Un seul champ
porte le régime d'un arrêt — `sentAt`.

| `sentAt` | Régime | Ce que le courtier peut faire |
|---|---|---|
| absent | **Bac à sable** | Composer librement, glisser-déposer, aucun statut affiché |
| posé | **Engagé** | L'heure est un engagement : elle ne se change que par « Modifier la visite », ce qui renvoie une demande de validation |

Statuts d'un arrêt : `sandbox · pending · confirmed · proposed · refused · cancelled · noreply`
Statuts d'un tour, tous dérivés : `brouillon · en_cours · confirme · non_envoye · partage`

## Le flow

1. **Liste** — à venir / passés, rangés par date. Un tour daté d'hier bascule seul dans « Passé », et se ramène d'un bouton.
2. **Nommer l'acheteur** — dès le bac à sable, pour que deux brouillons ne se ressemblent pas. Le courriel n'est exigé qu'à l'envoi.
3. **Composer** — propriétés du catalogue, hors catalogue, arrêts libres, pauses. Réordonnancement par glisser-déposer tant que rien n'est parti.
4. **Optimiser** — depuis le point de départ du courtier, pas depuis la première propriété.
5. **Envoyer** — chaque demande peut partir seule, ou en lot avec sélection des propriétés.
6. **Traiter les réponses** — confirmation, contre-proposition, refus, annulation après confirmation, absence de réponse à 48 h. Chacune a sa sortie sous l'arrêt concerné.
7. **Partager à l'acheteur** — une fois les visites confirmées. Le tour signale s'il n'est plus à jour depuis l'envoi.
8. **Jour J** — marquer visité, rédiger le compte rendu, l'envoyer ou le garder de côté.

## Lancer en local

```bash
node server.js
```

Puis <http://localhost:5290>. Ou n'importe quel serveur statique à la racine.

## Structure

- `index.html` — coquille de l'app (sidebar, bandeaux desktop et mobile)
- `css/styles.css` — jetons de design Immocontact et styles
- `js/app.js` — écrans, état, données fictives
- `assets/` — logos, icônes et images exportés du Figma officiel

Le prototype porte les deux marques : l'interrupteur **Flags** bascule entre
Immocontact et Touchbase, logotype compris.

## Accessibilité

Vérifié à chaque livraison, sur liste, tour, carte et compte rendu :

- contrastes WCAG AA sur tout texte affiché, calculés nœud par nœud ;
- cibles tactiles ≥ 24 px (WCAG 2.5.8), hors attribution Leaflet imposée par sa licence ;
- tout élément interactif porte un nom accessible, tout champ un libellé lié ;
- modales : `role="dialog"`, focus piégé et restitué, fermeture par ESC ou par le fond ;
- `prefers-reduced-motion` respecté globalement ;
- pas de débordement horizontal jusqu'à 320 px.

Reste ouvert : le réordonnancement n'a pas encore d'équivalent clavier ni tactile
(WCAG 2.1.1 et 2.5.7) — le glisser-déposer HTML5 n'existe pas sur navigateur mobile.

Design source : fichier Figma *Immocontact*, page Tour de visites.
