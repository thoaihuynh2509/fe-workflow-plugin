# Component Patterns

## Compound components
Use Context + provider for tightly-coupled sub-parts (Tabs, Accordion).
Always throw if hook used outside provider. Type the context value explicitly.

## Headless / custom hooks
`useToggle`, `useDisclosure` — share logic without prescribing UI. Return typed object.

## Data-fetching component
Hook owns the query. Component handles: loading → skeleton, error → message, empty → empty state, data → content. Never fetch in the component body.

## Forwarding refs
`React.forwardRef<HTMLInputElement, InputProps>`. Set `displayName`. Spread remaining props.

## Event handler typing
Form: `React.FormEvent<HTMLFormElement>` · Change: `React.ChangeEvent<HTMLInputElement>`
Click: `React.MouseEvent<HTMLButtonElement>` · Key: `React.KeyboardEvent<HTMLDivElement>`

## Props patterns
- Explicit `interface XProps` above component. Never infer from usage.
- Discriminated union for variant props: `type ButtonProps = PrimaryButton | GhostButton`
- Children: `React.ReactNode`. Render props: typed callback.
