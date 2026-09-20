# Obsidian Librarian Configuration

Configure your installed copy before archiving. Never commit your personal vault path to the public repository.

```yaml
vault_path: "SET_ME"
library_folder: "Library/Links"
note_language: "ru"
tag_language: "en"
max_tags: 8
create_related_section: true
update_existing_notes: true
```

- Set `vault_path` to your own absolute Obsidian vault path. With `SET_ME`, the worker must stop instead of guessing.
- `library_folder` is relative to the vault root; originals are preserved under its `Attachments/` subfolder.
- Change `note_language` to your preferred prose language. The included template uses Russian section headings; translate those headings if desired.
- `tag_language` is a preference; established technical names need not be translated.
- Update existing notes only when source identity is confirmed, including cross-format duplicates. A matching title alone is insufficient.
- Never overwrite unrelated notes. Preserve annotations and source provenance.
- Keep API credentials in the environment or your secret manager, never in this file.
