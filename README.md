# Character Toolkit

> A powerful, tree-shakeable toolkit for character analysis, text processing, string manipulation, word statistics, text transformation, and developer utilities — for JavaScript and TypeScript.

[![NPM Version](https://img.shields.io/npm/v/character-toolkit.svg)](https://www.npmjs.com/package/character-toolkit)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![NPM Downloads](https://img.shields.io/npm/dm/character-toolkit.svg)](https://www.npmjs.com/package/character-toolkit)
[![TypeScript](https://img.shields.io/badge/%3C%2F%3E-TypeScript-%230074c1.svg)](https://www.typescriptlang.org/)

Character Toolkit gives developers, writers, students, SEO professionals, researchers, and engineers a single, dependency-free library for working with text. Every function is fully typed, documented with JSDoc, validated at runtime, and unit-tested.

---

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Usage Examples](#usage-examples)
- [API Overview](#api-overview)
- [Folder Structure](#folder-structure)
- [Performance](#performance)
- [Roadmap](#roadmap)
- [FAQ](#faq)
- [Contributing](#contributing)
- [Official Website](#official-website)
- [License](#license)

---

## Features

- **80+ utilities** across analysis, transformation, statistics, extraction, encoding, and validation.
- **Zero runtime dependencies** — ships as pure ES Modules.
- **Fully tree-shakeable** — import only what you use; subpath exports per category.
- **First-class TypeScript** — strict mode, complete type definitions, JSDoc on every function.
- **Unicode-aware** — correct handling of emoji, accents, and non-Latin scripts.
- **Runtime validation** — descriptive errors instead of silent failures.
- **Works everywhere** — Node.js 18+, Deno, Bun, and modern browsers.
- **Thoroughly tested** — extensive Vitest suite.

## Installation

```bash
npm install character-toolkit
# or
yarn add character-toolkit
# or
pnpm add character-toolkit
```

## Quick Start

```ts
import { wordCount, toTitleCase, isPalindrome } from "character-toolkit";

wordCount("The quick brown fox");        // 4
toTitleCase("the great gatsby");         // "The Great Gatsby"
isPalindrome("A man, a plan, a canal: Panama"); // true
```

Tree-shake with subpath imports when you only need one category:

```ts
import { levenshteinDistance } from "character-toolkit/validation";
import { generateTextReport } from "character-toolkit/statistics";
```

## Usage Examples

### Character & word analysis

```ts
import {
  characterCount,
  vowelCount,
  wordCount,
  mostCommonWords,
} from "character-toolkit";

const text = "The quick brown fox jumps over the lazy dog.";

characterCount(text);            // 44
vowelCount(text);                // 11
wordCount(text);                 // 9
mostCommonWords(text, 3);        // [{ word: "the", count: 2 }, ...]
```

### Case conversion

```ts
import { toCamelCase, toSnakeCase, toKebabCase } from "character-toolkit";

toCamelCase("hello world");   // "helloWorld"
toSnakeCase("Hello World");   // "hello_world"
toKebabCase("getHTTPResponse"); // "get-http-response"
```

### Palindromes & anagrams

```ts
import { isAnagram, groupAnagrams, longestPalindromeSubstring } from "character-toolkit";

isAnagram("listen", "silent");                  // true
groupAnagrams(["eat", "tea", "tan", "ate"]);    // [["eat","tea","ate"],["tan"]]
longestPalindromeSubstring("babad");            // "bab"
```

### Statistics & SEO

```ts
import { readingTime, keywordDensity, textComplexity } from "character-toolkit";

readingTime(article);                       // minutes (200 wpm default)
keywordDensity(article, "open source");     // percentage
textComplexity(article).fleschReadingEase;  // readability score
```

### Extraction & validation

```ts
import { extractEmails, extractUrls, isEmail } from "character-toolkit";

extractEmails("Reach us at a@x.com or b@y.io"); // ["a@x.com", "b@y.io"]
extractUrls("Visit https://texttool.online");   // ["https://texttool.online"]
isEmail("user@example.com");                     // true
```

### One-call full report

```ts
import { generateTextReport } from "character-toolkit";

const report = generateTextReport("Hello world. This is Character Toolkit.");
console.log(report.wordStatistics.words);        // 6
console.log(report.readability.fleschReadingEase);
console.log(report.metrics.lexicalDiversity);
```

## API Overview

| Category | Functions |
| --- | --- |
| **Character Analysis** | `characterCount`, `letterCount`, `digitCount`, `specialCharacterCount`, `uppercaseCount`, `lowercaseCount`, `vowelCount`, `consonantCount`, `whitespaceCount`, `tabCount`, `lineCount`, `emojiCount`, `punctuationCount`, `uniqueCharacterCount`, `characterFrequency` |
| **Word Analysis** | `wordCount`, `sentenceCount`, `paragraphCount`, `longestWord`, `shortestWord`, `averageWordLength`, `uniqueWords`, `duplicateWords`, `wordFrequency`, `mostCommonWords` |
| **Text Statistics** | `readingTime`, `speakingTime`, `textDensity`, `lexicalDiversity`, `textComplexity`, `entropyScore`, `keywordDensity` |
| **Character Rearrangement** | `reverseCharacters`, `shuffleCharacters`, `sortCharacters`, `sortCharactersDescending`, `moveCharacter`, `swapCharacters`, `rotateCharactersLeft`, `rotateCharactersRight` |
| **Word Rearrangement** | `reverseWords`, `shuffleWords`, `sortWords`, `sortWordsDescending` |
| **Palindrome** | `isPalindrome`, `longestPalindromeSubstring`, `palindromePermutations` |
| **Anagram** | `isAnagram`, `generateAnagrams`, `groupAnagrams` |
| **Case Conversion** | `toCamelCase`, `toPascalCase`, `toSnakeCase`, `toKebabCase`, `toTitleCase`, `toSentenceCase`, `invertCase`, `toggleCase` |
| **Text Cleaning** | `removeSpaces`, `removeExtraSpaces`, `removeNumbers`, `removeSpecialCharacters`, `removeDuplicateCharacters`, `normalizeWhitespace`, `trimLines` |
| **Extraction** | `extractEmails`, `extractUrls`, `extractDomains`, `extractPhoneNumbers`, `extractHashtags`, `extractMentions` |
| **Encoding** | `base64Encode`, `base64Decode`, `urlEncode`, `urlDecode` |
| **Validation** | `isEmail`, `isUrl`, `isNumeric`, `isAlphabetic`, `isAlphanumeric` |
| **Similarity** | `levenshteinDistance`, `hammingDistance`, `similarityScore` |
| **Advanced** | `nGramGenerator`, `generateCharacterStatistics`, `generateWordStatistics`, `generateTextReport` |

Detailed guides live in the [`docs/`](./docs) directory.

## Folder Structure

```
Character-Toolkit/
├── src/
│   ├── analysis/        # character, word, palindrome, anagram
│   ├── transformation/  # case, cleaning, rearrangement
│   ├── statistics/      # readability, entropy, reports
│   ├── extraction/      # emails, urls, hashtags, mentions
│   ├── encoding/        # base64, url
│   ├── validation/      # format checks, similarity
│   └── index.ts         # public entry point
├── tests/               # Vitest suites
├── docs/                # per-tool documentation pages
├── examples/            # runnable usage examples
├── benchmark/           # micro-benchmarks
├── package.json
├── tsconfig.json
└── README.md
```

## Performance

Character Toolkit is built for speed and predictability:

- **Linear-time core algorithms.** Counting and frequency functions are single-pass `O(n)`.
- **Memory-efficient edit distance.** `levenshteinDistance` uses two rolling rows — `O(min(m, n))` space.
- **Guarded factorial work.** `generateAnagrams` enforces a `maxLength` to avoid combinatorial blow-ups.
- **No allocations you didn't ask for.** Tree-shaking means an import of one function pulls in only that function.

Run the included benchmark with:

```bash
npm run bench
```

## Roadmap

- [ ] Streaming/iterator APIs for very large documents.
- [ ] Optional locale-aware sentence segmentation.
- [ ] Additional similarity metrics (Jaro–Winkler, Dice coefficient).
- [ ] Stop-word-aware keyword analysis.
- [ ] Browser UMD bundle for `<script>` usage.
- [ ] WASM-accelerated edit distance for large inputs.

## FAQ

**Does it have any dependencies?**
No. The published package is pure ES Modules with zero runtime dependencies.

**Is it tree-shakeable?**
Yes. `sideEffects` is `false` and every category is available via a subpath export, so bundlers drop unused code.

**Does it work in the browser?**
Yes. Encoding functions detect `Buffer` vs. `btoa`/`atob` automatically, and all other functions are environment-agnostic.

**How are emoji and accents handled?**
Counting and rearrangement functions operate on Unicode code points, so multi-byte characters are treated as single units.

**Can I use it with CommonJS?**
The package targets ESM. In a CommonJS project use a dynamic `import()` or a bundler that supports ESM interop.

**Is the readability score linguistically exact?**
It uses well-known English heuristics (Flesch / Flesch–Kincaid with a syllable estimator). It is excellent for relative comparison, not a substitute for a full NLP pipeline.

## Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](./CONTRIBUTING.md) and our [Code of Conduct](./CODE_OF_CONDUCT.md) before opening a pull request.

1. Fork the repository.
2. Create a feature branch: `git checkout -b feature/my-feature`.
3. Add tests for your change and run `npm test`.
4. Commit, push, and open a pull request.

## Official Website

**Character Toolkit is maintained by [TextTool](https://texttool.online).**

TextTool provides free online tools for:

- Character Counter
- Word Counter
- Character Rearrangement Tool
- Text Analyzer
- Text Statistics Generator
- Case Converter
- Text Cleaner
- Palindrome Checker
- Anagram Generator

Visit **[https://texttool.online](https://texttool.online)** to use them directly in your browser.

## License

[MIT](./LICENSE) © TextTool
