# TP CI/CD — pipeline GitHub Actions

[![CI](https://github.com/AlexRovere/github-actions-ci-tp/actions/workflows/ci.yml/badge.svg)](https://github.com/AlexRovere/github-actions-ci-tp/actions/workflows/ci.yml)

TP du cours CI/CD : mettre en place l'intégration continue d'une petite API Node.js fournie par le formateur ([coaxial/cicd-tp](https://github.com/coaxial/cicd-tp)).

**Ma contribution** : le workflow [`.github/workflows/ci.yml`](.github/workflows/ci.yml) et les tests, construits par pull requests successives.

- Déclenchement sur push et pull request vers `master`, ou à la demande
- Version de Node lue depuis `.nvmrc`, installation reproductible avec `npm ci` et cache npm
- Tests Jest (unitaires, intégration, end-to-end), dont des tests unitaires et d'intégration ajoutés au projet fourni, puis lint ESLint
- Résultats JUnit publiés directement sur la pull request (`dorny/test-reporter`)
- Rapport Allure généré à chaque run, et résultats conservés 7 jours en artefacts
---

## L'application

A Node.js application providing a simple greeting service with a REST API. It includes a server built with Express, greeting logic, and comprehensive test
suites (unit, integration, and end-to-end).

## Features

- **Greeting Functionality**: Generates personalized greetings via `src/greeting.js`.
- **REST API Server**: Built with Express in `src/server.js`, supporting GET and POST endpoints for greetings.
- **Testing**: Full test coverage with Jest:
  - Unit tests in `tests/unit/greeting.test.js`.
  - Integration tests in `tests/integration/app.test.js`.
  - End-to-end tests in `tests/e2e/e2e.test.js`.
- **Linting**: Configured with ESLint (via `.eslintrc.js` and `.eslintignore`).
- **Node.js Version Management**: Uses `.nvmrc` to specify Node.js v22.19.0.

## Prerequisites

- Node.js ≥22.19.0 (use `.nvmrc` with nvm: `nvm use`).
- npm (included with Node.js).

## Installation

1. Fork the repository:
2. Install dependencies:

```
npm install
```

## Usage

Start the server:

```
npm start
```

The server runs on port 3000 (or `process.env.PORT`). Endpoints:

- `GET /hello/:name?`: Returns a greeting (e.g., "Hello world!" or "Hello world! From [name]").
- `POST /hello`: Expects `x-name` header for the name.

## Testing

Run tests with Jest:

- All tests: `npm test`
- Unit tests: `npm test -- tests/unit/`
- Integration tests: `npm test -- tests/integration/`
- E2E tests: `npm test -- tests/e2e/`

## Linting

Check code quality:

```
npm run lint
```

## Project Structure

- `src/greeting.js`: Core greeting logic.
- `src/server.js`: Express server setup.
- `tests/`: Test suites (unit, integration, e2e).
- `.eslintrc.js`: ESLint configuration.
- `.eslintignore`: Files/directories excluded from linting.
- `.nvmrc`: Node.js version specification.
- `package.json`: Project metadata, dependencies, and scripts.

## Dependencies

- **Runtime**: Express (web server), Axios (HTTP client), Supertest (testing utility).
- **Dev**: ESLint (linting), Jest (testing).

## Contributing

1. Fork the repo.
2. Create a feature branch.
3. Run tests and linting.
4. Submit a pull request.
