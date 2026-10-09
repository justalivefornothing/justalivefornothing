# JAFN

I work on small browser-based tools, especially search and programming languages.

## Selected projects

### [Sift](https://github.com/justalivefornothing/sift-search)

A browser search engine with typo matching, filters, and an explanation of why each result ranks where it does. Queries run in a Web Worker over a bundled, generated dataset.

A recent fix bounds pagination and lets the app recover from invalid requests. The [project notes](projects/sift.md) cover that change, the search pipeline, and its limits.

### [Kiln](https://github.com/justalivefornothing/kiln-lang)

A small typed language and browser playground for inspecting how source becomes WebAssembly. The editor shows tokens, syntax trees, emitted bytes, and program output.

A recent fix removed a fallback that could run an infinite loop on the UI thread. The [project notes](projects/kiln.md) cover worker execution and the language's supported subset.

---

[Other experiments](projects/experiments.md) · [All repositories](https://github.com/justalivefornothing?tab=repositories) · [Website](https://jafn-portfolio.vercel.app)
