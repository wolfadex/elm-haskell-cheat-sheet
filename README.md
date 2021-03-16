## Elm <-> Haskell Cheat Sheet

### _and other tidbits_

A collection of operators and other things I forget when going between Elm and Haskell.

| Elm                                             | Haskell                                     | Notes                                                                                |
| ----------------------------------------------- | ------------------------------------------- | -------------------------------------------------------------------------------------- |
| Type.map                                        | fmap _or_ <$>                               | modify the inner value                                                                  |
| Type.andThen                                    | >>=                                         | return a new `Type` from the inner value                                                |
| \x -> x / 2                                     | (/ 2)                                       | The Elm version is a little more clear                                                  |
| a :: rest                                       | a : rest                                    | cons                                                                                    |
| func : a -> b                                   | func :: a -> b                              | func name and type separator                                                            |
| func : number -> number                         | func :: Number a => a -> a                  | type classes                                                                            |
| <\|                                             | $                                           |                                                                                        |
| \|>                                             | &                                           |                                                                                        |
| <<                                              | .                                           |                                                                                        |
| >>                                              | .>                                          | requires the [flow](https://hackage.haskell.org/package/flow) package                |
|                                                 |                                             |                                                                                        |
| ++                                              | <>                                          |                                                                                        |
| Type.andMap                                     | <\*>                                        | `andMap :: f (a -> b) -> f a -> f b`                                                    |
|                                                 | <\|>                                        | Alternative aka `a <\|> b` aka `a or b`                                                |
| import My.Module as X exposing (func, Type(..)) | import My.Module as X                       |                                                                                        |
|                                                 | import My.Module (func, Type(..))           |                                                                                        |
|                                                 | import qualified My.Module                  | The default Haskell import is equivalent to `import My.Module exposing (..)` in Elm. |
| Tuple.pair                                      | (,)                                         |                                                                                        |
| ({ x, y } as point)                             | point@{x,y}.                                |                                                                                        |
| Maybe.withDefault                               | Data.Maybe.fromMaybe                        |                                                                                        |
| always                                          | const                                       |                                                                                        |
| { record \| field1 = value1, field2 = value2 }  | record { field1 = value1, field2 = value2 } |                                                                                        |
| record.field                                    | field record.                               |                                                                                        |
| .field record                                   |                                             | Elm also allows this syntax                                                            |

---

### Haskell:

Type class definition and implementation

```Haskell
-- Create a type class
class Eq a where
  (==) :: a -> a -> Bool

-- My custom type
data MyWrapper = MyWrapper String

-- Implementing `Eq` for my custom type
instance Eq MyType where
  (==) (MyWrapper a) (MyWrapper b) = a == b
```
