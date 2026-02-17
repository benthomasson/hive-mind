# Plan

Future enhancements for the hive mind system.

## Phase 1: Automatic Updates from Meetings

### Goal
Automatically create entries from meeting transcripts without manual intervention.

### Approach

1. **Meeting Transcription Source**
   - Google Meet transcripts (land in Google Drive)
   - Iris dictation mode
   - Other transcription services

2. **Trigger Mechanism**
   - File watcher on transcript folder
   - Calendar event end hook
   - Manual invocation with transcript path

3. **Processing Pipeline**
   - Detect new transcript file
   - Use gcmd skill to export from Google Drive if needed
   - Run Claude to extract:
     - Summary
     - Action items
     - Decisions made
     - Participants
   - Create entry using `new_entry` script
   - Populate entry with extracted content

4. **Topic Routing**
   - Match meeting title/participants to topic repos in `topics.md`
   - Create entry in appropriate topic repo
   - Fall back to hive-mind entries if no match

## Phase 2: Slack Integration

### Goal
Agent monitors Slack channels and participates as a team member.

### Capabilities

1. **Read-only monitoring**
   - Listen to channels in `channels.md`
   - Extract relevant information
   - Update summaries automatically

2. **Respond when mentioned**
   - Answer questions about domain knowledge
   - Cite sources from entries

3. **Proactive contribution**
   - Surface relevant context when topics arise
   - Suggest related information

## Phase 3: Agent with Function Calling

### Goal
Agent can take actions, not just answer questions.

### Actions

- Create Jira tickets
- Schedule calendar events
- Create reminders
- Update entries
- Post to Slack channels

## Phase 4: Multi-Agent Coordination

### Goal
Multiple domain agents coordinate to answer cross-cutting questions.

### Architecture

```
Orchestrator → Route to relevant domain agents →
Parallel queries → Synthesis → Response
```

See: Project Analyze architecture for enterprise-scale reference.

## Open Questions

- How to handle recurring meetings that span multiple topics?
- Should transcripts be stored or just processed and discarded?
- What's the right granularity for topic repos?
- How do agents maintain context across sessions?
