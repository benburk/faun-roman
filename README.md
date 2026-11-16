# faun-roman

Roman numerals for [Faun](https://github.com/benburk/faun-lang): `to_roman`
writes a natural number as one, and `from_roman` reads one back.

```ruby
import roman {to_roman, from_roman}

expect to_roman(1994) == "MCMXCIV"
expect from_roman("MCMXCIV") == Ok(1994)
```

## Using it

Each release publishes a bundle, and its notes give the line to depend on
it, a URL naming the bundle by its hash:

```ruby
package {
  uses: {roman: "https://github.com/benburk/faun-roman/releases/download/v0.1.0/HASH.tar.zst"},
}
```

## Releasing

Push a tag, `v0.1.0`. The release workflow tests the library, bundles it
with `faun bundle`, and creates the tag's release with the bundle.
