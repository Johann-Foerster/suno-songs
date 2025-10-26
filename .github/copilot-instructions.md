# GitHub Copilot Agent Instructions for `suno-songs`

This repository is for generating Suno song prompt assets (lyrics + style metadata). It is NOT a codebase. Your job: produce correctly structured prompt files to maximize consistent, high‑quality Suno outputs.

## Core Folder & File Convention
Each song lives at: `{genre}/{album}/{song}/`
Required files inside the song folder:
1. `text.txt` – Lyrics with section tags.
2. `text-prompt.txt` – Same lyrics, but tough/technical words rewritten phonetically for cleaner TTS.
3. `style.txt` – Concise 4‑part style prompt (Genre / Exclude / Instruments / Tags).

Each album also requires:
4. `concept.md` – Album concept document at `{genre}/{album}/concept.md` describing the thematic vision, style consistency, and narrative arc for all songs in the album.

Directory naming: lowercase, hyphen-separated (`deep-house`, `tech-trance`). Avoid spaces. Assume you may create new genre/album folders when absent.

## Lyrics Rules (`text.txt`)
Use section headers: `[Intro]`, `[Verse]`, `[Chorus]`, `[Bridge]`, `[Drop]`, `[Outro]`.
Optional performance cues in brackets, too: `[whispered]`, `[airy]`, `[belted]`, `[instrumental break]`.
Target total word count: 120–180 (≤180). Keep individual lines concise while allowing for comprehensive storytelling; avoid overlong single verses.
Lyrics should tell an engaging story that keeps the listener's attention throughout the song. Focus on compelling narratives, vivid imagery, and emotional progression that maintains interest from start to finish.
Instrumental tracks: include a single `[Instrumental]` section or minimal atmospheric cues.
Always consider the album's concept.md when writing lyrics to ensure thematic consistency and narrative coherence across the album.

## TTS Variant (`text-prompt.txt`)
Clone `text.txt`, then transform technical / acronym / hard‑to‑pronounce tokens:
- `HTML` → `Aitch Tee Em Ell`
- `CSS` → `See Ess Ess`
- `SQL` → `Ess Queue Ell`
- `JSON` → `Jay Son`
- `CSV` → `See Ess Vee`
Also expand years/numbers if clarity helps: `1999` → `nineteen ninety nine`. Maintain tags & section order.

## Album Concept (`concept.md`)
Each album requires a concept document at `{genre}/{album}/concept.md` that defines:
- **Thematic Vision**: Overall narrative and conceptual framework
- **Musical Style Consistency**: Genre, tempo, instrumentation, and production guidelines
- **Narrative Arc**: How songs connect and progress through the album
- **Key Themes**: Central ideas and motifs that run through all songs
- **Lyrical Guidelines**: Specific direction for maintaining thematic coherence

When creating songs, always reference the album's concept.md to ensure consistency in style, themes, and narrative progression. New albums should have their concept.md created before any songs are written. For existing albums without concept.md, create one based on existing songs' themes and styles before adding new songs.

## Style Prompt (`style.txt`)
Use exactly this 4-part template (one per line or compact block):
```
Genre: "<specific subgenres>"  Exclude: "<styles NOT wanted>"
Instruments: "<key instruments; vocal treatment>"
Tags: "<BPM; mood; structure cues; 2–4 style adjectives>"
```
Guidelines:
- Pick ONE spine + ONE color: e.g. `Techno Trance` + `80s synthwave arps`.
- Limit style adjectives (2–4) from the seed bank: `uplifting`, `dark`, `melodic`, `hypnotic`, etc.
- Use concrete production terms: `rolling bassline`, `909 hats`, `sidechain pump`, `supersaw leads`.
- BPM numeric when known (e.g. `138 BPM`).
- Avoid overstuffing instruments; prefer 4–6 focused elements.

## Example `style.txt`
```
Genre: "Techno Trance" Exclude: "Trap, Acoustic, Dubstep"
Instruments: "whispered female vocals; supersaw leads; rolling bassline; 909 percussion; neon pads"
Tags: "140 BPM; euphoric drop; long riser; hypnotic; 90s nostalgia"
```

## Common Tag / Phrase Bank (use sparingly)
Energy: `138 BPM`, `slow build`, `fast`, `extended build`
Mood: `dark`, `uplifting`, `dreamy`, `hypnotic`, `melancholic`
Texture: `supersaw leads`, `metallic stabs`, `909 percussion`, `atmospheric pads`
Vocals: `whispered female vocals only (no belting)`, `breathy harmonies`, `[Instrumental]`
Structure: `euphoric drop`, `instrumental break`, `key change after verse 2`, `long riser`
FX: `sidechain pump`, `vinyl crackle`, `tape delay`, `gated reverb`

## Quality Checklist Before Commit
- All three files exist and non-empty.
- Album concept.md exists at {genre}/{album}/concept.md.
- `text.txt` 120-180 words; sections & cues formatted correctly; tells engaging story.
- `text-prompt.txt` matches structure; phonetic replacements applied.
- `style.txt` uses template; no vague terms (`nice`, `cool`).
- No style overloading (avoid >4 adjectives or conflicting genres).
- Lyrics align with album concept and maintain thematic consistency.

## Edge / Decision Notes
- If genre fusion ambiguous, pick dominant atmosphere (e.g., trance vs techno) and add one secondary flavor.
- For purely instrumental intentions: exclude vocals explicitly in Genre or Exclude and add `[Instrumental]` tag line.
- Prefer consistency: if BPM specified in `style.txt`, avoid tempo contradictions in lyrics.

## Adding a New Song (Recommended Flow)
1. Decide genre + album + song slug; create folders.
2. Check/create album concept.md if it doesn't exist at {genre}/{album}/concept.md.
3. Draft `style.txt` (spine + color + BPM + 2–4 descriptors) aligned with album concept.
4. Write lyrics (`text.txt`) with sections & cues that tell an engaging story and align with album concept.
5. Derive phonetic variant (`text-prompt.txt`).
6. Run checklist; adjust for brevity & clarity.
7. Commit with message: `add <genre>/<album>/<song>`.

## Request for Clarification
If any convention (naming, phonetic mapping scope, tag vocabulary limits) seems unclear, ask user to refine. Otherwise proceed with assumptions above.
