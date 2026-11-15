# Contribuer

Projet personnel de l'organisation `craftkit44`. Ces règles valent pour tous les
dépôts `craftkit-*`. Ce fichier est la valeur **par défaut** de l'organisation :
un dépôt qui a son propre `CONTRIBUTING.md` (ou son propre modèle de branches,
comme `ZenPractice` ou `j3b-starters`) prime.

## Modèle de branches

| Branche | Rôle |
|---|---|
| `main` | État déployé / déployable. N'avance **que** par PR mergée. |
| `develop` | Intégration continue. Cible par défaut des PR. |
| `feature/*`, `fix/*`, `chore/*` | Travail en cours, branchées depuis `develop`, PR vers `develop`. |
| `hotfix/*` | Correctif urgent, branché **directement depuis `main`**, PR vers `main` puis report sur `develop`. |

Seules `develop` et `hotfix/*` (issue directement de `main`, sans commit
spécifique à `develop`) peuvent être mergées dans `main`. Les workflows
`main-guard` / `develop-guard` le vérifient et ouvrent une issue en cas d'écart
(pas de branch protection : dépôts privés en plan GitHub free).

## Avant d'ouvrir une PR

- La branche cible est `develop` (ou `main` pour un `hotfix/*`).
- Les tests passent en local.
- Aucun secret, credential, `.env` ou clé n'est commité.
- La documentation impactée est à jour.
- Pour une montée de version : la version Maven / `package.json` est incrémentée
  (elle sert de tag d'image et de release).

## Tests — conventions communes

Structure **GIVEN / WHEN / THEN** obligatoire, un test = un seul comportement,
descriptions en français, code en anglais. Les tests sont de la documentation
vivante : la lisibilité prime.

### Java (JUnit 5 + Mockito)

- `@DisplayName` obligatoire, en français : `"nomDeLaMethode : ce qui doit se passer"`.
- Nom de méthode en anglais, préfixé : `nomDeLaMethode_should...`.
- `@ExtendWith(MockitoExtension.class)`, `@Mock`, `@InjectMocks`.
- Préférer `assertEquals(expected, actual)` à `assertTrue` / `assertFalse`.
- `./mvnw -B verify` (Maven) ou `npm test` (Angular) avant de pousser, selon le dépôt.

### TypeScript / Angular (Jest + Testing Library)

- `describe()` par fonctionnalité, `it()` / `test()` avec descriptions complètes en français.
- Requêtes centrées utilisateur : `getByRole()`, `getByLabelText()`, `getByText()` —
  pas de `getByTestId()` en première intention.
- Isolation via `jest.spyOn()` / `jest.mock()`.

## Commits

Messages à l'impératif, en français, une intention par commit. Historique
linéaire (rebase plutôt que merge sur les branches de travail).
