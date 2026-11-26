# BetterInvest — application mobile

Projet personnel d’Enzo. BetterInvest est une application mobile éducative pour apprendre l’investissement long terme (approche gamifiée, style Duolingo).

Ce dépôt contient le client **Expo / React Native** (TypeScript).

**Plateforme prioritaire : Android (Play Store).** iOS reste configuré mais secondaire.

## Stack

D’après les dépendances du dépôt :

| Techno | Rôle |
|---|---|
| [Expo](https://docs.expo.dev/) SDK 58 | Framework et tooling (dev, lint, export, EAS) |
| React Native | UI native |
| TypeScript | Typage |
| [expo-router](https://docs.expo.dev/router/introduction/) | Navigation file-based (`src/app/`) |
| [NativeWind](https://www.nativewind.dev/) | Styles utilitaires (Tailwind CSS pour React Native) |

React Native Reusables n’est **pas** présent dans ce dépôt pour le moment.

## Prérequis

- Node.js 22 LTS (ou compatible avec Expo SDK 58)
- npm
- Compte Expo / EAS (uniquement pour les builds cloud, pas nécessaire pour le développement local)

## Installation

```bash
npm install
cp .env.example .env
```

## Variables d’environnement

Copier `.env.example` vers `.env`. Variables exposées côté client (préfixe `EXPO_PUBLIC_`) :

| Variable | Description |
|---|---|
| `EXPO_PUBLIC_API_URL` | URL de base de l’API (placeholder : `https://api.example.com`) |
| `EXPO_PUBLIC_EAS_PROJECT_ID` | ID du projet EAS (optionnel, après liaison Expo) |

Ne committez jamais de secrets réels dans `.env`.

## Lancement

```bash
npm start
```

Puis ouvrir l’app avec Expo Go ou un development build (`a` pour Android dans le terminal Expo).

| Commande | Description |
|---|---|
| `npm start` | Démarre le serveur de développement Expo |
| `npm run android` | Ouvre l’app sur Android |
| `npm run ios` | Ouvre l’app sur iOS (secondaire) |
| `npm run web` | Ouvre l’app sur le web |
| `npm run lint` | ESLint (config Expo) |
| `npm run typecheck` | Vérification TypeScript (`tsc --noEmit`) |
| `npm test` | Tests unitaires (Jest + Testing Library) |
| `npm run build` | Export du bundle (`expo export --platform android`) |

Checks locaux recommandés avant une PR (voir aussi [CONTRIBUTING.md](./CONTRIBUTING.md)) :

```bash
npm run lint
npm run typecheck
npm test
npm run build
```

## Structure

- `src/app/` — routes Expo Router
- `src/components/` — composants UI
- `eas.json` — profils EAS `development`, `preview`, `production`
- Identifiants : `com.betterinvest.app` (package Android et bundle id iOS)

## Conventions Git

Aligné sur [CONTRIBUTING.md](./CONTRIBUTING.md) :

- Branches longues : `main` (production) et `develop` (intégration)
- Travail : `feat/*` ou `fix/*` depuis `develop` (pas de préfixe `chore/` ; le type de commit `chore:` reste autorisé) → PR vers `develop` (squash merge)
- Release : `develop` → `main` en **merge commit**, puis tag `vX.Y.Z`
- Hotfix : `hotfix/*` depuis `main` → merge commit + tag, puis immédiatement une PR `main` → `develop` (merge commit)

Commits et code en anglais (Conventional Commits). Documentation du dépôt en français.

## Liens

- Application mobile (ce dépôt) : [Kob0o/betterinvest-mobile-app](https://github.com/Kob0o/betterinvest-mobile-app)
- API back-end : [Kob0o/betterinvest-back-end-api](https://github.com/Kob0o/betterinvest-back-end-api)
- Contribution : [CONTRIBUTING.md](./CONTRIBUTING.md)
- Sécurité : [SECURITY.md](./SECURITY.md)
- Docs Expo : [docs.expo.dev](https://docs.expo.dev/)
