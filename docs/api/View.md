# View

## Methods

### exclude()

Excludes entities with the given components from the view.

- **Type**

    ```lua
    function View:exclude<T...>(components: ...unknown): View<T...>
    ```

- **Details**

    Entities with *any* of the excluded components, will not be returned
    during iteration.

--------------------------------------------------------------------------------

### use()

Specifies a component to iterate along.

- **Type**

    ```lua
    function View:use<T...>(component: unknown): View<T...>
    ```

- **Details**

    Views, by default, iterate along the smallest pool within the given set of
    components. This function allows a specific pool to be iterated along
    instead.

--------------------------------------------------------------------------------

## Iteration

Views support generalized iteration.

```lua
for id: Entity, ...: T... in View<T...> do
```

The entity followed by the component values are returned.

Components can be added, changed and removed during iteration.
Components added during iteration are not returned for that iteration.

::: warning
During iteration, adding or removing components from entities not currently
being iterated can invalidate the iterator.
:::

## Length

Returns the amount of entities in the view.

```lua
#View<T...>: number
```

For single component views, this returns the exact amount of entities in the
view.

For multiple component views, this returns an estimated amount of entities.
This estimate will never be less than the actual amount of entities.
