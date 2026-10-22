# UI/UX design resources and implementation references

These are the GitHub links collected in the previous handoff brief; audit each for licensing, relevance, and compatibility before importing assets. The user also requested an Apple/OpenAI/Craft-quality experience, not a copy of a screenshot.

## GitHub repos

1. UI UX Pro Max Skill — https://github.com/nextlevelbuilder/ui-ux-pro-max-skill
2. Awesome Design MD — https://github.com/VoltAgent/awesome-design-md
3. Open Design — https://github.com/nexu-io/open-design
4. Taste Skill — https://github.com/Leonxlnx/taste-skill
5. Impeccable — https://github.com/pbakaus/impeccable
6. React Bits — https://github.com/DavidHDev/react-bits
7. Emil Kowalski Skills — https://github.com/emilkowalski/skills
8. Hallmark — https://github.com/Nutlope/hallmark
9. GSAP Skills — https://github.com/greensock/gsap-skills
10. Canvas UI — https://github.com/DavidHDev/canvas-ui

## Additional inspiration

- https://www.details.so/
- https://refero.design/
- https://designspells.com/
- https://www.craft.do/
- https://linear.app/
- ChatGPT app workspace and OpenAI UI principles

## Requested setup

Codex MCP configuration is checked into `.codex/config.toml`:

```toml
[mcp_servers.shadcn]
command = "npx"
args = ["shadcn@latest", "mcp"]
```

Requested (run **inside Codex development environment**, after the relevant React/shadcn app is initialized and permissions/network are available):

```bash
npx shadcn@latest add @canvas-ui/liquid-react
```

Try the component in a non-document surface only if accessibility and performance tests show value. Do not use it as a reason to add ornamentation.

## Concrete design standards

- Use restrained neutral backgrounds, subtle separators, one predictable primary action.
- 16px-ish default body type at desktop; supporting text >=13–14px where space allows.
- Modern sans-serif (e.g., Geist, Inter, DM Sans), proper readable weights, generous line height.
- Page hierarchy: batch/file list | document viewer | matching MDR row and differences.
- Selected fields and actions should be apparent without onboarding; keyboard navigable.
- Show only actionable mismatches by default, reveal secondary metadata on demand.
- Avoid decorative shadows, gradients, frosted glass, tab proliferation and dozens of equal-priority controls.
- Test at 1280px laptop, 1440px desktop and narrower widths; preserve a usable document preview.
