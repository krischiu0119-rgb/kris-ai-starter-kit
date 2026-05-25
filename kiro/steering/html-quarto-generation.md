---
inclusion: always
---

<!-- 2026-05-25 -->

# HTML / Quarto / Markdown Generation Steering

## Primary Rule: Do Not Confuse Quarto Rendering With Manual HTML Generation

When the user asks to convert Markdown or Quarto documents into HTML, first determine whether the task is:

1. **Quarto/Markdown rendering** — use Quarto CLI
2. **Custom hand-authored HTML generation** — manual workflow

If the source is `.qmd`, `.md`, `_quarto.yml`, or the user explicitly mentions Quarto, prefer the Quarto workflow. Do not manually recreate the document as a large `slides.html` unless the user explicitly asks for a custom standalone HTML file.

---

## Quarto Workflow

When the task is Markdown/Quarto to HTML:

1. Inspect the source document first.
2. Check whether YAML front matter exists.
3. If YAML front matter is missing, recommend or add valid Quarto front matter.
4. Use Quarto render commands when available.

```bash
quarto render document.qmd --to html
quarto render slides.qmd --to revealjs
```

If `quarto` CLI is not installed or not available, report that clearly. Do not silently replace the Quarto workflow with manually generated HTML.

---

## Manual HTML Generation Workflow

Only use manual HTML generation when the user explicitly wants custom standalone HTML, custom CSS slides, or a non-Quarto artifact.

For large HTML files (> ~200 lines):

1. **Do not use sub-agents** — sub-agent context will be exhausted by large HTML content.
2. **Do not put an entire large HTML file into one tool call** — risk of truncation.
3. Prefer one of these approaches:
   - `fs_write` first chunk (HTML head + CSS + first few sections) → `fs_append` subsequent chunks
   - Template + partials assembled by a build script
   - Structured source data rendered into HTML via a generator script

If direct file writing is used:

1. Write in chunks of ~100–150 lines each.
2. Include `</body></html>` in the final chunk (not earlier).
3. After all chunks, verify the file has proper closing tags.
4. Never remove closing tags unless the next step immediately restores them.

---

## Tool Call Safety (CRITICAL)

Before calling any file tool, mental checklist: `path` ✓ · `text`/`newStr` ✓ · parameter types correct ✓

| Tool | Required Parameters | Common Mistake |
|------|-------------------|----------------|
| `fs_write` | `path` + `text` | Forgetting `text` |
| `fs_append` | `path` + `text` | Forgetting `text` |
| `str_replace` | `path` + `oldStr` + `newStr` | Forgetting `newStr` (even for deletion, use `""`) |

**2-Strike Rule**: If the same tool fails twice with the same error:
1. Stop repeating the call.
2. Inspect the error message — identify the missing/invalid parameter.
3. Switch strategy if the tool fundamentally cannot do what you need.

---

## Sub-Agent Usage for HTML Tasks

**Do NOT ask a sub-agent to generate or write a large complete HTML file.**

The main context should own final file assembly and verification. Sub-agents may help with reviewing, outlining, or generating small components (< 50 lines).

---

## macOS Shell Compatibility

| ❌ Don't use | ✅ Use instead |
|-------------|---------------|
| `head -n -2 file` | `lines=$(wc -l < file) && head -n $((lines - 2)) file` |
| `sed -i 's/x/y/' file` | `sed -i '' 's/x/y/' file` |

---

## Local HTML Visual QA

**Do not use `file://`** — Playwright and many browser tools block it.

```bash
python3 -m http.server 8765 --directory <dir> &
# → http://localhost:8765/<file>.html
# After QA: lsof -ti:8765 | xargs kill -9
```

---

## PDF Generation from HTML Slides

When generating PDF from HTML slides using Playwright:

1. Set page size to match slide dimensions (e.g., `width: '1280px', height: '720px'`)
2. Use `printBackground: true` and zero margins
3. **Before PDF generation**, inject inline styles via `page.evaluate()`:
   - `maxHeight` + `overflow: hidden` on each slide
   - `pageBreakAfter: always` + `breakAfter: page`
   - Remove body padding/gap
4. Verify resulting PDF page count matches slide count

---

## Final Success Criteria

For HTML/slides/report generation, completion requires:
1. Source workflow chosen correctly (Quarto vs. manual)
2. File generated successfully
3. HTML structure validated (closing tags present)
4. Browser rendering checked
5. Visual QA completed (overflow check)
6. PDF page count verified (if applicable)
7. Any missing tools reported clearly
