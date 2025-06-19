# Analysis, ie. Prior Art

Let’s begin with an analysis:

* What formatting implementations currently exist across major programming languages or applications?
* What common principles or patterns do they share?
* Should we adopt an existing standard, or is there a justified need to create a new one?

## Programming Languages

List of string and type formatting implementations.

| Language         | Formatting Style(s)                             | Example Syntax                              |
| ---------------- | ----------------------------------------------- | ------------------------------------------- |
| **Python**       | `str.format()`, f-strings (`f""`), `%` operator | `f"Value: {x:.2f}"`                         |
| **JavaScript**   | Template literals, manual formatting            | `` `Value: ${x.toFixed(2)}` ``              |
| **Java**         | `String.format()`, `Formatter`, printf-style    | `String.format("Value: %.2f", x)`           |
| **C**            | `printf`, `sprintf`                             | `printf("Value: %.2f", x);`                 |
| **C++**          | `printf`, C++20 `std::format`, `ostringstream`  | `std::format("Value: {:.2f}", x)`           |
| **C#**           | Interpolation (`$""`), `String.Format()`        | `$"Value: {x:F2}"`                          |
| **Go**           | `fmt.Sprintf`, `fmt.Printf`                     | `fmt.Sprintf("Value: %.2f", x)`             |
| **Rust**         | `format!`, `println!` macros with formatting    | `format!("Value: {:.2}", x)`                |
| **Kotlin**       | Interpolation, `String.format()`                | `"Value: %.2f".format(x)`                   |
| **Swift**        | Interpolation, `String(format:)`                | `String(format: "Value: %.2f", x)`          |
| **TypeScript**   | Same as JavaScript                              | `` `Value: ${x.toFixed(2)}` ``              |
| **PHP**          | Interpolation, `sprintf()`, `printf()`          | `sprintf("Value: %.2f", $x)`                |
| **Ruby**         | `sprintf`, interpolation, `.format`             | `"Value: %.2f" % x`                         |
| **Shell (Bash)** | `printf`, variable substitution                 | `printf "%.2f\n" $x`                        |
| **R**            | `sprintf`, `format`, paste                      | `sprintf("Value: %.2f", x)`                 |
| **MATLAB**       | `sprintf`, `fprintf`                            | `sprintf('Value: %.2f', x)`                 |
| **Perl**         | `sprintf`, interpolation                        | `sprintf("Value: %.2f", $x)`                |
| **Lua**          | `string.format()`                               | `string.format("Value: %.2f", x)`           |
| **Pascal**       | `WriteLn`, `Format()` (Delphi), `FormatFloat()` | `Format('Value: %.2f', [x])` (Delphi-style) |
| **Scala**        | Interpolation (`s""`), `f""`, `printf`-style    | `f"Value: $x%.2f"`                          |

## Typst and Typst Universe (as of 2025-06-19)

Typst itself doesn’t yet include native, flexible number‑and‑string formatting akin to `sprintf`/`std::format`, 
but both the core system and the broader *Typst ecosystem* offer solid tools and approaches.

### Core Typst: Numbering & Basic Formatting

* **`numbering`**: A built-in mechanism used for generating structured counters (e.g. headings, figures).
It supports custom patterns (like "1.1", "A‑i") or custom functions.

* **Basic formatting via functions and rules**: Typst’s formatting relies on parameters like width, fonts, alignment,
and shows rules (`#set`, `#show`), but it lacks a direct `format()`-style interface for raw numbers.

### Typst Universe Libraries: Enhanced Number & Unit Formatting

#### fancy‑units

Provides `num()`, `unit()`, and `qty()` functions to format numbers **with units**, supporting:

* Styled output rendered in math mode
* Unicode unit symbols (e.g. Ω, Å, μ)
* Language-aware decimal separators, different layout options (fractions, power‑style division)
* Custom macros for recurring units ([typst.app][3], [forum.typst.app][4])

#### unify

Functions like `num`, `unit`, `qty`, `numrange`, `qtyrange`:

* Thousand separators, exponent/scientific formatting
* SI prefixes, per‑mode (fractions/exponents), unit extensibility via CSV configs
* Handles uncertainty, ranges, customizable delimiters ([github.com][5], [github.com][6])

#### zero

Focuses on **scientific number formatting**:

* Digit grouping (e.g., 299 792 458)
* Alignment in tables
* Scientific notation (`2×10⁴`), symmetric/asymmetric uncertainty
* Rounding options and publication‑style output ([typst.app][7], [github.com][8])

### Summary

| Feature                        | Typst Core | fancy‑units    | unify       | zero           |
| ------------------------------ | ---------- | -------------- | ----------- | -------------- |
| Standard numbering (`1.2.3`)   | ✅          | –              | –           | –              |
| Basic `num()`/`unit()`         | –          | ✅ (units+nums) | ✅ (complex) | ✅ (scientific) |
| Thousand grouping              | –          | (via config)   | ✅           | ✅              |
| Scientific / exponent format   | –          | –              | ✅           | ✅              |
| Uncertainty handling           | –          | basic?         | ✅           | ✅              |
| Unit support (SI, macros)      | –          | ✅              | ✅           | –              |
| Locale-aware decimal separator | –          | ✅              | –           | –              |

## Common Patterns

Despite the diversity of programming languages, most string and type formatting implementations share a 
core set of principles and patterns. These include placeholder substitution, type-specific formatting 
(e.g., for integers, floats, and strings), and support for width, precision, and alignment. 

Nearly all systems, whether based on printf-style syntax (e.g., C, Lua), template literals (e.g., JavaScript), 
or format functions and macros (e.g., Python's `format()`, Rust's `format!`), rely on a separation between the 
format string and the data to be injected. Additionally, formatting systems often offer escape mechanisms, 
locale-aware formatting, and extensibility through custom formatters. 

These shared traits reflect a convergent evolution toward balancing expressiveness, safety, and readability. 
Understanding these commonalities helps guide the design of new formatting systems, making them more intuitive 
and interoperable.
