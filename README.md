# 🎯 RIPER Agent Mode Implementation Guide

## Overview
This implementation provides two approaches for integrating RIPER discipline into Cursor's custom agents:
1. **Multi-Agent System**: 5 specialized agents (one per RIPER mode)
2. **Unified Agent**: Single agent with mode switching

Both approaches use ultra-compressed Sigma notation to minimize token usage while maintaining strict RIPER discipline.

## 🚀 Quick Start (15 minutes)

### Option A: Multi-Agent Setup

1. **Copy the master rule** to your project:
   ```
   Copy: agent-mode/riper-sigma-core.mdc
   To:   .cursor/rules/riper-sigma-core.mdc
   ```

2. **Create 5 custom agents** in Cursor (Settings > Custom Modes):

   **Agent 1: RIPER Research**
   - Name: `RIPER Research Agent`
   - Icon: 🔍
   - Tools: All Search tools + Web
   - Instructions: Copy from `agent-research.md`

   **Agent 2: RIPER Innovate**
   - Name: `RIPER Innovate Agent`
   - Icon: 💡
   - Tools: Read File, List Directory
   - Instructions: Copy from `agent-innovate.md`

   **Agent 3: RIPER Plan**
   - Name: `RIPER Plan Agent`
   - Icon: 📋
   - Tools: Read File, List Directory
   - Instructions: Copy from `agent-plan.md`

   **Agent 4: RIPER Execute**
   - Name: `RIPER Execute Agent`
   - Icon: ⚡
   - Tools: ALL tools enabled
   - Instructions: Copy from `agent-execute.md`

   **Agent 5: RIPER Review**
   - Name: `RIPER Review Agent`
   - Icon: ✅
   - Tools: Read File, Terminal
   - Instructions: Copy from `agent-review.md`

3. **Update your memory files**:
   - Add agent state section to `memory-bank/activeContext.md` (see `activeContext-extension.md`)
   - Initialize with `Ω_current: Ω₁`

### Option B: Unified Agent Setup (Simpler)

1. **Copy the master rule** (same as above)

2. **Create ONE custom agent**:
   - Name: `RIPER Framework Agent`
   - Icon: 🎯
   - Tools: ALL tools enabled
   - Instructions: Copy from `agent-unified.md`

3. **Update memory files** (same as above)

## 📖 How It Works

### The Master Rule
`riper-sigma-core.mdc` defines the entire RIPER framework in ~30 lines:
- Mode definitions and permissions
- State machine logic
- Memory protocol
- Protection levels
- Command mappings

### Agent Instructions
Each agent has minimal instructions (~20 lines) that:
- Reference the master rule with `@RIPER·Σ`
- Check current state from `σ₄` (activeContext.md)
- Enforce mode-specific permissions
- Handle handoffs to next mode

### State Management
All agents share state through memory files:
- `σ₄` (activeContext.md) tracks current mode and handoffs
- `σ₅` (progress.md) tracks completion
- Other memory files store mode-specific data

## 🎮 Usage Examples

### Multi-Agent Workflow:
```
1. Start chat with Research Agent
   User: "I need to build a user authentication system"
   Agent: "RIPER·Ω₁ Active. Let me gather requirements..."
   
2. When ready to ideate:
   User: /handoff
   Agent: "Research complete. Switch to Innovate Agent."
   
3. Open new chat with Innovate Agent
   Agent: "RIPER·Ω₂ Active. Based on research, here are 3 approaches..."
   
4. Continue through all modes...
```

### Unified Agent Workflow:
```
1. Start chat with RIPER Framework Agent
   User: "I need to build a user authentication system"
   Agent: "RIPER Agent in mode Ω₁. Gathering requirements..."
   
2. Transition modes:
   User: /i
   Agent: "Switched to Ω₂ INNOVATE. Here are 3 approaches..."
   
3. Continue with same agent through all modes...
```

## 🔧 Commands

- `/r` - Enter RESEARCH mode
- `/i` - Enter INNOVATE mode  
- `/p` - Enter PLAN mode
- `/e` - Enter EXECUTE mode
- `/rev` - Enter REVIEW mode
- `/handoff` - Complete current mode and transition

## 📊 Token Efficiency

Traditional verbose instructions: ~500-800 tokens/agent
Our Sigma implementation: ~50-100 tokens/agent
With master rule: ~20-30 tokens/agent

Total framework overhead: <200 tokens (vs 3000+ traditional)

## ⚠️ Important Notes

1. **Manual Agent Switching**: With multi-agent setup, you must manually switch between agents. Context is preserved through memory files.

2. **State Enforcement**: Agents will refuse operations outside their mode. This is intentional RIPER discipline.

3. **Memory Files Required**: Ensure your project has the standard RIPER memory structure in `memory-bank/`

4. **No Backward Transitions**: RIPER enforces forward-only flow (except Review→Plan for fixes)

## 🧪 Testing Your Setup

1. **Test State Check**:
   - Try using Execute Agent without approved plan
   - Should refuse with mode error

2. **Test Handoff**:
   - Complete research and use `/handoff`
   - Check that `activeContext.md` updates correctly
   - Verify next agent reads handoff context

3. **Test Mode Discipline**:
   - Try to write code in Research mode (should fail)
   - Try to suggest ideas in Execute mode (should fail)

## 🤔 Which Approach to Choose?

**Multi-Agent System** if you want:
- Clearest separation of concerns
- Different models per mode (e.g., cheaper model for research)
- Visual distinction between modes
- Team members using different agents

**Unified Agent** if you want:
- Simpler setup (one agent to configure)
- Continuous conversation context
- Easier mode transitions
- Less window switching

## 🐛 Troubleshooting

**"Wrong mode" errors**: Check `activeContext.md` has correct `Ω_current`

**Lost context between agents**: Ensure handoff_summary is written before switching

**Agent won't transition**: Verify previous mode completed its checklist

**Commands not recognized**: Check master rule is in `.cursor/rules/` and loaded

## 📚 Reference

### Sigma Notation Quick Guide:
- `Ω` = Mode (Ω₁=Research, Ω₂=Innovate, etc.)
- `σ` = Memory file (σ₁=brief, σ₂=patterns, etc.)
- `Γ` = Context type (Γ₁=Files, Γ₂=Folders, etc.)
- `Ψ` = Protection level (Ψ₁=Info to Ψ₆=Catastrophic)
- `✓` = Allowed operation
- `✗` = Forbidden operation

### Memory Files:
- σ₁: projectbrief.md
- σ₂: systemPatterns.md  
- σ₃: techContext.md
- σ₄: activeContext.md (STATE)
- σ₅: progress.md
- σ₆: protection.md

---

For questions or improvements, reference the main CursorRIPER Sigma documentation.