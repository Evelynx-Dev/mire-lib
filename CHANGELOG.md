# Changelog

All notable changes to the mire standard library.

## [0.0.3] - 2026-07-26 (Maybe unwrap::or + Section Comments)

### Added

- **`mire::maybe`** — Added `unwrap::or::i64/str/f64/ptr` nested group for unwrap-with-default.
  All 4 C runtime functions (`rt_maybe_unwrap_or_*`) were already declared but had no
  public API. Added section comments for consistency with other modules.

### Changed

- Verified all 6 modules (vec, map, str, arr, result, maybe) compile and link correctly
  with nested function grouping. No parser bug exists — type keywords (`i64`, `str`, etc.)
  are tokenized as `Ident` by the lexer, so `is_member_name_token` handles them correctly.

## [0.0.2] - 2026-07-26 (Nested Function Grouping)

### Changed

All modules rewritten with the new nested function grouping syntax (`parent::child`
via `pub fn parent: () { pub fn child: ... }`). Every existing function is preserved.

- **`mire::map`** — `get::str/i64`, `set::str/i64`, `is::empty`, `values::i64` now
  use nested grouping. `len`, `has`, `keys`, `remove`, `entries`, `merge` remain standalone.
- **`mire::vec`** — `push::i64/str`, `pop::i64`, `get::i64/str`, `first::i64`, `last::i64`,
  `contains::i64`, `index::i64` now use nested grouping. `len`, `remove`, `clear`, `sort`,
  `reverse`, `unique`, `slice`, `flatten`, `concat`, `join` remain standalone.
- **`mire::arr`** — `first::i64`, `last::i64`, `contains::i64`, `index::i64`, `reverse::i64`
  now use nested grouping. `len`, `join` remain standalone.
- **`mire::str`** — `starts::with`, `ends::with`, `pad::left/right`, `from::i64/bool/f64`,
  `to::i64` now use nested grouping. Added `is::empty`. `replace` stays standalone with
  `replace::first` as flat 3-level.
- **`mire::result`** — `ok::i64/str/ptr`, `err::i64/str/ptr/payload`, `is::ok/err`,
  `unwrap::i64/str/f64/ptr/err::str` now use nested grouping. `unwrap::*::or` stays flat.
- **`mire::maybe`** — already migrated in previous commit.

### Added

- `str::is::empty` — returns true if string has zero length

### Removed

- `io` and `math` module exports from `owl.toml` (deprecated since v3.24.2)

## [0.0.1] - 2026-07-21

### Added

- `mire::vec` — vector operations: push, pop, get, remove, clear, concat, sort, reverse, contains, index, slice, flatten, unique, len
- `mire::map` — map/dict operations: get, set, has, keys, values, remove, merge, len
- `mire::str` — string operations: len, upper, lower, trim, replace, contains, starts_with, ends_with, split, join, substr, repeat, index, from_i64, to_i64
- `mire::maybe` — optional type: some, none, is_some, is_none, unwrap, unwrap_or, free
- `mire::result` — result type: ok, err, is_ok, is_err, unwrap, unwrap_or, free
- `mire::arr` — fixed-size array operations: len, first, last, contains, index_of, reverse, join
