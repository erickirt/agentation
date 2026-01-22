# Agentation Package

This is the publishable npm package. Changes here affect everyone who installs `agentation`.

## Critical Rules

1. **NEVER run `npm publish`** - Only publish when explicitly instructed
2. **NEVER bump version** in package.json without explicit instruction
3. **NEVER modify exports** in index.ts without discussing breaking changes

## What Gets Published

- `dist/` folder (compiled from `src/`)
- `package.json`, `README.md`, `LICENSE`

## Before Modifying `src/`

- Consider: Is this a breaking change?
- Consider: Does this affect the API surface?
- Consider: Will existing users' code still work?

## Structure

```
src/
├── index.ts           # Main exports
├── types.ts           # TypeScript types (Annotation, etc.)
├── components/
│   ├── icons.tsx      # SVG icons with morph animations
│   ├── icons-css.tsx  # CSS-only icon variants
│   ├── annotation-popup/   # Popup for entering feedback
│   └── page-toolbar/       # Main floating toolbar
└── utils/
    ├── element-identification.ts  # Smart DOM element naming
    └── storage.ts                 # localStorage helpers
```

## Two Component Variants

1. **Agentation** (default) - Uses framer-motion for smooth animations
2. **AgentationCSS** - Zero runtime deps, CSS-only animations

## Testing Changes

1. Run `pnpm build` to ensure it compiles
2. Check the example app still works: `pnpm dev`
3. Verify no TypeScript errors in consumers

## Before v1 Release (see PLAN.md)

High priority:
- [ ] Convert SCSS to CSS-in-JS or CSS variables for easier adoption
- [ ] Add configuration props (theme, position, storage adapter)
- [ ] Abstract storage layer for custom implementations

Medium priority:
- [ ] Export TypeScript types properly
- [ ] Add position prop for toolbar placement

Low priority:
- [ ] Add tests
- [ ] Consider removing framer-motion dependency option
