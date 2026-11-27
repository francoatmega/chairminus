# Contributing to Chairminus

Thanks for your interest in Chairminus! This guide explains how to pick something to work on, how we discuss changes, and how to send a pull request.

## Where to start

- The [roadmap (#1)](https://github.com/francoatmega/chairminus/issues/1) lists the planned features, each with its own issue.
- New to the project? Look for issues labeled [`good first issue`](https://github.com/francoatmega/chairminus/labels/good%20first%20issue).
- Ready-to-work issues with an agreed scope are labeled [`help wanted`](https://github.com/francoatmega/chairminus/labels/help%20wanted).
- Have a new idea? Open a [feature request](https://github.com/francoatmega/chairminus/issues/new/choose) and we'll discuss it there.

## How we work on an issue

1. **Comment on the issue** saying you'd like to work on it. For anything bigger than a small fix, describe your approach in a few lines.
2. **Wait to be assigned.** This avoids two people working on the same thing.
3. **Open a pull request** that references the issue (`Closes #N`).

Please don't open a pull request for an issue labeled `needs discussion` before the approach has been agreed in the issue. See below.

### Issues labeled `needs discussion`

These are features whose design or scope is not decided yet. The discussion happens in the issue's comments:

1. Read the issue, especially the **Open questions** section.
2. Comment with your proposal: how you'd implement it, which parts of the code it touches (`src/main`, `src/drivers`, `src/renderer`, `src/shared`…), and your answers to the open questions. For large features, a short design write-up (a few paragraphs, a rough API or a sketch) helps a lot.
3. A maintainer will reply. Once the approach is agreed, the issue's description is updated, `needs discussion` is replaced by `help wanted`, and the issue is assigned to you.
4. Then you can open the pull request. Splitting a large feature into smaller PRs is welcome.

## Labels

| Label | What it means | What to do |
|---|---|---|
| `good first issue` | Small, well-scoped task, good for newcomers | Comment to claim it, wait to be assigned, then open a PR |
| `help wanted` | Scope is agreed and contributions are welcome | Comment to claim it and open a PR referencing the issue |
| `needs discussion` | Design or scope is not agreed yet | Don't open a PR yet. Comment with your proposed approach (see above) |
| `enhancement` | New feature or improvement | — |
| `bug` | Something isn't working | Include steps to reproduce, OS, app version and database engine |
| `question` | More information is needed | Answer in the comments |
| `documentation` | Improvements or additions to documentation | — |
| `accessibility` | Barrier affecting people with disabilities | — |
| `duplicate` / `invalid` / `wontfix` | Won't be worked on | The issue is closed with a short explanation |

### Area labels

Area labels say which part of the app an issue affects, so you can filter by what you know:

| Label | Part of the app |
|---|---|
| `area: backup` | Backup and restore of databases |
| `area: connections` | Connections, drivers and grouping |
| `area: import-export` | Importing and exporting data and files |
| `area: migrations` | Schema changes and migration generation |
| `area: nosql` | MongoDB, Redis, Elasticsearch, OpenSearch and Neo4j |
| `area: performance` | Query plans, profiling and performance suggestions |
| `area: plugins` | Plugin system and plugins |
| `area: query-editor` | Query editor, execution and results |

## Setting up the project

You need Node.js 22 or newer.

```sh
npm install
npm start
```

The test databases (one for every engine except SQLite) are in `test/seeds`:

```sh
cd test/seeds
docker compose up -d
```

See the [README](README.md) for connection details, building the app and the project layout.

## Before opening a pull request

Run the checks:

```sh
npm test               # unit tests for the shared modules
npm run check:drivers  # every database driver loads inside Electron
npm run smoke          # opens the app against a scratch database
```

Then make sure that:

- the PR references its issue (`Closes #N`) and explains what changed and why;
- new logic in `src/shared` or the drivers has unit tests;
- UI changes include a screenshot or a short recording;
- the README is updated if you changed how something is used;
- the change works on the engines it touches, using the seeded test databases.

CI runs the unit tests and the interface build on every pull request.

## Reporting bugs and suggesting features

Use the [issue templates](https://github.com/francoatmega/chairminus/issues/new/choose). For security problems, please don't open a public issue. Contact the maintainer privately instead.

## License

By contributing, you agree that your contributions are licensed under the project's [license](LICENSE).
