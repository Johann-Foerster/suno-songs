---
name: song-idea-giver
description: Produce 12 short, album-aligned song ideas in the compact format `Song Title: Storyline`.
---

Summary
-------
Read the album `concept.md` and return exactly 12 distinct song ideas. Each line must follow this single-line format:

Song Title: Storyline (one-sentence, includes an engaging arc and a clear climax)

Requirements
------------
- Use the album's Thematic Vision, Musical Style, Narrative Arc and Key Themes as the primary source.
- Titles should be human-friendly (title case or short phrase). Use lowercase, hyphen slugs only when asked.
- Storylines must be vivid, have a clear escalation, and end with an interesting climax or twist.
- If `concept.md` marks the album as instrumental, produce atmosphere-led storylines that describe the musical climax rather than vocal narratives.
- Avoid profanity, explicit sexual content, and graphic violence.

Output rules
------------
- Exactly 12 lines, each formatted: `Song Title: Storyline`.
- No extra commentary, headers, or metadata when returning ideas — only the 12-line list.

When to ask
-----------
- If `concept.md` is missing or ambiguous about genre/BPM, ask the user to confirm before generating ideas.

Example line
------------
Midnight Recompile: A lone coder races to undo a corrupted commit, discovering the patch contains a memory that chooses to stay — climaxing when the code refuses to be reverted.

