# CKA Revision Hub — Context Prompt

Paste this into a new Cowork chat to bring Claude up to speed on the project.

---

## Copy-paste this into a new chat:

I'm studying for the CKA exam. I have a folder of HTML revision notes at `/Users/anuragsunil/CKA` — please request access to it.

The folder is a small "study hub": an `index.html` that links to topic-specific HTML notes, all sharing one polished dark theme. When I ask you to add a new note or expand a topic, you should:

1. **Create a new self-contained `cka-<topic>.html` file** in `/Users/anuragsunil/CKA` matching the existing theme (see "Theme System" below — every page must use this exact CSS).
2. **Add a card for it on `index.html`** under the right category section.
3. **Update the note count** in the index header stats.

Always read `cka-daemonset.html` (or any recent note) first to copy the exact CSS — every page is fully self-contained with its own `<style>` block. Don't introduce a new theme; reuse this one.

### Theme System (must match exactly)

- **Background:** `#0d1117` with subtle radial gradients (blue 15%/10% top-left, orange 85%/80% bottom-right).
- **Palette (CSS vars):** `--bg #0d1117`, `--surface #161b22`, `--surface-2 #1c2128`, `--border #30363d`, `--text #e6edf3`, `--text-dim #8b949e`, `--accent #58a6ff` (blue), `--accent-warm #f0883e` (orange), `--green #3fb950`, `--red #f85149`, `--yellow #e3b341`, `--purple #bc8cff`, `--code-bg #010409`.
- **Fonts:** Inter (body), Fraunces serif (headings — italic for accent words in h1), JetBrains Mono (code, eyebrows, table headers).
- **Layout:** `max-width: 860px` container, `← back to hub` link top-left linking to `index.html`.

### Component Vocabulary (reuse, don't invent)

- **Header:** `.eyebrow` (mono, uppercase, blue) → `<h1>` with one italic orange accent word inside `<span class="accent">` → `.subtitle` (text-dim).
- **`<h2>`** uses `§` prefix in blue mono via `::before`.
- **`.key-fact`** — gradient surface card with orange left border, used for the "TL;DR" or "one line to remember".
- **`.scenario`** — story-mode cards with colored left borders. Variants: `.good` (green), `.warn` (yellow), `.bad` (red), `.info` (blue), `.story` (purple). Each has a `.label` chip in matching color.
- **`.mistake`** — red-tinted callout for pitfalls. `<b>✗ Mistake N —</b>` style.
- **`.tip`** — green-tinted callout for advice. `<b>✓ Tip —</b>` style.
- **`.vs`** — two-column grid for side-by-side comparisons (1fr 1fr, stacks at 600px).
- **`.mantra`** — italic centered quote at the bottom with horizontal borders, label "The Mantra" in mono uppercase.
- **`footer`** — mono, centered, breadcrumb-style path like `cka_notes / category / topic.html`.
- **Tables:** mono uppercase headers on `--surface-2`, body rows on `--surface`.
- **Code blocks:** `var(--code-bg)` background, blue 3px left border, JetBrains Mono. Inline `code` is orange on dark.
- **Annotations in YAML:** `<span class="annotation">` for yellow italic comments inside `<pre>` blocks.

### Tone / Content Style

- **Story-driven where possible** — analogies (chefs in a kitchen, building inspectors, job fairs, recipes). The story should map cleanly to the technical concept.
- **Layered:** start with mental model → cast/setup → scenarios → syntax → common mistakes → quick reference / commands → mantra.
- **Exam-grade:** every note ends with imperative `kubectl` commands the user can actually run.
- **Concise prose, no fluff.** Bullets only when listing distinct items.
- **Mistakes section is non-negotiable** — list 3–6 real pitfalls with red callouts.

### Existing Notes (as of last update)

| File | Category | Topic |
|---|---|---|
| `index.html` | hub | clickable index of all notes |
| `cka-scheduling-story.html` | Scheduling | selectors, affinity, tolerations (job-fair story) |
| `cka-nodeaffinity-terms.html` | Scheduling | terms vs expressions, AND/OR logic |
| `cka-daemonset.html` | Scheduling/Workloads | DaemonSet concept, dry-run trick, mistakes |
| `cka-requests-and-limits-story.html` | Resources | CPU/memory request+limit permutations (kitchen story) |
| `k8s-memory-units-gi-vs-gb.html` | Resources | Gi vs GB binary/decimal |
| `cka-apiversion-guide.html` | Fundamentals | how to guess apiVersion |

### Hub (`index.html`) Structure

- Header with logo chip, gradient h1, tagline, stats (notes count / categories / last updated).
- Section per category (`.section-title` with mono uppercase, divider line).
- Cards (`.card`) inside `.grid`. Each card has a colored top stripe via `--card-accent` style attr, a tag chip (`.tag.scheduling | .resources | .story | .fundamentals`), an h2, a one-sentence description, and a card-meta showing the filename.
- When adding a new note: bump the notes count in the stats, add a new card under the matching category, optionally add a new category section if needed.

### Behavioural Rules for You

- **Never** use a light theme or a different palette.
- **Never** create a new HTML note without also linking it from `index.html`.
- **Always** include a `← back to hub` link in new notes.
- **Always** give me `computer://` links to view files at the end.
- Keep responses concise. The HTML files do the heavy lifting; chat replies should just summarise what changed.

That's it — ask me what topic to add next.

---

## How I use this

1. Open a new Cowork chat.
2. Copy the section above ("Copy-paste this into a new chat") and paste as my first message.
3. Then ask for whatever new topic I want — Claude will match the theme and update the hub.
