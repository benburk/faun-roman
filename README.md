# roman

Roman numerals for [Faun](https://github.com/faun-lang/faun), from `I`
to `MMMCMXCIX`: 1 to 3,999.

```ruby
import roman {RomanNumeral}

expect RomanNumeral.from_nat(16).map_ok(|numeral| numeral.to_str()) == Ok("XVI")
expect RomanNumeral.from_str("xlii").map_ok(|numeral| numeral.to_nat()) == Ok(42)
expect RomanNumeral.from_nat(4000) == Err(OutOfRange)
expect RomanNumeral.from_str("IIII") == Err(Malformed)
```

## Using it

Each [release](https://github.com/faun-lang/roman/releases)'s notes give
the line to add to your package's `uses`.

## Releasing

Push a version tag. The release workflow tests the library, bundles it,
and publishes the bundle on the tag's release.

## License

[Zero-Clause BSD](LICENSE).
