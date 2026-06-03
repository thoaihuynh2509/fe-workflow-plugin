# TypeScript Patterns

## Discriminated unions (API state, action types)
`type Result<T> = { status: 'idle' } | { status: 'loading' } | { status: 'success'; data: T } | { status: 'error'; error: Error }`
Switch on `status` — TS narrows automatically.

## Branded types (prevent ID mix-ups)
`type Brand<T, B extends string> = T & { readonly __brand: B }`
`type UserId = Brand<string, 'UserId'>` — now distinct from `OrderId`.

## Type guards
`function isApiError(v: unknown): v is ApiError` — check shape with `typeof` + `in`.

## Utility types
`PartialBy<T, K>` = Omit<T,K> & Partial<Pick<T,K>>
`RequiredBy<T, K>` = Omit<T,K> & Required<Pick<T,K>>
`DeepReadonly<T>` = recursive readonly mapped type.

## Exhaustive switch
`function assertNever(v: never): never` in default case — compile error if case missing.

## Mapped types for handlers
`type Handlers<E extends string> = { [K in E as \`on${Capitalize<K>}\`]: () => void }`
