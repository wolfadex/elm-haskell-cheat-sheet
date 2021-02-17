## Elm <-> Haskell Cheat Sheet

### _and other tidbits_

A collection of operators and other things I forget when going between Elm and Haskell.

| Elm                                             | Haskell                           | Notes                                                                                |
| ----------------------------------------------- | --------------------------------- | ------------------------------------------------------------------------------------ |
| Type.map                                        | fmap _or_ <$>                     | modify the inner value                                                               |
| Type.andThen                                    | >>=                               | return a new `Type` from the inner value                                             |
| \x -> x / 2                                     | (/ 2)                             | The Elm version is a little more clear                                               |
| a :: rest                                       | a : rest                          | cons                                                                                 |
| func : a -> b                                   | func :: a -> b                    | func name and type separator                                                         |
| func : number -> number                         | func :: Number a => a -> a        | type classes                                                                         |
| <\|                                             | $                                 |                                                                                      |
| \|>                                             | &                                 |                                                                                      |
| <<                                              | .                                 |                                                                                      |
| >>                                              |                                   | nothing 😢                                                                           |
|                                                 |                                   |                                                                                      |
| ++                                              | <>                                |                                                                                      |
| Type.andMap                                     | <\*>                              | `andMap :: f (a -> b) -> f a -> f b`                                                 |
|                                                 | <\|>                              | Alternative aka `a <\|> b` aka `a or b`                                              |
| import My.Module as X exposing (func, Type(..)) | import My.Module as X             |                                                                                      |
|                                                 | import My.Module (func, Type(..)) |                                                                                      |
|                                                 | import qualified My.Module        | The default Haskell import is equivalent to `import My.Module exposing (..)` in Elm. |

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
