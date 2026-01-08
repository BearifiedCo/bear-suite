# Bear Suite Guide to AI Pair Programming

**Inspired by:** Geoffrey Huntley's Ralph Wiggum technique
**Reference:** Ryan Carson's step-by-step implementation guide

---

## Philosophy

Two perspectives are better than one.

This applies to code review, architecture decisions, and AI-assisted development. Bear Suite brings this philosophy to your terminal with tools designed for iterative, collaborative AI programming.

## The Tools

### Bear Pair
Real-time dual Claude orchestration in synchronized tmux panes.

- **Two Claude instances** working simultaneously
- **One codes, one reviews** - or both tackle different aspects
- **Synchronized context** through shared files and git history
- **Zero context switching** - everything in your terminal

### Bear Call
Voice-first AI interaction when typing feels like friction.

- **Speak your intent**, get code
- **Natural conversation** flow for complex explanations
- **Hands-free coding** during whiteboard sessions
- **Quick captures** for ideas and TODOs

## When to Use Bear Suite

### Good For

- **Iterative development** - Building features incrementally
- **Code review loops** - One instance writes, one reviews
- **Complex refactors** - Multiple perspectives catch edge cases
- **Learning new codebases** - Voice queries while reading
- **Pair programming solo** - Two AI perspectives, one developer

### Not Good For

- **One-shot tasks** - Use single Claude instance instead
- **Simple edits** - Overhead not worth it
- **Security-critical code** - Requires human review
- **Production debugging** - Use targeted debugging tools

## Ralph Integration

Bear Suite works beautifully with Ralph Wiggum loops.

### The Pattern

```bash
# ralph.sh with Bear Pair
while :; do
  cat prompt.md | bear-pair --sync
done
```

Each iteration:
1. Both Claude instances receive the prompt
2. Instance A implements
3. Instance B reviews
4. Changes commit to git
5. Next iteration sees previous work
6. Learnings compound

### Memory Persistence

Ralph maintains context through:
- **Git commits** - Code history
- **progress.txt** - Session learnings
- **prd.json** - Task status
- **File changes** - Work-in-progress

Bear Suite adds:
- **Synchronized tmux panes** - Visual context
- **Shared clipboard** - Quick transfers
- **Dual perspectives** - Catch more issues

## File Structure

```
your-project/
├── scripts/ralph/
│   ├── ralph.sh           # Loop runner
│   ├── prompt.md          # Task instructions
│   ├── prd.json           # User stories
│   └── progress.txt       # Learnings
└── .bear/
    ├── pair-config.yml    # Bear Pair settings
    └── call-config.yml    # Bear Call settings
```

## Quick Start

### Bear Pair

```bash
# Install
brew tap bearifiedco/bear-suite
brew install bear-pair

# Start dual Claude session
bear-pair start

# With specific task
bear-pair start --task "Refactor auth module"
```

### Bear Call

```bash
# Install
brew install bear-call

# Start voice session
bear-call

# With context file
bear-call --context src/auth/
```

### Ralph + Bear Pair

```bash
# Clone the setup
git clone https://github.com/BearifiedCo/bear-suite-ralph-template

# Configure your task
vim scripts/ralph/prompt.md
vim scripts/ralph/prd.json

# Run
./scripts/ralph/ralph.sh 10  # 10 iterations max
```

## Critical Success Factors

### 1. Small Stories

Must fit in one context window.

| Too Big | Right Size |
|---------|-----------|
| Build entire auth system | Add login form |
| Refactor all tests | Add validation for email field |
| Implement API | Add single endpoint |

### 2. Fast Feedback

Bear Pair needs quick validation:

```bash
# In prompt.md
After each change:
1. Run `npm run typecheck`
2. Run `npm test`
3. If passing, commit
4. If failing, fix before continuing
```

### 3. Explicit Criteria

| Vague | Explicit |
|-------|----------|
| Users can log in | Email/password fields present |
|  | Email format validates |
|  | Error shows on failure |
|  | typecheck passes |

### 4. Dual Perspectives

Use both Claude instances effectively:

```
Instance A (Left pane):
- Implements the feature
- Writes the code
- Runs tests

Instance B (Right pane):
- Reviews changes in real-time
- Suggests improvements
- Catches edge cases
```

## prd.json Format

```json
{
  "branchName": "feature/user-auth",
  "userStories": [
    {
      "id": "US-001",
      "title": "Add login form",
      "acceptanceCriteria": [
        "Email field with validation",
        "Password field with masking",
        "Submit button disabled until valid",
        "typecheck passes",
        "tests pass"
      ],
      "priority": 1,
      "passes": false,
      "notes": ""
    },
    {
      "id": "US-002",
      "title": "Add form submission",
      "acceptanceCriteria": [
        "Calls auth API on submit",
        "Shows loading state",
        "Handles success redirect",
        "Handles error display",
        "typecheck passes"
      ],
      "priority": 2,
      "passes": false,
      "notes": ""
    }
  ]
}
```

## prompt.md Template

```markdown
# Bear Pair Instructions

## Context
You are running in Bear Pair mode with a synchronized partner instance.

## Your Task

1. Read `scripts/ralph/prd.json` for stories
2. Read `scripts/ralph/progress.txt` for learnings
3. Check current branch matches prd.json branchName
4. Pick highest priority story where `passes: false`
5. Implement that ONE story
6. Run typecheck and tests
7. If passing, commit: `feat: [ID] - [Title]`
8. Update prd.json: `passes: true`
9. Append learnings to progress.txt

## Coordination

- Left pane: Implementation
- Right pane: Review and suggestions
- Communicate via comments in code
- Both must agree before committing

## Stop Condition

If ALL stories pass, reply:
<promise>COMPLETE</promise>

Otherwise, end normally for next iteration.
```

## progress.txt Format

```
=== Session 2026-01-08 ===

Story US-001:
- Used shadcn/ui Input component for consistency
- Email regex: /^[^\s@]+@[^\s@]+\.[^\s@]+$/
- Form state managed with react-hook-form

Story US-002:
- Auth endpoint at /api/auth/login
- Used fetch with credentials: 'include'
- Error handling: 401 = invalid, 500 = server error

Codebase Patterns:
- Components in src/components/
- API routes in src/app/api/
- Validation schemas in src/lib/validations/
```

## Learnings Compound

By story 10, Bear Pair knows:
- Codebase patterns from stories 1-9
- Common pitfalls and solutions
- Test patterns that work
- Preferred libraries and approaches

Two places for learnings:
- **progress.txt** - Session memory for Ralph iterations
- **CLAUDE.md** - Permanent docs for future sessions

## Tips

### For Bear Pair

1. **Split responsibilities clearly** - Don't have both instances doing the same thing
2. **Use the right pane for review** - Catches issues early
3. **Commit often** - Small, atomic commits
4. **Trust but verify** - Run tests even when confident

### For Bear Call

1. **Be specific** - "Add validation for email field" not "fix the form"
2. **Provide context** - "In the login component"
3. **Iterate verbally** - Talk through the problem
4. **Use for planning** - Voice is great for architecture discussions

### For Ralph Integration

1. **Keep iterations small** - 2-5 minutes each
2. **Watch the loop** - Check progress periodically
3. **Trust the process** - Learnings compound
4. **Know when to stop** - Some tasks need human judgment

## Resources

- **Bear Suite Homepage**: [bearifiedco.github.io/bear-suite](https://bearifiedco.github.io/bear-suite)
- **Bear Pair Repo**: [github.com/BearifiedCo/bear-pair](https://github.com/BearifiedCo/bear-pair)
- **Bear Call Repo**: [github.com/BearifiedCo/bear-call](https://github.com/BearifiedCo/bear-call)
- **Ralph Wiggum Original**: [ghuntley.com/ralph](https://ghuntley.com/ralph)
- **Ryan Carson's Guide**: [@ryancarson on X](https://x.com/ryancarson)

---

*Two perspectives are better than one. Ship with Bear Suite.*
