# loXiv

A comprehensive archive of linguistics olympiads — problems, solutions, and grading schemes from IOL, NACLO, APLO, UKLO, and many more international, regional, and national competitions.

This project is forked from [phoxiv](https://phoxiv.org), adapted for linguistics olympiad archives.

## Development

```bash
# Install dependencies
bun install

# Run development server
bun run dev

# Build for production
bun run build
```

## Adding more competitions

The archive data lives in `static/contests/`. Each competition is one folder, and each year is a subfolder with one year YAML.

### Directory structure

Use this shape:

```text
static/contests/
  <contest-id>/
    index.yaml
    2026/
      2026.yaml
      <pdf files...>
    2025/
      2025.yaml
      <pdf files...>
```

Rules:
- `contest-id` should be lowercase and stable (e.g. `naclo`, `iol`, `uklo`).
- Year folders must be 4-digit years (`2024`, `2025`, ...).
- The year YAML filename must match the folder name exactly (`2025/2025.yaml`).
- PDF paths referenced in YAML should use `/competitions/<contest-id>/<year>/<file>.pdf`.

### `index.yaml` format (competition metadata)

Keep keys in this order for consistency:

```yaml
id: naclo
name: North American Computational Linguistics Olympiad
shortName: NACLO
website: "https://naclo.org/"
summary: Regional olympiad across North America focused on computational linguistics puzzles.
icon: "🌎"
tag: Regional
url: "https://naclo.org/"
desc: |
  Short multi-line description of the contest, history, and scope.
```

Required keys used by the app:
- `id`, `name`, `shortName`, `website`
- `summary`, `icon`, `tag`, `url`, `desc`

Allowed `tag` values:
- `International`
- `Regional`
- `National`
- `Open`

### Year YAML format (`<year>/<year>.yaml`)

Full example:

```yaml
name: "2026 Linguistics Olympiad"
location: "Virtual & In-Person"
link: "https://example.org/2026"
problemsLink: "https://example.org/2026/problems"

papers:
  - examDuration: 180
    gradingScheme: "/pdfs/2026_universal_grading.pdf"

  - category: "Round 1"
    link: "/pdfs/2026_r1_problems.pdf"
    solutionLink: "/pdfs/2026_r1_solutions.pdf"
    # Overrides the base template duration of 180
    examDuration: 240
    # Total contestants is strictly known
    n: 450
    camp: 85.5

    scores:
      - [99.5, 98.2, 95.0, 91.1, 88.0] # Row 1: Always TOTAL Scores
      - [20.0, 19.5, 15.0, 10.0, 10.0] # Row 2: Problem 1 Scores
      - [20.0, 20.0, 18.0, 15.0, 12.0] # Row 3: Problem 2 Scores

  - category: "N" 
    link: "/pdfs/2026_n_problems.pdf"
    # We don't know the total number of participants for this category,
    # so we use a tilde (~) to explicitly tell the system it is null/unknown.
    n: ~
    gold: 92.0
    silver: 80.0
    scores:
      - [98.0, 95.0, 92.0, 89.0, 80.0]
      - [20.0, 18.0, 15.0, 12.0, 10.0]

problems:
  - id: "lo-2026-1"
    number: "1"
    name: "Deciphering Linear A"
    category: "Round 1"
    author: "Jane Doe"
    maxScore: 20
    link: "https://example.org/p1"
    solutionLink: "https://example.org/s1"

  - id: "lo-2026-2"
    number: "2"
    name: "Austronesian Alignment"
    category: "Round 1"
    author: "John Smith"

  - id: "lo-2026-3"
    number: "3"
    name: "The Syntax of Category N"
    category: "N"
    maxScore: 15
```

Notes:
- The first `papers` item without `category` acts as a base template for all categories.
- In `scores`, row 1 should be total scores; subsequent rows are per-problem scores in order.
- Use `n: ~` when participant count is unknown/incomplete.

### After adding or editing data

Regenerate derived data:

```bash
bun run pregen
```

Then start the app:

```bash
bun run dev
```

## Contributing

Want to add problems or help maintain the site? Open a PR.

## License

MIT
