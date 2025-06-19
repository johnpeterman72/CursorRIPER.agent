# 🎯 RIPER Agent Quick Reference Card

## Mode Commands
```
/r    → Ω₁ RESEARCH (gather info)
/i    → Ω₂ INNOVATE (propose ideas)  
/p    → Ω₃ PLAN (create specs)
/e    → Ω₄ EXECUTE (implement)
/rev  → Ω₅ REVIEW (validate)

/handoff → Complete mode & transition
```

## Mode Permissions
```
Ω₁: ✓READ ✗SUGGEST
Ω₂: ✓IDEAS ✗CODE
Ω₃: ✓SPEC ✗BUILD  
Ω₄: ✓EXACT ✗DEVIATE
Ω₅: ✓CHECK ✗FIX
```

## State Location
Current mode: `@memory-bank/activeContext.md → Ω_current`

## Quick Checks
- Am I in the right mode? Check σ₄
- Can I transition? Check handoff_from
- What's my session? Check Ω_session

## Symbols
- Ω = Mode
- σ = Memory 
- Γ = Context
- Ψ = Protection
- ✓/✗ = Allow/Deny

## Flow
RESEARCH → INNOVATE → PLAN → EXECUTE → REVIEW
    ↑__________________________|
           (if deviations)