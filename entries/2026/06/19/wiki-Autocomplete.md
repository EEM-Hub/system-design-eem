---
source: sources/wiki-Autocomplete.md
source_url: https://en.wikipedia.org/wiki/Autocomplete
---

## Autocomplete and Word Prediction Systems

Autocomplete (also called word completion or predictive text) is a software feature that predicts the rest of a word or phrase as a user types. This page covers the history, types, integration points, underlying algorithms, and efficiency research related to autocomplete technology across computing platforms — from accessibility devices to search engines to IDEs.

## Key Concepts

- **Autocomplete** predicts words from partial input; **autocorrect** automatically replaces strings (e.g., fixing typos like "teh" → "the")
- **Context completion** predicts words based on surrounding text and training data, not just prefix matching — more precise but requires larger training datasets
- **Line completion** (introduced in TED Notepad, 2006) uses the current document as a training set to complete entire lines
- **Language modeling** underpins word prediction — calculating which words are most likely within a vocabulary
- **Frecency model** combines frequency and recency to rank predictions, commonly used on AAC devices
- Word prediction was originally designed as an **assistive technology** for people with physical disabilities, whose speech-generating device output is <10% the speed of oral speech
- Autocomplete works best in **constrained domains**: command-line interpreters (limited commands), email (small set of frequent addresses), source code (structured namespaces)
- Many systems **learn user vocabulary** over time, adding new words to prediction dictionaries
- Search engine autocomplete uses **error-tolerant matching** algorithms: phonetic Soundex and language-independent Levenshtein distance
- Content filtering: vulgar, morbid, or sensitive terms are often excluded from autocomplete suggestions

## Commands and Syntax

**HTML autocomplete attribute** — controls browser autofill behavior on forms:
```html
<form autocomplete="on">
  <input name="username" autocomplete="on">
  <input name="password" type="password">
</form>
```

**HTML datalist element** — provides a predefined set of autocomplete options for an input:
```html
<input list="ice-cream-flavors" id="ice-cream-choice" name="ice-cream-choice" />
<datalist id="ice-cream-flavors">
  <option value="Chocolate"></option>
  <option value="Vanilla"></option>
</datalist>
```

**Command-line completion** — press Tab after typing initial characters to complete commands/filenames (bash, PowerShell, cmd.exe)

## Relationships

- **Autocorrection**: Related but distinct — replaces entire strings rather than completing partial input
- **Code completion / IntelliSense**: Specialized autocomplete for programming — leverages namespace structure, variable/function names, and class members; doubles as inline documentation
- **Predictive text (mobile)**: Android/iOS implementation of autocomplete for touchscreen keyboards
- **Incremental search**: Search-as-you-type pattern used in search engines (also called autosuggest)
- **Language modeling**: Foundation technology — statistical models that calculate word probability within a vocabulary
- **Augmentative and Alternative Communication (AAC)**: Primary domain where word prediction originated as assistive technology
- **Chinese typewriter history**: Predictive text was invented in 1950s China to solve logographic character selection; this work influenced modern computer word processors
- **Reputation management**: Search autocomplete suggestions can impact brand perception; negative term associations are a concern

## Exam-Relevant Points

- Autocomplete was **invented in 1950s China** for typewriters handling thousands of logographic characters — not in Western computing
- The `autocomplete` HTML attribute can be set to `"on"` or `"off"` at both `<form>` and `<input>` level; child elements inherit the parent form's value
- The `<datalist>` HTML element provides native browser autocomplete without JavaScript
- **Cognitive load tradeoff**: Word prediction reduces keystrokes but does not always increase typing speed because users must shift attention from keyboard to suggestion list
- Research-backed UI guidelines: limit suggestion list to **5 words**, use **vertical layout**, position list **near the keyboard** (bottom of screen) to minimize eye movement
- Browser autofill of forms creates a **phishing attack vector** via hidden form fields that silently collect personal information
- **Levenshtein distance** and **Soundex** are named algorithms used for error-tolerant autocomplete in search engines
- In code editors, autocomplete encourages **longer, more descriptive variable names** because typing cost is reduced
- Database query tool autocomplete is **context-aware**: suggests table names vs. column names based on cursor position within SQL statement
- The first autocomplete software was **Smartype** (late 1980s), originally for medical transcriptionists in WordPerfect for MS-DOS
