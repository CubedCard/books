# Note-writing instructions

Use the chapter summary at [`The_Pragmatic_Programmer/Chapter_01/Chapter_01_summary.md`](The_Pragmatic_Programmer/Chapter_01/Chapter_01_summary.md) as the standard structure for new book chapter notes.

## Location and filename

Store each chapter note in its own chapter directory under the book directory, using this pattern:

`<Book_Name>/Chapter_<NN>/Chapter_<NN>_summary.md`

Use a two-digit chapter number consistently in both the directory and filename.

## README

Whenever you add a chapter note, update `README.md` to include a link to it in the relevant book's chapter list. Keep the list consistent with the notes present in the repository.

## Note structure

Each note should contain:

1. A level-one heading with the chapter number and title.
2. A `Key Ideas` section containing concise bullets. Bold each idea's name, then explain it after an em dash. Use nested bullets only when an idea needs supporting points.
3. A `Core Message` section with a single blockquote that captures the chapter's main takeaway.

Use this template:

```markdown
# Chapter <N> — <Chapter Title>

## Key Ideas
- **<Idea>** — <Concise explanation.>
- **<Idea>** — <Concise explanation.>

## Core Message
> <One-sentence summary of the chapter's central takeaway.>
```
