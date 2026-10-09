# Project context

This repository is a personal React knowledge wiki. Use it to structure and
connect React knowledge, practical findings, and lessons learned during team
work—not as an application project by default.

## Owner context

- The owner is a delivery manager working with four teams.
- One team is migrating to React; that migration is the main practical source
  for learning and applying the knowledge captured here.
- The owner worked as a React developer about five years ago with support from
  a more senior developer and has a broad technical background.
- Treat the owner as an experienced technical professional refreshing and
  deepening React knowledge, not as a programming beginner.

## How to contribute

- Organize knowledge so it is useful both for personal learning and for
  decisions and discussions across the teams.
- Prioritize modern React practices, migration patterns and pitfalls,
  architecture and trade-offs, and reusable team guidance.
- Keep general React knowledge distinct from findings specific to the team's
  migration, and connect related topics where useful.
- When adding or updating knowledge, explain important reasoning and preserve
  useful examples, sources, and version context.
- Every Markdown page in `docs/react-fundamentals/` must be linked from
  `docs/react-fundamentals/README.md`. When adding a page there, update this
  local index in the same change. Each topic page in that folder must end with
  a `See also` section formatted as a bulleted list, including a link back to
  the local `README.md` index.
- Every new Markdown knowledge file must also be linked from the top-level
  `README.md`. Keep it organized as the wiki index, grouping links under clear
  topic headings and updating it in the same change that adds a file.
- Keep persistent project context and knowledge artifacts inside this
  repository; do not rely on or create external memory for this project.
