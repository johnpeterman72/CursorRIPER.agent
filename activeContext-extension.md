# ActiveContext.md Agent State Extension

Add this section to your existing `memory-bank/activeContext.md`:

```markdown
## 🤖 RIPER Agent State
Ω_current: Ω₁              # Current RIPER mode
Ω_session: AGT_2025_001    # Agent session ID
Ω_transitions: []          # Mode transition history
locked_by: null            # Concurrency control
lock_timestamp: null

## 🤝 Agent Handoff
handoff_from: null         # Previous mode
handoff_to: null           # Expected next mode
handoff_summary: |         # Context for next agent
  [Handoff details here]
handoff_timestamp: null

## 📊 Mode History
| Time | From | To | Trigger | Summary |
|------|------|----|---------|---------|
| -    | -    | -  | -       | -       |
```

This extension enables:
- State tracking across agent switches
- Handoff context between modes
- Session continuity
- Transition history
- Concurrency control