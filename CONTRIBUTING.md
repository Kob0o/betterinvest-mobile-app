# Contribuer à betterinvest-mobile-app

Les commits et le code sont en **anglais** (Conventional Commits). La documentation du dépôt est en français.

## Branches

- `main` — production
- `develop` — intégration
- `feat/*` ou `fix/*` — démarrent depuis `develop` (pas de préfixe `chore/` ; le type de commit `chore:` reste autorisé)
- `hotfix/*` — démarrent depuis `main`

## Fusion

| Flux | Méthode |
|---|---|
| `feat/*` / `fix/*` → `develop` | Squash merge |
| `develop` → `main` (release) | Merge commit (jamais squash ni rebase), puis tag `vX.Y.Z` sur `main` |
| `hotfix/*` → `main` | Merge commit + tag, puis immédiatement une PR `main` → `develop` en merge commit |

Les tags `vX.Y.Z` sont réservés à Enzo et Yanis.

Après merge, la branche source est **supprimée automatiquement**.

## Dependabot

- Mises à jour **mensuelles** ciblant `develop` (npm + GitHub Actions), groupées par type.
- Les PR **patch** et **minor** sont proposées en auto-merge (squash) lorsque la CI est verte.
- Les mises à jour **major** restent en revue manuelle.

## Release PR

À chaque push sur `develop`, un workflow maintient une PR ouverte `develop` → `main` (`Release: develop → main`). Elle n’est **jamais** auto-mergée : fusionner manuellement en merge commit, puis taguer.

## Pull requests

Une PR doit avoir :

- 1 approbation
- CI verte
- conversations résolues
- branche à jour avec la base

`git push --force-with-lease` est autorisé uniquement sur **votre** branche de travail, jamais sur `main` / `develop`.

## Checks locaux avant PR

```bash
npm run lint
npm run typecheck
npm test
npm run build
```
