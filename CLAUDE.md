# CLAUDE.md

Central hub for managing multiple domain-specific knowledge repositories.

## Purpose

This is the meta-repository that indexes all topic-specific shared understanding repos. It provides:
- Cross-topic notes and personal entries
- Team member profiles
- Blocked item tracking
- Communication channel monitoring

## Structure

- `topics.md` - Index of all domain repositories
- `channels.md` - Slack/communication channels to monitor
- `waiting.md` - Items blocked on specific people
- `summaries/` - Living summaries per topic
- `people/` - Team member profiles
- `entries/` - Cross-topic dated entries

## Commands

```bash
# Create a new entry
./new_entry thinking "Cross-topic Thoughts"
./new_entry decision "Architecture Decision"

# List all topics
cat topics.md

# Check blocked items
cat waiting.md

# View topic summary
cat summaries/topic-name.md
```

## Workflow

1. Add new topic repos to `topics.md` as they're created
2. Use `entries/` for thoughts that span multiple topics
3. Track blocked items in `waiting.md` by person
4. Monitor channels listed in `channels.md`
5. Keep `summaries/` updated as understanding evolves

## Skills Available

External tool integrations via `uvx`:

### Google Drive (gcmd)
```bash
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd export "DOC_URL" -o /tmp/
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list -q "search term"
```

### Jira (jirahhh)
```bash
uvx --from "git+https://github.com/shanemcd/jirahhh" jirahhh search "keywords"
uvx --from "git+https://github.com/shanemcd/jirahhh" jirahhh create --project PROJ --type Story --summary "Title"
```

### Slack (slacker)
```bash
uvx --from "git+https://github.com/shanemcd/slacker" slacker search "query"
uvx --from "git+https://github.com/shanemcd/slacker" slacker reminder create "15 minutes" "Follow up"
```

### Google Calendar (gcalcli)
```bash
uvx --from gcalcli gcalcli agenda
uvx --from gcalcli gcalcli add --title "Meeting" --when "tomorrow 2pm" --duration 30
```

## Slack Channel Monitoring

Use `slacker` to search for messages in monitored channels (see `channels.md`):

```bash
# Search a channel for today's messages
uvx --from "git+https://github.com/shanemcd/slacker" slacker -o json api --workspace search.messages \
  --params '{"query": "in:#channel-name on:2026-02-17", "count": 20}'

# Search with date range
uvx --from "git+https://github.com/shanemcd/slacker" slacker -o json api --workspace search.messages \
  --params '{"query": "in:#channel-name after:2026-02-01", "count": 20}'
```

## Entry Template

Entries follow a standardized structure:

```markdown
# Title

**Date:** YYYY-MM-DD
**Time:** HH:MM

## Overview
High-level summary

## Details
Comprehensive information

## Next Steps
Action items

## Related
Links to related entries or resources
```

## Agent as Team Member

This system is designed for agents to be team members, not just tools:

- **Present in information flow** - Slack access, meeting attendance
- **Self-updating knowledge** - Entries created from transcripts, threads
- **Proactive contribution** - Surface relevant context, suggest actions
- **Function calling** - Create tickets, schedule meetings, update docs
