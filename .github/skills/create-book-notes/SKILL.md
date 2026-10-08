---
name: create-book-notes
description: Interview the reader about their latest book chapter or reading session, then create or update a chapter summary and its README link. Use when asked to create book notes, capture reading takeaways, or summarize what the reader learned.
---

# Create book notes

Turn the reader's own reflections into concise chapter notes. This is an interactive interview, not a request to generate a chapter summary from general knowledge.

## 1. Read the repository conventions

- Read the root `AGENTS.md` and any instructions that apply to the destination directory. Follow them for structure, placement, naming, and README updates.
- Read `The_Pragmatic_Programmer/Chapter_01/Chapter_01_summary.md` as the style reference and `README.md` for the book index.
- Inspect the relevant book directory once the reader identifies the book. Reuse its existing directory name.
- Do not modify any files until the reading scope and takeaways are clear.

## 2. Interview the reader

Use `ask_user` to ask questions and wait for answers. Keep the conversation friendly and focused, with a small group of related questions per turn. Reuse information already provided rather than asking for it again.

Start by identifying the reading session:

- Which book did you read?
- Which chapter number and title was it?
- Did you finish the chapter, or read only a part? Which section, topic, or page range did you cover?

Then explore their understanding:

- What were the main ideas you learned, in your own words?
- What stood out, surprised you, or changed how you think?
- Was there an example or practical application that helped the ideas click?

Ask targeted follow-ups only where needed to make a takeaway clear. For example: "What makes that approach useful?" or "How would you apply that idea?" Do not force a fixed number of ideas or require an example if the reader has none.

If a chapter number or title is missing, ask for it rather than guessing from the latest note or inventing a title. If the reading spans several chapters or is not chapter-based, clarify how the reader wants to organize it before choosing a destination. For several chapters, gather the takeaways for each and create separate notes.

If the reader cancels, stop without making changes. If essential information remains unanswered, explain what is missing and do not write a speculative note.

## 3. Write the note

- Base the content on the reader's answers. Improve clarity and consolidate overlapping ideas while preserving their meaning.
- Do not add book claims, examples, quotations, or takeaways from memory or external sources unless the reader explicitly requests additional research. Do not present a paraphrase as a direct quote from the book.
- Follow the heading, `Key Ideas`, and `Core Message` structure defined in `AGENTS.md`. Write in the language used by the repository's chapter notes unless the reader requests otherwise.
- For a partially read chapter, make the limited scope explicit in the relevant idea explanations. Do not imply that the note covers unread sections.
- Use the reader's takeaways to write the single-sentence `Core Message` in your own words.
- Save the note at `<Book_Name>/Chapter_<NN>/Chapter_<NN>_summary.md`, with a two-digit chapter number in the path. For a new book, use an underscore-separated directory name consistent with the repository.
- If the destination already exists, read it and ask whether to merge the new takeaways or replace the note. Default to merging and preserving existing content; do not overwrite without the reader's decision. Clarify conflicting takeaways rather than silently discarding either version.

## 4. Update the README

- Add the chapter link to the relevant book's chapter list in `README.md`, in chapter order, matching the existing formatting.
- If the book has no entry, add a book section and chapter list consistent with the README. Do not invent a book quote or author.
- Preserve existing book-level links and unrelated content.
- Keep that book's chapter list consistent with its chapter notes, without duplicate links.

## 5. Check and finish

- Read back the saved note and the affected README section.
- Check that the note follows `AGENTS.md`, reflects the interview accurately, and that the README link resolves to the saved file.
- Briefly report the note's path and the README update. Do not commit or push unless explicitly requested.
