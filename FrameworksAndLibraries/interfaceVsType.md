# [Interface vs Type](https://medium.com/@martin_hotell/interface-vs-type-alias-in-typescript-2-7-2a8f1777af4c)

type aliases can act sort of like interfaces, however, there are some subtle differences.

``` ts
interface PointInterface {
  x: number;
  y: number;
}

type = PointType {
  x: number;
  y: number;  
}
```

## Misconceptions

> “One difference is, that interfaces create a new name that is used everywhere. Type aliases don’t create a new name — for instance, error messages won’t use the alias name.”

&#10071; Same error reference for both type alias and interface

> “A second more important difference is that type aliases cannot be extended or implemented from”

&#10071; We can extend an interface with type alias or use type alias for implementing a Class constraint. We can also combine both type alias and interface for implementing a Class constraint

> “type aliases cannot extend/implement other types”

&#10071; You can use interface or any other TypeScript valid type(which has shape of an Dictionary/JS Object, so non primitive types etc…) for type alias extension via intersection operator &

## Differences

1. you cannot use implements on an class with type alias if you use union operator within your type definition
2. you cannot use extends on an interface with type alias if you use union operator within your type definition
3. declaration merging doesn’t work with type alias

## What should I use?

- use what you want ( type alias / interface ) just be consistent
- always use interface for public API's definition when authoring a library or 3rd party ambient type definitions
- consider using type for your React Component Props and State