# component-contract

> A Claude Code skill that requires a written component contract before any UI implementation begins.

![Claude Code](https://img.shields.io/badge/Claude_Code-skill-blue)
![License](https://img.shields.io/badge/license-MIT-green)

---

## The Problem

Claude builds components without defining their API first.

Props get added ad-hoc. States get forgotten. Accessibility is an afterthought. The mobile layout breaks because it was never planned. The result: brittle components that need rewrites when requirements clarify.

---

## Before / After

**Without component-contract**
```
[Claude builds Button]
You: can it have a loading state?
[Claude rewrites it]
You: does it work with keyboard navigation?
[Claude retrofits ARIA, restructures JSX]
You: what about mobile?
[Claude scatters responsive styles through the file]
```

**With component-contract**
```
// Contract: Button
// Props: label(string), onClick(fn), variant(primary|secondary|ghost),
//        size(sm|md|lg), disabled(bool), loading(bool)
// States: default | hover | active | disabled | loading
// Accessibility: role="button", Enter/Space, contrast AA
// Responsive: full-width <640px, auto-width md+

[implementation starts only after this is confirmed]
```

---

## Install

```bash
mkdir -p ~/.claude/skills/component-contract
curl -o ~/.claude/skills/component-contract/SKILL.md \
  https://raw.githubusercontent.com/Feli2arias/component-contract/main/SKILL.md
/component-contract
```

---

## What It Enforces

| Rule | Why |
|------|-----|
| Write the full contract before any implementation | Surfaces requirements early |
| All states: default, hover, disabled, loading, error, empty | No forgotten states |
| Accessibility in the contract: ARIA, keyboard, contrast | a11y from day one |
| Responsive behavior per breakpoint | No mobile afterthoughts |
| No implementation until contract is confirmed | Hard gate |

---

## What It Doesn't Change

Visual quality and implementation correctness are never compromised.

---

## License

MIT
