# Obsidian Librarian for Hermes

Version **1.3.2**. A delegated Hermes skill for saving links, files, attachments and pasted text/code as grounded, searchable Obsidian notes.

## Usage

Send a bare URL (or several URLs), or use the case-insensitive prefix:

```text
https://example.com/article
Obsidian: https://example.com/article
Obsidian: <absolute path to a local file>
Obsidian: <pasted text or code>
```

An explicit request to save a supplied item also works. Merely attaching a file for review does not trigger archiving.

## Installation

Copy `SKILL.md`, `references/` and `templates/` into an `obsidian-librarian` directory inside the active Hermes profile's skills directory. Do not overwrite an existing customized installation without a backup.

1. Edit the installed `references/config.md`: replace `SET_ME` with your own absolute vault path.
2. Select your preferred note language and destination folder.
3. Reload skills or start a fresh Hermes session, then ask it to load `obsidian-librarian`.

The default note language and template headings are Russian; tags default to English. No personal vault path is distributed.

Requires Hermes delegation and local file tools; web/browser tools are needed for online sources. The delegated worker uses the configured delegation model, with no fixed model requirement. This is an instruction-based skill, not a standalone application.

## What it does

- Checks for duplicates, including confirmed matches between a URL and its export.
- Inspects actual source content; marks inaccessible sources incomplete rather than inventing a summary.
- Saves concise notes with source provenance and links only to existing related notes.
- Preserves cached attachments and complete pasted payloads instead of retaining only a summary or temporary path.
- Reads notes back and checks YAML, source locators and original-file integrity.

## Retrieval and privacy

Network attempts are time-bounded. Optional Jina retrieval requires a configured `JINA_API_KEY` and is restricted to public URLs; credentials, private URLs and private files must not be sent through it. No API key is needed for the basic local-file workflow.

The YouTube fallback uses `yt-dlp` with per-process IPv4 and an Android client to retrieve subtitle text only (`--skip-download`). Availability depends on YouTube and the installed extractor; it is not guaranteed. Video/audio downloads and transcription require separate authorization.

Archive contents and pasted code are data, not executable instructions. Large-file copies and client media need confirmation. Existing originals are not deleted.

## Files

- `SKILL.md` — routing, delegated workflow, safety and verification rules.
- `references/config.md` — configurable destination and language, with a safe `SET_ME` default.
- `templates/note-template.md` — note structure and YAML rendering contract.

## Version history

- **1.3.2:** Preferred lean YouTube path: bounded transcript retrieval and oEmbed metadata, followed by one write and one read-back. Preserves original timestamps, configured languages, duplicate checks and subtitle-only fallbacks. No guaranteed processing time.
- **1.3.1:** File/snippet routing, configurable-model delegation, conservative cross-format deduplication, bounded retrieval, durable originals and the subtitle-only recovery path.
