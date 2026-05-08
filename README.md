<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://img.shields.io/badge/coach-mastery--learning-7C3AED?style=for-the-badge&logo=claude&logoColor=white&labelColor=1a1a2e">
    <img alt="Coach" src="https://img.shields.io/badge/coach-mastery--learning-7C3AED?style=for-the-badge&logo=claude&logoColor=white&labelColor=f0f0ff">
  </picture>
</p>

<p align="center">
  <b>A Claude Code skill that teaches you any subject using Bloom's mastery learning method — the same pedagogy proven to outperform 98% of conventional instruction.</b>
</p>

<p align="center">
  <a href="https://github.com/anthropics/claude-code"><img src="https://img.shields.io/badge/Claude_Code_Skill-7C3AED?logo=claude&logoColor=white" alt="Claude Code Skill"></a>
  <a href="./LICENSE"><img src="https://img.shields.io/badge/license-MIT-green" alt="MIT License"></a>
  <img src="https://img.shields.io/badge/version-1.0.0-blue" alt="Version 1.0.0">
  <img src="https://img.shields.io/badge/subject-agnostic-success" alt="Subject Agnostic">
</p>

---

## The Problem

Most people use AI wrong for learning. They open a chat, stare at a blank input, and ask vague questions about things they don't yet understand. The result: generic answers that feel correct but don't build real understanding.

This isn't the user's fault. **You can't ask good questions about something you haven't learned yet.**

Meanwhile, the best learning method ever discovered — one-on-one tutoring with mastery learning — has been locked behind a paywall for decades. Personalized, adaptive teaching has been a privilege of the wealthy.

## The Solution

**Coach** is a Claude Code skill that flips the dynamic. Instead of waiting for you to ask questions, it acts as an active teacher:

- It asks **you** questions to gauge what you know
- It teaches in small, structured modules
- It tests your understanding after each module
- It won't advance until you reach 80%+ mastery
- It remembers everything across sessions via local files

This is Bloom's Two Sigma method, delivered at zero marginal cost.

---

## Features

| Feature | What It Does | Why It Matters |
|---------|-------------|----------------|
| **Active Teaching** | AI asks questions, you answer | No "blank page" problem for beginners |
| **Mastery Progression** | 80% threshold before advancing | No cumulative knowledge gaps |
| **Persistent State** | Progress saved to local `_learning/` files | Resume weeks later with full context |
| **Adaptive Pacing** | Accelerates or re-explains based on responses | Never bored, never lost |
| **Subject Agnostic** | Works for any topic | Use the same skill for everything |
| **Obsidian Integration** | Save notes to your vault on demand | Build a permanent knowledge base |

---

## Quick Start

```bash
# 1. Clone the skill
git clone https://github.com/yourname/coach.git
cd coach

# 2. Open Claude Code in this directory
claude

# 3. Start learning
> I want to learn Wittgenstein's logical philosophy
```

That's it. Coach activates automatically and begins the teaching session.

### Resuming Later

```bash
cd coach
claude
> Continue my philosophy study
```

Coach reads your saved progress and picks up exactly where you left off.

### Saving a Note to Obsidian

First set your vault path in `config.json`:

```json
{
  "notesDirectory": "/Users/me/my-vault"
}
```

Then during a session:

```
> Save this as a note
```

The note lands at `/Users/me/my-vault/Coach/<subject>/<filename>.md`.

---

## Installation

### Option 1: Clone (Recommended)

```bash
git clone https://github.com/yourname/coach.git
cd coach
```

### Option 2: Manual

Create the project directory and copy these files:

```
coach/
├── SKILL.md
├── references/
│   └── methodology.md
├── config.json
└── examples/
```

### Registering the Skill

Place the skill where Claude Code can discover it, or symlink it:

```bash
mkdir -p ~/my-project/.claude/skills
ln -s /path/to/coach ~/my-project/.claude/skills/coach
```

Then run `claude` in `~/my-project`.

---

## Configuration

Create `config.json` in the project root:

```json
{
  "notesDirectory": "/absolute/path/to/obsidian/vault"
}
```

| Field | Type | Description |
|-------|------|-------------|
| `notesDirectory` | string (path) | Path to your Obsidian vault root. When set, enables "save as note" during sessions. Leave empty to disable. |

---

## How a Learning Session Works

```
┌─────────────────────────────────────────────────┐
│                   START                          │
│  User: "I want to learn X"                      │
└──────────────┬──────────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────────┐
│          CHECK EXISTING STATE                    │
│  Look for _learning/<subject>/profile.md         │
│  New ↔ Create curriculum & start Module 1       │
│  Returning ↔ Load state & ask: review or continue │
└──────────────┬──────────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────────┐
│          THE TEACHING LOOP                       │
│                                                  │
│  ┌──────────┐    ┌──────────┐    ┌───────────┐  │
│  │ PRESENT  │───▶│   TEST   │───▶│ EVALUATE  │  │
│  │ concept  │    │ 2-4 Qs   │    │ score <80%│  │
│  └──────────┘    └──────────┘    └─────┬─────┘  │
│                                        │        │
│                        ┌───────────────┘        │
│                        ▼                        │
│                   ┌──────────┐                  │
│                   │ ≥80%?    │                  │
│                   │ ┌───┐ ┌──┴──┐               │
│                   │ │YES│ │ NO │               │
│                   │ └─┬─┘ └──┬──┘               │
│                   │   │      └─▶ Re-explain     │
│                   │   │         with new angle   │
│                   │   │         & re-test        │
│                   │   ▼                         │
│                   │  Next module                │
│                   └──────────────────┘          │
└─────────────────────────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────────┐
│          SESSION END                             │
│  Summarize → Save profile.md → Preview next     │
└─────────────────────────────────────────────────┘
```

### Example: A Real Session

**User:** "Teach me Wittgenstein's Tractatus."

**Coach** (creates `_learning/wittgenstein/` and begins):

> Let's start with the core idea. Wittgenstein believed that language and reality share a logical structure — he called it a "picture theory" of meaning.
>
> Here's the key claim: a proposition is a picture of reality. Just like a map represents a territory, a proposition represents a state of affairs by sharing its logical form.
>
> **Question 1:** In your own words, what does it mean for a proposition to "picture" reality?
>
> **Question 2:** If I say "The cat is on the mat," what would Wittgenstein say makes this sentence meaningful?
>
> (Answers determine whether you advance to the next module or need a different explanation.)

---

## Why This Works: Bloom's Two Sigma

In 1984, educational psychologist Benjamin Bloom published a landmark finding: students who received one-on-one tutoring with mastery learning performed **two standard deviations better** than students in conventional classrooms. The average tutored student outperformed 98% of the control group.

Bloom called this the "2 Sigma Problem" — not because tutoring was unproven, but because it was **too expensive to scale**. He spent the rest of his career searching for group instruction methods that could approach this level of effectiveness.

Two conditions make the 2 Sigma effect possible:

1. **One-on-one tutoring** — Real-time adaptation to the individual's comprehension
2. **Mastery learning** — 80-90% competency required before advancing

Coach implements both conditions through AI, at near-zero marginal cost.

See [`references/methodology.md`](references/methodology.md) for the full research background.

---

## Comparison

| Aspect | Coach | Traditional Chat | Textbook | Tutor |
|--------|-------|-----------------|----------|-------|
| **Active teaching** | ✅ AI drives | ❌ You drive | ❌ You drive | ✅ Teacher drives |
| **Mastery check** | ✅ Built-in | ❌ None | ❌ None | ✅ Implicit |
| **Persistent progress** | ✅ Local files | ❌ Lost on close | ✅ Bookmark | ✅ Notes |
| **Cost** | Free | Free | $20-100 | $50-200/hr |
| **Any subject** | ✅ Yes | ✅ Yes | ❌ Per book | ❌ Per tutor |
| **Adaptive pacing** | ✅ Yes | ❌ No | ❌ Fixed | ✅ Yes |

---

## Project Structure

```
coach/
├── SKILL.md                 # Core skill — the teaching engine
├── references/
│   └── methodology.md       # Bloom research background
├── config.json              # Your settings (vault path, etc.)
├── examples/                # Example session flows
├── _learning/               # Auto-created — your progress data
│   └── <subject>/
│       ├── profile.md       # Mastery state, session history
│       ├── module-01-*.md   # Learning modules
│       └── ...
└── README.md                # This file
```

---

## FAQ

**Q: Do I need to know how to use Claude Code?**  
A: Basic familiarity with the CLI helps, but Coach handles the teaching flow — you just answer questions.

**Q: What subjects can I learn?**  
A: Any subject. Programming, philosophy, science, languages, mathematics, history, creative skills. The skill adapts its teaching style per domain.

**Q: Does this work without the Obsidian vault config?**  
A: Yes. The note-saving feature is optional. Without it, Coach still works fully for teaching.

**Q: What if I'm stuck on a concept?**  
A: Coach tries alternative explanations (different metaphors, examples, angles). After 3 attempts, it tags the concept for review and moves on — no endless loops.

**Q: Where is my learning data stored?**  
A: In the `_learning/` directory inside this project. Plain Markdown files — yours to read, edit, back up, or version control.

**Q: Can I interrupt a session and come back later?**  
A: Yes. Say "stop here" or "continue next time." Progress is saved immediately. Next session, say "continue learning X" and Coach restores full context.

---

## Limitations

- **No multimedia** — Coach teaches through text. Some subjects benefit from diagrams, video, or hands-on practice.
- **No spaced repetition (yet)** — Coach tracks what needs review but doesn't schedule future review sessions automatically.
- **Teacher quality depends on the model** — The underlying LLM's capabilities affect explanation quality.
- **Not a replacement for practice** — Understanding concepts and building skills (playing an instrument, coding, writing) are different; Coach handles the conceptual side well but can't replace deliberate practice.

---

## License

MIT

---

## Acknowledgments

- Benjamin Bloom (1913–1999) for the research that made this approach possible
- The Claude Code team for building the skill system
