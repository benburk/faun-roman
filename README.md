# faun-roman

Roman numerals for [Faun](https://github.com/benburk/faun-lang), from `I`
to `MMMCMXCIX`: 1 to 3,999.

```ruby
import roman {RomanNumeral}

expect RomanNumeral.new(16).map_ok(|numeral| numeral.to_str()) == Ok("XVI")
expect RomanNumeral.parse("xlii").map_ok(|numeral| numeral.value()) == Ok(42)
expect RomanNumeral.new(4000) == Err(OutOfRange)
expect RomanNumeral.parse("IIII") == Err(InvalidRomanNumeral)
```

After [AA-Turner/roman-numerals](https://github.com/AA-Turner/roman-numerals).

## Using it

Each [release](https://github.com/benburk/faun-roman/releases)'s notes give
the line to add to your package's `uses`.

## Releasing

Push a version tag. The release workflow tests the library, bundles it,
and publishes the bundle on the tag's release.

## License

[Zero-Clause BSD](LICENSE).
