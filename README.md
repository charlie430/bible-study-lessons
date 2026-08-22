# Bible Study Lessons

Reusable Bible study lessons (cleaned OCR text, study plans, and metadata) aligned with the teaching of Stephen Davey / Wisdom International.

These lessons are designed to be used with the **bible-study** Grok skills and the public web app. Personal sessions (transcripts, answers, progress) are stored separately so this repo can remain public without exposing private study notes.

## Structure

```
lessons/
  <book-slug>/
    book-meta.yaml           # book title, author, slug (once per book)
    <lesson-slug>/
      lesson-meta.yaml       # lesson title, number, scripture, theme
      content.md             # full cleaned lesson text (authoritative script)
      study-plan.yaml        # interaction map (YAML only — no markdown)
```

### `study-plan.yaml` format

```yaml
items:
  - id: p1
    type: prayer
    title: Opening prayer
    prompt: Pray for understanding.
  - id: r1
    type: bible-reading
    reference: Matthew 3:1-12
  - id: q1
    type: question
    number: 1
    text: What stood out to you?
  - id: q2
    type: reflection
    number: 2
    text: How will you apply this?
```

Supported `type` values: `prayer`, `bible-reading`, `question`, `fill-blank`, `table`, `reflection`, `memory`.

Ids: `p1`… for prayer, `r1`… for bible-reading, `q1`… for question-like items.

### `book-meta.yaml` example

```yaml
title: "Follow Me: An In-Depth Study of the Gospel of Matthew"
author: "Elizabeth Bagwell Ficken"
slug: follow-me-gospel-of-matthew
doctrinal_alignment: "Stephen Davey / Wisdom International"
notes: "Optional notes"
```

### `lesson-meta.yaml` example

```yaml
title: "Jesus' Baptism"
number: 3
slug: lesson-3-jesus-baptism
scripture: "Matthew 3:1-17"
theme: "Short theme description"
workbook_pages: "17–21"
created: "2026-08-20"
```

Do **not** repeat full book title/author in `lesson-meta.yaml` — that lives only in `book-meta.yaml`.

## Books & Lessons

### Follow Me: An In-Depth Study of the Gospel of Matthew
*by Elizabeth Bagwell Ficken*

- [Lesson 3: Jesus' Baptism (Matthew 3:1-17)](lessons/follow-me-gospel-of-matthew/lesson-3-jesus-baptism/)
- [Lesson 4: Jesus Versus Satan (Matthew 4:1-11)](lessons/follow-me-gospel-of-matthew/lesson-4-jesus-versus-satan/)

## Usage

- **Ingest:** New lessons are added via the `bible-study-ingest` skill (OCR → YAML meta + content + YAML study plan → this repo).
- **Study (chat skill):** `bible-study-session` loads lessons from this repo.
- **Web app:** Catalog and lesson content live in Supabase; study plans are stored as YAML text.

Personal session archives live in the private repo [`charlie430/bible-studies`](https://github.com/charlie430/bible-studies).
