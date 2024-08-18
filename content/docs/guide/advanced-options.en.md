---
title: Advanced Options
weight: 6
prev: /docs/guide/text-indenting
---

In TextWrap, the `wrap`, `fill`, and `shorten` functions are designed to offer flexible text formatting. Beyond basic usage, these functions provide advanced options that give you fine control over how text is processed and formatted.

<!--more-->

## Supported Options

- **`width`**</br>
  (default: `70`) – The maximum length of wrapped lines. As long as there are no individual words in the input text longer than `width`, TextWrap guarantees that no output line will be longer than `width` characters.
- **`expand_tabs`**</br>
  (default: `true`) – If `true`, then all tab characters in text will be expanded to spaces using the [`expandTabs()`](https://npm.im/@barudakrosul/expand-tabs) method of text.
- **`tabsize`**</br>
  (default: `8`) – If `expand_tabs` is `true`, then all tab characters in text will be expanded to zero or more spaces, depending on the current column and the given tab size.
- **`replace_whitespace`**</br>
  (default: `true`) – If `true`, after tab expansion but before wrapping, the `wrap()`, `fill()`, or `shorten()` method will replace each whitespace character with a single space. The whitespace characters replaced are as follows: tab, newline, vertical tab, formfeed, and carriage return (`'\t\n\v\f\r'`).</br>
  {{< callout type="info" >}}
    If `expand_tabs` is `false` and `replace_whitespace` is `true`, each tab character will be replaced by a single space, which is not the same as tab expansion.
  {{< /callout >}}
  </br>
  {{< callout type="info" >}}
    If `replace_whitespace` is `false`, newlines may appear in the middle of a line and cause strange output. For this reason, text should be split into paragraphs (using [`String.splitLines()`](https://npm.im/@barudakrosul/split-lines) or similar) which are wrapped separately.
  {{< /callout >}}

## Basic Usage

```javascript {filename="example.js"}
const text = "This is a long line of text that needs\tto be wrapped properly\twithout cutting\twords in half.";
const options = {
  replace_whitespace: false,
  tabsize: 12,
  initial_indent: "[!] "
}
const wrapped = textwrap.wrap(text, 20, options)

console.log(wrapped);
```

Result:

```javascript
[
  '[!] This is a long',
  'line of text that',
  'needs          to be',
  'wrapped properly',
  'without cutting',
  'words in half.'
]
```
