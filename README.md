# mire v0.0.1

Standard library for the [Mire](https://mire-lang.org) programming language.

## Modules

| Module | Description |
|--------|-------------|
| `mire::vec` | Vector operations (push, get, set, len, sort, etc.) |
| `mire::map` | Map/dictionary operations (get, set, has, keys, values) |
| `mire::str` | String operations (len, upper, lower, split, join, etc.) |
| `mire::io` | I/O primitives (print, println, input) |

## Usage

```toml
# owl.toml
[dependencies]
mire = "0.0.1"
```

```mire
load mire

pub fn main: () {
    set v = [] :vec[i64] mut
    set v = mire::vec::push(v 42)
    set n = mire::vec::len(v)
    use dasu(n) // "1"

    set m = [] :map[str i64] mut
    set m = mire::map::set(m "key" 100)
    set val = mire::map::get_i64(m "key")
    use dasu(val) // "100"
}
```

## Design

- **One-word philosophy**: `mire::vec::push`, `mire::map::set`, `mire::str::len`
- **Independent package**: does not require kioto as a dependency
- **Thin wrappers**: each function wraps a single runtime C function (`rt_*`/`pal_*`)
- **No version()**: version is tracked in `owl.toml` and the lockfile

## Building

```bash
owl build
owl test
```

## License

Part of the Mire ecosystem. See the main project for license details.
