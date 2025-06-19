# Introduction

## What is Typst

Typst is a modern markup-based typesetting system designed to offer a powerful yet user-friendly alternative to LaTeX. 
It aims to simplify the process of creating professional-quality documents such as academic papers, reports, and presentations. 
Typst combines the precision and control of traditional typesetting tools with the flexibility of a programming language, 
featuring built-in logic, functions, and variables. Its syntax is clean and intuitive, enabling both technical and non-technical 
users to format complex documents efficiently. Typst is particularly well-suited for collaborative environments, offering fast 
compilation and real-time previews, and supports web-based editing, which lowers the barrier to entry for new users. Overall, 
Typst represents a significant step forward in document preparation, balancing ease of use with advanced typesetting capabilities.

## The need for Number Formatting

As Typst evolves into a comprehensive typesetting system, the need for advanced number and text formatting capabilities — akin to 
those found in sprintf (C/C++) or std::format (C++20, Python)—becomes increasingly essential. Complex documents often demand 
precise control over how numerical data and strings are displayed, such as padding, alignment, fixed decimal precision, localized 
number formats, and date/time formatting. Without such features, authors must rely on verbose or inefficient workarounds, which 
undermines Typst’s goal of providing both elegance and expressiveness. Integrating robust formatting tools would enhance Typst’s 
utility in scientific, technical, and data-driven documents, supporting dynamic content generation, programmatic layout logic, 
and multilingual output. Ultimately, these capabilities are foundational for bridging the gap between high-level typesetting and 
low-level data presentation, making Typst a more competitive and versatile platform for modern publishing.

## Analysis, ie. Prior Art

Let’s begin with an analysis:

* What formatting implementations currently exist across major programming languages or applications?
* What common principles or patterns do they share?
* Should we adopt an existing standard, or is there a justified need to create a new one?

### Programming Languages

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

### Common Patterns

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
