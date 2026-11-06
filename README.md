# UI Copy Skill

[![skills.sh](https://skills.sh/b/ilikescience/ui-copy-skill)](https://skills.sh/ilikescience/ui-copy-skill)

An agent skill that makes interface copy shorter by deleting it.

When LLMs design interfaces, they overuse copy to explain functionality. 
This skill gives the agent two tests for every line, plus follow-through that keeps cuts from coming back.

## The two tests

1. **Does the screen already say it?** Cut the line.
2. **Does it explain how the system works?** Cut that clause.

| Before                                                                                 | After                                   |
| -------------------------------------------------------------------------------------- | --------------------------------------- |
| "Type the six-digit code from your authenticator app" under **Enter your authenticator code** | _(cut)_                          |
| "We've emailed them a link to pay. The order stays on hold until payment is collected." | "Payment link sent"                    |
| "Dana opened it (1m 12s)"                                                              | "Email opened"                          |
| "Incorrect — try again"                                                                | "Incorrect"                             |

## What it covers

- Cutting lines the screen already shows, and clauses that teach the data model
- Activity feeds and audit logs as system events, not narration
- Analysis and summary panels as tiles, not prose
- Following a cut through to the state, props, and styles that only fed that line
- Keeping cuts from returning through refactors (optional copy props)
- Checking that a shortened line still has exactly one meaning, and that
  irreversible actions keep their consequence line
- A final pass that extracts every string and reads it cold

## Installation

### skills.sh

```bash
npx skills add ilikescience/ui-copy-skill
```

### Manual

```bash
# User-level (all projects)
cp -r skills/ui-copy ~/.claude/skills/ui-copy

# Project-level
cp -r skills/ui-copy .claude/skills/ui-copy
```

## Usage

The skill activates when the agent is writing or reviewing interface text. You
can also invoke it directly:

```
/ui-copy src/settings/TwoFactorSetup.tsx
"Review the copy on this onboarding flow"
"This empty state feels wordy, tighten it"
"Make the activity feed read like a real product"
```

## License

[MIT](LICENSE)
