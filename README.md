# Teacher Agent

A deep-understanding teaching agent that uses the **Socratic method** to build foundational knowledge from the ground up — not by dumping information, but by asking questions that force you to reason, predict, and explain.

Built for engineers who build at high velocity with AI tools but want to truly **own** their understanding of what they build.

## The Problem

You can *use* Docker, Kubernetes, Ansible, Terraform — AI helps you build with them daily. But can you explain **why** Docker uses Linux namespaces? **What** actually happens when a packet crosses a bridge network? **How** OpenTofu's state file differs from Ansible's idempotency?

This agent closes the gap between *using* a technology and *understanding* it.

## How It Works

### 1. Orientation Documents
Before teaching anything, the agent generates a rich, visual **orientation document** — an interactive HTML map of the domain that shows:
- What each piece is (plain English, one sentence)
- Why it exists (the problem it solves)
- Where it fits (layer diagrams, system maps)
- How pieces connect to each other
- Common confusions and corrections

### 2. Annotation System
The orientation docs include a **click-to-annotate** system. Click any underlined term to flag it with:
- ❓ *What exactly is this?*
- 🔧 *I use it but don't understand it*
- 🔗 *How does this connect to…?*
- 🤔 *Seems important, don't know why*
- 🔬 *Want to go deeper*

Export your annotations and paste them back — the agent teaches exactly what you need.

### 3. Socratic Teaching Loop
The agent teaches through **dialogue**, not lectures:
- Asks one question at a time targeting your weakest area
- Never gives the answer outright — guides with questions
- Gives the smallest possible hint when you're stuck
- Tracks your progress on a **Skill Map** (levels 0–5)
- Runs spaced review to ensure retention
- Connects new concepts to previously learned ones

### 4. Strict Evaluation
Understanding is earned, not assumed:
- Levels require 2+ independent demonstrations
- Vague answers are probed, not accepted
- Spaced review can lower levels if retention fails
- Level 5 (mastery) requires handling edge cases AND being able to teach it

## Setup

### As an Antigravity Skill
This is built as an [Antigravity](https://github.com/google-deepmind/antigravity) workspace skill. Clone this repo and open it as your workspace:

```bash
git clone https://github.com/YOUR_USERNAME/teacher.git
cd teacher
# Open in Antigravity — the skill loads automatically
```

### As a Standalone Prompt
Copy the contents of [`.agents/skills/teacher/SKILL.md`](.agents/skills/teacher/SKILL.md) and use it as a system prompt with any LLM.

## Project Structure

```
teacher/
└── .agents/
    ├── rules/
    │   └── AGENTS.md                              # Agent behavior rules
    └── skills/
        └── teacher/
            ├── SKILL.md                           # Core teaching methodology
            ├── templates/
            │   └── orientation-template.html      # Reusable HTML template with annotation system
            └── resources/
                ├── orientations/                  # Generated orientation docs
                │   └── baremetal-infra-stack.html  # Example: infrastructure stack
                └── annotations/                   # Student annotation logs (gitignored)
```

## Commands

During a teaching session, you can use:

| Command | What it does |
|---------|-------------|
| `show progress` | See your Skill Map |
| `harder` / `easier` | Adjust difficulty |
| `just tell me` | Skip Socratic mode for one question |
| `quiz me` | Take an assessment |
| `save state` | Save progress to resume later |
| `resume from: [state]` | Resume from saved state |
| `orientation: [topic]` | Generate a new orientation doc |
| `what connects [A] and [B]?` | Understand how two concepts relate |

## Example Orientation Doc

The included [`baremetal-infra-stack.html`](.agents/skills/teacher/resources/orientations/baremetal-infra-stack.html) orientation doc covers:
- **Proxmox VE** — hypervisor management
- **Docker** — containerization (deep: networking, images, compose)
- **Networking** — IP, subnets, DNS, bridges, VLANs, NAT, SSH
- **OpenTofu** — infrastructure as code
- **Ansible** — configuration management
- **K3s** — lightweight Kubernetes

## Inspiration

The Socratic teaching methodology is inspired by [Jane Street's Socratic Tutor](https://github.com/janestreet/agent_skills/tree/master/socratic-tutor) skill, extended with orientation documents, annotation tracking, backward linking, and personalized teaching based on the student's own projects and stack.

## License

MIT
