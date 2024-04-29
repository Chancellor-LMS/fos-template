---
name: "Tables"
---

Chancellor supports the creation of tables in markdown, following the [MultiMarkdown syntax](https://www.npmjs.com/package/markdown-it-multimd-table).

# Basic Table

```markdown
| Header 1 | Header 2 | Header 3 |
| -------- | -------- | -------- |
| Cell 1   | Cell 2   | Cell 3   |
| Cell 4   | Cell 5   | Cell 6   |
| Cell 7   | Cell 8   | Cell 9   |
| Cell 10  | Cell 11  | Cell 12  |
```

| Header 1 | Header 2 | Header 3 |
| -------- | -------- | -------- |
| Cell 1   | Cell 2   | Cell 3   |
| Cell 4   | Cell 5   | Cell 6   |
| Cell 7   | Cell 8   | Cell 9   |
| Cell 10  | Cell 11  | Cell 12  |

# Table with Alignment

```markdown
| Left-aligned | Center-aligned | Right-aligned |
| :---         | :---:          | ---:         |
| Cell 1       | Cell 2         | Cell 3        |
| Cell 4       | Cell 5         | Cell 6        |
| Cell 7       | Cell 8         | Cell 9        |
| Cell 10      | Cell 11        | Cell 12       |
```

| Left-aligned | Center-aligned | Right-aligned |
| :---         | :---:          | ---:         |
| Cell 1       | Cell 2         | Cell 3        |
| Cell 4       | Cell 5         | Cell 6        |
| Cell 7       | Cell 8         | Cell 9        |
| Cell 10      | Cell 11        | Cell 12       |

# Multiline Table

Backslashes `\` at the end of a line can be used to create multiline cells. This can be useful for lists, or multiline content.

```markdown
| Header 1 | Header 2 | Header 3 |
| -------- | -------- | -------- |
| Cell 1   | Cell 2   | Cell 3   |
| - Cell 4   | - Cell 5   | - Cell 6   \
  - continued | - Cell 7  | - Cell 8  |
| Cell 9   | Cell 10  | Cell 11  |
```

| Header 1 | Header 2 | Header 3 |
| -------- | -------- | -------- |
| Cell 1   | Cell 2   | Cell 3   |
| - Cell 4   | - Cell 5   | - Cell 6   \
  - continued | - Cell 7  | - Cell 8  |
| Cell 9   | Cell 10  | Cell 11  |

# Column Span

```markdown
| Span 2 Columns || Span 3 Columns |||
| --- | --- | --- | --- | --- |
| Cell 1 | Cell 2 | Cell 3 | Cell 4 | Cell 5 |
```

| Span 2 Columns || Span 3 Columns |||
| --- | --- | --- | --- | --- |
| Cell 1 | Cell 2 | Cell 3 | Cell 4 | Cell 5 |

# Row Span

`^^` indicates cells being merged above.

```markdown
Stage | Direct Products | ATP Yields
----: | --------------: | ---------:
Glycolysis | 2 ATP ||
^^ | 2 NADH | 3--5 ATP |
Pyruvaye oxidation | 2 NADH | 5 ATP |
Citric acid cycle | 2 ATP ||
^^ | 6 NADH | 15 ATP |
^^ | 2 FADH2 | 3 ATP |
**30--32** ATP |||
```

Stage | Direct Products | ATP Yields
----: | --------------: | ---------:
Glycolysis | 2 ATP ||
^^ | 2 NADH | 3--5 ATP |
Pyruvaye oxidation | 2 NADH | 5 ATP |
Citric acid cycle | 2 ATP ||
^^ | 6 NADH | 15 ATP |
^^ | 2 FADH2 | 3 ATP |
**30--32** ATP |||