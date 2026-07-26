# mire v0.0.3

Standard library for the [Mire](https://github.com/mire-lang) programming language.

## Modules

| Module | Description |
|--------|-------------|
| `mire::vec` | Vector operations (`push::i64`, `get`, `set`, `len`, `sort`, etc.) |
| `mire::map` | Map/dictionary operations (`get::i64`, `set::i64`, `has`, `keys`, `values`) |
| `mire::str` | String operations (`len`, `upper`, `lower`, `split`, `join`, etc.) |
| `mire::maybe` | Optional types (`some`, `none`, `unwrap`, `unwrap::or`, `map`, `and_then`) |
| `mire::result` | Result types (`ok`, `err`, `is`, `unwrap`, `unwrap::or`, `map`) |
| `mire::arr` | Fixed-size array operations (`new`, `get`, `set`, `len`) |

## Usage

```toml
# owl.toml
[dependencies]
mire = "0.0.3"
```

```mire
load mire

pub fn main: () {
    set v = [] :vec[i64] mut
    set v = mire::vec::push::i64(v 42)
    set n = mire::vec::len(v)
    use dasu(n) // "1"

    set m = [] :map[str i64] mut
    set m = mire::map::set::i64(m "key" 100)
    set val = mire::map::get::i64(m "key")
    use dasu(val) // "100"
}
```

## Design

- **Nested function grouping**: `push::i64`, `get::i64`, `set::i64` — type suffixes for polymorphic operations
- **Independent package**: does not require kioto as a dependency
- **Thin wrappers**: each function wraps a single runtime C function (`rt_*`)
- **No version()**: version is tracked in `owl.toml` and the lockfile

## Building

```bash
owl build
owl test
```

## License

Part of the Mire ecosystem. See the main project for license details.
