# Hive Mind

A collaborative intelligence system where AI agents serve as team members, not just tools. Each agent maintains domain-specific knowledge and participates actively in team workflows.

## Philosophy

**Agents are team members, not tools.**

Traditional approach:
```
Team works → Knowledge accumulates → Someone updates docs → Agent answers questions
```

Hive Mind approach:
```
Team works → Agent is present → Knowledge updates automatically → Agent contributes proactively
```

## Structure

```
hive-mind/
├── README.md           # This file
├── CLAUDE.md           # AI assistant guidance
├── topics.md           # Index of domain-specific repos
├── channels.md         # Communication channels to monitor
├── waiting.md          # Blocked items by person
├── PLAN.md             # Future enhancements
├── new_entry*          # Entry creation script
├── entries/            # Cross-topic dated entries
├── people/             # Team member profiles
├── summaries/          # Per-topic summaries
└── .claude/skills/     # External tool integrations
```

## Quick Start

### Create an Entry

```bash
./new_entry meeting-notes "Team Standup Notes"
./new_entry decision "Architecture Decision"
```

### Query Domain Knowledge

```bash
cd ~/git/domain-repo
claude -p "What do we know about X?"
claude -c -p "How does that relate to Y?"
```

### Monitor Channels

```bash
# Check today's activity
uvx --from "git+https://github.com/shanemcd/slacker" slacker search "in:#team-channel today"
```

## Core Concepts

### Topics

Each major knowledge domain gets its own shared-understanding repository. See `topics.md` for the index.

### Entries

Chronologically organized knowledge capture in `entries/YYYY/MM/DD/`. Use `new_entry` to create.

### Skills

External tool integrations via `uvx`:
- `gcmd` - Google Drive (export docs, manage files)
- `jirahhh` - Jira (issues with wiki markup)
- `slacker` - Slack (search, reminders, messages)
- `gcalcli` - Google Calendar
- `browser-fetch` - Authenticated web content
- `curl` - Web fetching

### Summaries

Living summaries per topic in `summaries/`. Updated as understanding evolves.

### People

Team member profiles in `people/`. Useful for context on collaborators.

## Usage Patterns

### Daily Workflow

1. Check `waiting.md` for blocked items
2. Review relevant `channels.md` activity
3. Create entries for decisions/meetings
4. Update `summaries/` as understanding evolves

### Meeting Flow

1. Pre-meeting: Query relevant topic repos
2. During: Take notes (or use Iris dictation)
3. Post-meeting: Create entry with decisions/action items
4. Update `waiting.md` with new blocked items

### Cross-Topic Research

```bash
# Query multiple domains
for repo in ~/git/topic-*; do
    echo "=== $repo ==="
    (cd $repo && claude -p "What do we know about X?")
done
```

## Agent Integration

Agents can be integrated as team members via:

- **Slack access** - Monitor channels, respond to mentions
- **Meeting attendance** - Dictation mode captures context
- **Proactive updates** - Create entries automatically
- **Function calling** - Take actions (create tickets, schedule, etc.)

See `PLAN.md` for the roadmap.
