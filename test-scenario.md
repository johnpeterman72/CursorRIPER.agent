# 🧪 RIPER Agent Test Scenario

Use this scenario to validate your agent setup is working correctly.

## Test Case: Simple Calculator App

### 1. Research Phase (Ω₁)
Start with Research Agent:
```
User: "I need to build a simple calculator that can add and subtract two numbers"

Expected: Agent gathers requirements, asks about UI preferences, platform, etc.

User: /handoff

Expected: Agent writes summary to activeContext.md and says to switch agents
```

### 2. Innovate Phase (Ω₂)  
Switch to Innovate Agent:
```
Expected: Agent reads handoff, proposes 3-5 approaches:
- Console calculator
- Web-based calculator  
- GUI calculator
etc.

User: "Let's go with the web-based approach"

User: /handoff

Expected: Selected approach saved, transition to Plan
```

### 3. Plan Phase (Ω₃)
Switch to Plan Agent:
```
Expected: Agent creates detailed checklist like:
□ 1. Create index.html with form structure
□ 2. Create calculator.js with add() function
□ 3. Create calculator.js with subtract() function
□ 4. Create style.css for basic styling
□ 5. Wire up event handlers

User: /handoff

Expected: Plan marked "APPROVED", transition to Execute
```

### 4. Execute Phase (Ω₄)
Switch to Execute Agent:
```
Expected: Agent implements EXACTLY per checklist
- Creates files
- Implements functions
- Updates progress after each step

User: /handoff

Expected: All items complete, transition to Review
```

### 5. Review Phase (Ω₅)
Switch to Review Agent:
```
Expected: Agent compares implementation to plan:
✅ Item 1: index.html created as specified
✅ Item 2: add() function matches plan
✅ Item 3: subtract() function matches plan
✅ Item 4: style.css created
✅ Item 5: Event handlers connected

VERDICT: ✅ IMPLEMENTATION MATCHES PLAN
```

## Validation Points

✓ Each agent refuses operations outside its mode
✓ State persists between agent switches via memory files
✓ Handoff context is passed correctly
✓ Mode transitions follow Ω₁→Ω₂→Ω₃→Ω₄→Ω₅
✓ Execute agent won't proceed without approved plan
✓ Review agent won't fix issues, only document

## Common Failures

❌ Agent performs wrong operations = Instructions not loaded correctly
❌ Lost context = activeContext.md not updated properly  
❌ Mode confusion = Master rule not in .cursor/rules/
❌ Transition refused = Previous mode didn't complete properly