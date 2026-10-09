# Questions for the team: getting up to speed with React

Use these questions to learn how React is used in this project. The fastest
approach is to ask a teammate to walk through a real feature from the user
flow to the implementation and tests, then pair on a small change.

## Project shape

1. Can you walk me through a typical user flow and show me the React code
   behind it? Could we trace it from the route or page through components and
   data loading to the API?
2. Which React version and framework are we using, and what does the framework
   handle for us (such as routing, server rendering, data loading, or build
   tooling)?
3. How is the UI divided into pages, shared components, and feature-specific
   components? Where should new functionality go?

## State, data, and interactions

4. How do we decide whether state belongs in a component, is shared across
   components, or comes from the server? Could you show examples?
5. How do we fetch, cache, refresh, and handle errors for server data? Do we
   use a data-fetching library, framework features, or custom Hooks?
6. Which Hooks do we use most, and what are our conventions for custom Hooks?
   How do we handle effects, and what work should not go in `useEffect`?
7. How do we handle forms, validation, and submission states?

## Team practices

8. What does a good React test look like here, and what do we usually test?
   Could you show a component test and an end-to-end test?
9. How do styling, accessibility, and responsive behavior work in this
   project? What styling system and accessibility checks do we use?
10. What conventions should I follow when adding or changing a component?
    Ask about naming, file structure, exports, lint rules, and code review.

## Migration

11. How are we choosing what to migrate first, and how do we integrate React
    with the existing application?
12. What migration patterns or pitfalls have we already discovered? Which
    examples caused rework?
13. How do we verify a migrated feature behaves the same as before? Ask about
    acceptance criteria, automated tests, analytics, and rollout strategy.
14. Which parts of the migration are still undecided or risky? What
    assumptions, dependencies, or decisions might affect other teams?

## Practical learning exercise

Ask a teammate to pair on a small, real change. Before starting, ask them to
explain their approach; afterward, discuss the conventions and trade-offs to
remember. A code walkthrough followed by one small change is a focused way to
learn the project's practices.

## Findings and context so far

- The repository is intended to be a React knowledge wiki, not primarily an
  application project.
- The owner is a delivery manager working with four teams. One team is
  migrating to React, and that work is the main practical source for learning
  and applying the knowledge here.
- The owner worked with React about five years ago as a developer, with
  support from a more senior developer, and has a broad technical background.
  Treat this as a focused refresh and deepening of knowledge, not a beginner's
  introduction.
- The team uses function components rather than class components. This is
  known so far; the project's React version, framework, state/data patterns,
  testing approach, and migration strategy still need to be confirmed with
  the team.
- For fast project-specific learning, trace a real feature end-to-end and
  pair on a small change. This reveals the team's actual conventions and
  trade-offs more directly than learning React in the abstract.
