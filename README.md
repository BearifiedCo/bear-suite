# Bear Suite

**The intelligent AI collaboration toolkit for Claude Code**

*Two perspectives are better than one.*

**By [BearifiedCo](https://bearified.co)** | MIT License

---

## What is Bear Suite?

Bear Suite is a collection of Claude Code plugins that enhance AI-assisted development through collaboration and human-AI communication. Built on the philosophy that **two perspectives are better than one**, Bear Suite combines real-time pair programming with intelligent voice escalation.

```
┌──────────────────────────────────────────────────────────────────┐
│                          BEAR SUITE                              │
│                                                                  │
│  ┌─────────────┐                           ┌─────────────┐      │
│  │  Bear Pair  │◀─────── escalates ───────▶│  Bear Call  │      │
│  │  (AI + AI)  │                           │  (AI → Human)│      │
│  └─────────────┘                           └─────────────┘      │
│        │                                          │              │
│        │ real-time review                         │ voice calls  │
│        ▼                                          ▼              │
│  ┌───────────────────────────────────────────────────────┐      │
│  │                    YOUR CODEBASE                       │      │
│  └───────────────────────────────────────────────────────┘      │
└──────────────────────────────────────────────────────────────────┘
```

---

## The Plugins

### Bear Pair — Real-time dual Claude orchestration

Two Claude instances working in parallel: **Driver** writes code, **Navigator** reviews in real-time. Errors are caught as they're written, not after.

**Key Features:**
- Real-time code review as you work
- Driver/Navigator pattern from pair programming
- File-based IPC for seamless communication
- tmux session orchestration

**Commands:**
- `/bear-pair <task>` — Start a pair programming session
- `/bear-status` — Check session status
- `/bear-stop` — End session
- `/bear-escalate` — Navigator escalates to human via Bear Call

[**→ Bear Pair Documentation**](https://github.com/BearifiedCo/bear-pair)

---

### Bear Call — Voice escalation for AI agents

When Claude needs immediate human attention, Bear Call makes it happen with a phone call. Production down? Security issue? Bear's calling.

**Key Features:**
- ElevenLabs AI voice synthesis (premium quality)
- Twilio telephony (production-grade)
- 4 urgency levels (critical/high/normal/low)
- Business hours awareness
- Automatic retry for critical calls

**Commands:**
- `/bear-call <reason> --urgency <level>` — Make a voice call
- `/bear-call-test` — Test the system
- `/bear-call-history` — View call history
- `/bear-call-spawn-pair` — Start Bear Pair from a call

[**→ Bear Call Documentation**](https://github.com/BearifiedCo/bear-call)

---

## Installation

### Install Both Plugins

```bash
# Clone both plugins
git clone https://github.com/BearifiedCo/bear-pair.git ~/.claude/plugins/bear-pair
git clone https://github.com/BearifiedCo/bear-call.git ~/.claude/plugins/bear-call

# Use with Claude Code
claude --plugin-dir ~/.claude/plugins/bear-pair --plugin-dir ~/.claude/plugins/bear-call
```

### Individual Installation

Install plugins separately based on your needs:

```bash
# Bear Pair only (pair programming)
git clone https://github.com/BearifiedCo/bear-pair.git

# Bear Call only (voice escalation)
git clone https://github.com/BearifiedCo/bear-call.git
```

---

## How They Work Together

The real power of Bear Suite emerges when both plugins work together:

```
┌─────────────────────────────────────────────────────────────────┐
│                    BEAR SUITE WORKFLOW                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   1. Human starts Bear Pair session                             │
│      └─▶ /bear-pair "Implement payment flow"                    │
│                                                                 │
│   2. Driver + Navigator work together                           │
│      └─▶ Driver codes, Navigator reviews in real-time           │
│                                                                 │
│   3. Navigator catches critical issue                           │
│      └─▶ Security vulnerability in auth logic                   │
│                                                                 │
│   4. Navigator escalates via Bear Call                          │
│      └─▶ /bear-escalate "Security vuln" --urgency critical      │
│                                                                 │
│   5. Human's phone rings                                        │
│      └─▶ "Bear calling: Security vulnerability detected..."     │
│                                                                 │
│   6. Human provides guidance                                    │
│      └─▶ "Use the sanitization library, not manual regex"       │
│                                                                 │
│   7. Bears continue with human input                            │
│      └─▶ Driver implements fix, Navigator validates             │
│                                                                 │
│   8. Task completes with human-AI collaboration                 │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Philosophy

### Two Perspectives Are Better Than One

Just as human pair programmers catch more bugs and produce better code through continuous review, Bear Suite brings this proven methodology to AI-assisted development.

**Bear Pair** implements the AI-AI collaboration layer—two Claude instances with complementary roles ensuring real-time quality.

**Bear Call** implements the AI-Human escalation layer—ensuring humans stay in the loop for critical decisions without being overwhelmed by noise.

Together, they create a **tiered collaboration system**:
1. **AI-AI** handles routine review (Bear Pair)
2. **AI-Human** handles exceptional cases (Bear Call)
3. **Human** stays productive, not interrupted by everything

---

## Requirements

### Bear Pair
- macOS (darwin)
- tmux
- Claude Code

### Bear Call
- macOS/Linux
- Node.js
- Claude Code
- Configured voice-calling backend (ElevenLabs + Twilio)

---

## Roadmap

### Bear Pair
- [ ] Cross-machine mode (Tailscale)
- [ ] Web dashboard for session monitoring
- [ ] Custom persona configurations

### Bear Call
- [ ] Two-way conversation support
- [ ] SMS fallback for low urgency
- [ ] Multi-recipient calls
- [ ] Call transcription

### Bear Suite
- [ ] Unified configuration
- [ ] Bear Slack (async notifications)
- [ ] Bear Dashboard (central observability)

---

## Credits

**[BearifiedCo](https://bearified.co)** — Making AI development friendlier, one bear at a time.

**Inspired by:**
- [Ralph Wiggum Technique](https://ghuntley.com/ralph/) by Geoffrey Huntley
- Traditional pair programming practices
- The belief that two perspectives are better than one

---

## License

MIT License — Free to use, modify, and distribute.

---

*"Two bears are smarter than one. Let's collaborate!"*
