# Typescript

TypeScript Tutorial for beginners: [https://ts.chibicode.com/todo/](https://ts.chibicode.com/todo/)

Declare a type:

```tsx
type Event = {
  title: string
  id: number
}
```

This type can have readonly properties, that prevents object from mutation:

```tsx
type Event = {
  readonly title: string
  readonly id: number
}
```

Or immutability could be added to all properties with mapped type:

```tsx
type Event = Readonly<{
  title: string
  id: number
}>
```

Other mapped types: `Required<...>`, `Partial<...>`

Array types:

```tsx
function iterateThroughEvents(events: Event[]){
}
```

Array itself is not readonly in this case. To prevent from pushing into array, we can add `readonly` to argument type definitions:

```tsx
function interateThroughEvents(events: readonly Event[]){
}
```

Literal types are types with exact values:

```tsx
type EventNotification = {
  eventId: number
  opened: true
}
```

Intersection types:

```tsx
type withTitle = {
  title: string
}

type withId = {
  id: number
}

type event = withId & withTitle
// is equal to
type event = {
  title: string
  id: number
}
```

Second type overrides the first in intersection type:

```tsx
type withOpened = {
  opened: true
}

type notification = {
  opened: boolean
}

type openedNotification = notification & withOpened
// is equal to
type openedNotification {
  opened: true
}
```

It helps with code duplication:

```tsx
type notification = Readonly<{
  eventId: number
  opened: boolean
}>

type openedNotification = notification & {
  readonly opened: true
}
```

Union types:

```tsx
type Foo = number | string | { custom: string }
```

Optional properties:

```tsx
type event = {
  alarm?: Alarm
}
```
