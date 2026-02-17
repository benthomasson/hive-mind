# Entries

Chronologically organized knowledge capture.

## Structure

```
entries/
└── YYYY/
    └── MM/
        └── DD/
            ├── meeting-notes.md
            ├── decision.md
            └── ...
```

## Creating Entries

Use the `new_entry` script:

```bash
# Basic usage
./new_entry meeting-notes

# With title
./new_entry architecture-decision "Architecture Decision"

# Open in editor after creation
./new_entry --edit standup "Daily Standup"
```

## Entry Template

```markdown
# Title

**Date:** YYYY-MM-DD
**Time:** HH:MM

## Overview
High-level summary of this entry.

## Details
Comprehensive information.

## Next Steps
- [ ] Action item 1
- [ ] Action item 2

## Related
- [Related Entry](../other-date/entry.md)
- [External Resource](https://example.com)
```

## Best Practices

1. **One topic per entry** - Create separate entries for different topics
2. **Use descriptive filenames** - `architecture-decision.md` not `notes.md`
3. **Link related entries** - Build a knowledge graph
4. **Track action items** - Use checkboxes in Next Steps
5. **Update as needed** - Entries are living documents
