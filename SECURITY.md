# Politique de sécurité

Projet personnel, sans programme de bug bounty. Les signalements restent
néanmoins les bienvenus et sont traités au mieux des disponibilités.

## Signaler une vulnérabilité

**Ne pas ouvrir d'issue publique** pour un problème de sécurité.

- **Si l'onglet _Security → Report a vulnerability_ est disponible** sur le
  dépôt : l'utiliser (signalement privé, visible des seuls mainteneurs).
- **Sinon** (fonctionnalité indisponible selon le plan GitHub) : contacter
  directement le mainteneur [`@jbdev44`](https://github.com/jbdev44) via GitHub.

Merci d'inclure : composant concerné, version / commit, description, étapes de
reproduction, impact estimé.

## Périmètre

- **Concerné** : les services applicatifs `craftkit-*` de l'organisation.
- **Hors périmètre** : l'infrastructure d'hébergement personnelle (home-lab),
  les dépendances tierces (à signaler à leurs éditeurs).

## Traitement

Accusé de réception au mieux sous quelques jours. Correctif publié sur `main`
via `hotfix/*` une fois la faille confirmée. Pas de délai contractuel.
