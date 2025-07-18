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
undermines Typst’s goal of providing both elegance and expressiveness. 

Integrating robust formatting tools would enhance Typst’s utility in scientific, technical, and data-driven documents, supporting 
dynamic content generation, programmatic layout logic, and multilingual output. Ultimately, these capabilities are foundational 
for bridging the gap between high-level typesetting and low-level data presentation, making Typst a more competitive and versatile 
platform for modern publishing.

While traditional string and type formatting covers numeric precision, alignment, and data representation, it falls short in domains 
requiring scientifically accurate expression of physical quantities. Formatting scientific units—such as meters, seconds, kilograms, 
or derived units like Newtons or Joules — is critical in technical, engineering, and scientific documentation. These units must not 
only be displayed correctly with symbols and SI prefixes, but also remain semantically meaningful for conversions, validation, and 
consistent presentation. 

Embedding unit-aware formatting alongside standard type formatting allows authors to maintain both clarity and correctness, especially 
in multilingual or multidisciplinary contexts. Without this support, developers and document authors must implement fragile, ad hoc 
solutions that undermine the consistency and readability of technical content. A unified formatting system that incorporates units 
bridges the gap between data representation and domain accuracy, enhancing both the expressiveness and robustness of scientific communication.

