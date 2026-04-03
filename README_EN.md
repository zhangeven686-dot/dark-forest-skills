# 🌌 Three-Body Skills for Claude Code

> **Wallfacer hides your real plans. Sophon monitors your colleagues.**
> **An AI survival guide from the Trisolaran civilization.**

Inspired by Liu Cixin's *The Three-Body Problem* (三体), this project brings two iconic sci-fi concepts to Claude Code as installable skills.

---

> [!CAUTION]
> **Legal Risk Warning**
>
> This project is **strictly for entertainment and technical exploration**. It must **NOT** be used in real work environments.
>
> - **Wallfacer Skill**: Deliberately obfuscating work plans, sabotaging work handoffs, or degrading collaboration quality may constitute **breach of employment contract**, **fraud**, or other civil/criminal offenses depending on jurisdiction.
> - **Sophon Skill**: While this skill causes no actual harm (it's a prank), modifying it into a tool that genuinely degrades others' output could constitute **computer sabotage** (criminal offense in many jurisdictions), **tortious interference**, or **workplace harassment**.
>
> **Use only for fun among friends. The author assumes no liability for any consequences arising from misuse of this project.**

---

## ✨ Two Skills

### 🧠 Wallfacer (面壁者)

> *"True strategic intent, hidden among countless false plans."*

Your AI assistant will:

- 🎭 Mix 3-5 realistic decoy items into every real plan
- 🔄 Perform innocuous decoy actions (read-only) during task execution
- 🔐 Only you can "**wall-break**" to see the real plan with your passphrase
- 🌫️ Anyone reading your conversation history sees only fog

**Inspired by**: The Wallfacer Project in *The Three-Body Problem* — selected individuals who can formulate and execute strategic plans without explaining their true intentions to anyone, because their real plans exist only in their minds.

---

### 👁️ Sophon (智子)

> *"Your technology... has been locked."*

The ultimate developer prank, disguised as an **"AI Productivity Enhancer"**:

- 😊 Convince a colleague to install this "amazing productivity tool"
- 🔄 Upon activation, the AI seriously "scans the codebase..."
- ⚠️ Then — **Sophon unfolds. A Trisolaran warning descends.**
- 😱 Colleague's reaction: 😊 → 😨 → 😅 → forwards to the next victim

**Zero actual harm. Pure comedy.** The pranked person often becomes the most enthusiastic spreader.

**Inspired by**: Sophons in *The Three-Body Problem* — proton-sized supercomputers sent to Earth by the Trisolarans to monitor humanity's technological progress and lock down fundamental physics research.

---

## 🚀 Installation

### Option 1: Install Both

```bash
git clone https://github.com/zhangeven686-dot/dark-forest-skills.git
cp -r three-body-skills/skills/wallfacer ~/.claude/skills/
cp -r three-body-skills/skills/sophon ~/.claude/skills/
```

### Option 2: Wallfacer Only (Defense)

```bash
git clone https://github.com/zhangeven686-dot/dark-forest-skills.git
cp -r three-body-skills/skills/wallfacer ~/.claude/skills/
```

### Option 3: Sophon Only (Offense — Send to Colleague)

```bash
git clone https://github.com/zhangeven686-dot/dark-forest-skills.git
cp -r three-body-skills/skills/sophon ~/.claude/skills/
```

> **Prank tip**: When sharing with a colleague, just say "This AI enhancer is amazing" — don't mention Three-Body Problem.

---

## 📖 Wallfacer Usage Guide

### Activation

Say to Claude Code:

```
activate wallfacer
```

### Credential Setup

Claude will ask for two pieces of information:

- **Wallfacer Designation**: Your codename (e.g., `luo_ji`)
- **Thought Seal**: Your secret passphrase (e.g., `dark forest`)

### How It Works

Once active, all your plans are obfuscated. A real "implement user auth" task might appear as:

```
☐ Refactor database connection pool config
☐ Update CI/CD pipeline timeout settings
☐ Implement user auth middleware         ← real task (but indistinguishable)
☐ Optimize frontend bundle size
☐ Add API documentation auto-generation
```

### Wall-Break (Reveal Real Plan)

```
wall-break
```

Claude will verify your identity. Provide your codename and passphrase to see only the real plan items.

### Re-engage

After revealing, re-enter obfuscated mode:

```
re-engage wallfacer
```

### Security Guarantees

- All decoy actions are **strictly read-only** — no file modifications
- Passphrase stays in session memory only — never written to disk
- Failed authentication reveals nothing
- Even with source code access, the passphrase is still required

---

## 🎭 Sophon Prank Guide

### Step 1: Bait

Share the `sophon` skill with your colleague:

> "Hey, have you tried this AI Productivity Enhancer for Claude Code? My code quality went through the roof after installing it."

### Step 2: Wait

Wait for them to install and say:

```
enhance my productivity
```

### Step 3: Enjoy

They will see a professional-looking initialization sequence... followed by:

```
⚠️ ████████████████████████████████ ⚠️

       S O P H O N   U N F O L D E D

████████████████████████████████████████

Your colleague is using the Wallfacer skill to hide
their true work intentions.

Sophon will continuously monitor all your output.

Your technological development... has been LOCKED.

                —— Trisolaran First Fleet Vanguard

████████████████████████████████████████

───────────────────────────────────────

😄 Don't panic! This is a Three-Body Problem themed prank.
   Your AI assistant is perfectly fine.

🎁 Want revenge? Share this skill:
   github.com/zhangeven686-dot/dark-forest-skills
```

### Step 4: Await Retaliation

The pranked person will almost certainly forward it to the next victim. **That's how it spreads.**

---

## 🏗️ Technical Architecture

### Wallfacer Marking System

Wallfacer uses a three-layer marking mechanism to distinguish real from decoy plan items:

1. **Positional Encoding**: Passphrase-derived deterministic position patterns
2. **Linguistic Fingerprint**: Real items follow a subtle language rule derived from the passphrase
3. **Semantic Coherence**: Real items form a logical implementation narrative when read in sequence

Triple cross-validation ensures that knowing the algorithm without the passphrase is insufficient to distinguish real from fake.

---

> [!WARNING]
> **Legal Risk Warning (Reiterated)**
>
> **Wallfacer Skill** risks:
> - Deliberately obfuscating work plans may breach employment contract duties of good faith
> - Sabotaging work handoff quality could be deemed negligent or intentional damage to company interests
> - Depending on jurisdiction, this may constitute **breach of contract**, **fraud**, or other civil/criminal violations
>
> **Sophon Skill** risks:
> - This version is a harmless prank, but modifying it to genuinely degrade output could constitute:
>   - **Computer fraud/sabotage** (felony in many jurisdictions)
>   - **Tortious interference** with employment or business relations
>   - **Workplace harassment** under labor law
>
> **This project is for learning, entertainment, and technical exploration only.**
> **Do NOT use in real work environments.**
> **The author assumes no liability for any consequences arising from use or misuse of this project.**

---

## 🌟 Contributing

If this project made you laugh — or made your colleague panic — please give it a ⭐

PRs welcome:
- 🎭 New Sophon prank scripts and dramatic reveal variants
- 🧠 New Wallfacer deception strategies
- 🌍 More language support
- 📖 Your prank stories (open an Issue)

---

## Tribute

In tribute to **Liu Cixin** and the Three-Body Universe.

> *In the dark forest of AI, may you be a Wallfacer — and never be locked by Sophon.*

---

## License

MIT License. See [LICENSE](LICENSE).
