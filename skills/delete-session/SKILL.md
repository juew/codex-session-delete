---
name: delete-session
description: Permanently delete a local Codex conversation by exact session ID. Use when the user provides a Codex session ID and asks to delete, purge, remove, or clean up that conversation from ~/.codex/sessions.
---

# Delete Codex Session

Use this skill when the user wants to permanently remove a local Codex conversation file.

## Workflow

1. Ask for the session ID if the user did not provide one.
2. Run the bundled script from this plugin directory with the exact ID:

```bash
python3 scripts/delete_codex_session.py <session-id>
```

3. Report the deleted file path from the script output.
4. Tell the user to restart Codex if the conversation still appears in the UI.

## Safety Rules

- Only delete files found under `~/.codex/sessions`.
- Require an exact session ID match against the JSONL filename stem.
- If multiple exact matches are found, stop and report the conflict instead of deleting.
- Do not delete directories.
- Do not use wildcards, partial IDs, or fuzzy matching for deletion.

## Useful Commands

Dry run:

```bash
python3 scripts/delete_codex_session.py <session-id> --dry-run
```

List the resolved sessions root:

```bash
python3 scripts/delete_codex_session.py --sessions-root
```
