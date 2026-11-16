# faun-roman

Roman numerals for [Faun](https://github.com/benburk/faun-lang), from `I`
to `MMMCMXCIX`: 1 to 3,999. A `RomanNumeral` holds only a number a numeral
can write, so one made is always valid.

```ruby
import roman {RomanNumeral}

expect RomanNumeral.new(16).map_ok(|numeral| numeral.to_str()) == Ok("XVI")
expect RomanNumeral.new(16).map_ok(|numeral| numeral.to_lower()) == Ok("xvi")
expect RomanNumeral.parse("xlii").map_ok(|numeral| numeral.value()) == Ok(42)
expect RomanNumeral.new(4000) == Err(OutOfRange)
expect RomanNumeral.parse("IIII") == Err(InvalidRomanNumeral)
```

- `RomanNumeral.new(n)` makes the numeral for `n`, or `Err(OutOfRange)`
  outside 1 to 3,999. Classical numerals have no zero, and write a letter at
  most three times running.
- `RomanNumeral.parse(text)` reads a numeral in capitals or small letters,
  all one case, written the one way `new` writes it, or answers
  `Err(InvalidRomanNumeral)`.
- `numeral.to_str()` writes it in capitals, as `"${numeral}"` does, and
  `numeral.to_lower()` in small letters. `numeral.value()` is its number.
- `RomanNumeral.min` and `RomanNumeral.max` are `I` and `MMMCMXCIX`.

The design follows
[AA-Turner/roman-numerals](https://github.com/AA-Turner/roman-numerals).

## Using it

Each release publishes a bundle, and its notes give the line to depend on
it, a URL naming the bundle by its hash:

```ruby
package {
  uses: {roman: "https://github.com/benburk/faun-roman/releases/download/v0.2.0/HASH.tar.zst"},
}
```

## Releasing

Push a tag, `v0.2.0`. The release workflow tests the library, bundles it
with `faun bundle`, and creates the tag's release with the bundle. Every
workflow builds `faun` from the faun-lang commit pinned in
`.github/actions/faun/action.yml`, so releases bundle alike; moving to a
newer compiler is changing that commit.

## License

[Zero-Clause BSD](LICENSE): use it for anything, with no attribution
required. Each release's bundle carries the license with it.
