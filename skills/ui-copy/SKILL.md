---
name: ui-copy
description: Review and edit UI copy by deleting and simplifying it. Use when writing or reviewing interface text such as labels, helper text, hints, empty states, confirmations, error messages, activity feeds, timelines, and summary panels, or when an AI-generated UI explains itself in narrative prose instead of terse product copy.
license: MIT
argument-hint: <file or component being built>
---

# UI Copy

When LLMs design interfaces, they overuse copy to explain functionality. They
reach for narrative prose where terse UI copy would do.

## Two tests

1. **Does the screen already say it?** Cut the line.
2. **Does it explain how the system works?** Cut that clause.

## Cut the line

| Kind                                               | Example                                                                                       | Why                                                       |
| -------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| Explains a rule the layout can demonstrate         | "Guests only ever see the project code, never its internal name."                             | Put the code under every name and the sentence is redundant |
| **Restates the screen's own title**                | "Type the six-digit code from your authenticator app" under **Enter your authenticator code** | The title said it, and the six cells said "six-digit"     |
| Restates a value already on screen                 | "24 cans" under a Quantity of 4, next to a product that says "6-pack"                         | The reader can see both inputs                            |
| **Repeats the section header**                     | A row labelled "Turn off two-step verification" under a **TURN OFF** header                   | One of the two is redundant, usually the header           |
| **Prefixes a value the field label already names** | `Key: 4F2K 9Q1D 7MX3 T8VZ` inside a field labelled **Setup key**                              | The prefix and the label say the same thing               |
| States a constraint that isn't being violated      | "Between 10 and 250 units"                                                                    | The error state says it at the moment it matters          |
| Narrates an obvious control                        | "Click Save to save your changes"                                                             | The button says Save                                      |
| Labels an empty field that says nothing            | A "Discount $0" row on an order with no discount                                              | A zero row is not information                             |

## Cut the explanation

A line can carry real information and still be twice as long as it needs to be.

| Too long                                                                                                         | Tight                                                         |
| ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------- |
| "The Denver office can't receive shipments yet — a shipment needs a street address, a ZIP code and a phone number." | "Needs a street address, ZIP, and phone" + a link to settings |
| "We've emailed them a link to pay. The order stays on hold until payment is collected."                          | "Payment link sent"                                           |
| "Google is your only way to sign in. Add a password before disconnecting it."                                    | "Add a password before you can disconnect Google."            |
| "Incorrect — try again"                                                                                          | "Incorrect"                                                   |
| "On — protecting sign-ins on new devices."                                                                       | Cut. A page whose last row is "Turn off" is evidently on      |
| "Enter the code we sent to name@example.com"                                                                     | "Sent to name@example.com" (the cells say "enter a code")     |

**The tell is an em-dash or a second sentence.** Write the line, delete from that
punctuation onward, and check whether anything was lost. In practice, nearly
every overlong line has this shape.

Keep the fact. "Needs a phone number" still stops someone shipping into a dead
end; "a shipment needs…" was teaching them the data model.

## Logs and timelines are events, not narration

A feed, timeline, or audit log shows what the system recorded, in the system's
own vocabulary. If a line could not have been written by the system at the
moment it happened, it's narration.

| Narration                                                   | Event                                                  |
| ----------------------------------------------------------- | ------------------------------------------------------ |
| "Dana opened it (1m 12s)"                                   | "Email opened"                                         |
| "Dana booked a demo from the email — Thu 9:00 AM"           | "Demo booked"                                          |
| "Personal check-in sent to Dana"                            | "Email sent"                                           |
| "Usage is falling off — logins down 60%, two seats idle"    | "Usage drop detected"                                  |
| "Opened her last 6 emails · clicked pricing twice"          | "Email opened"                                         |
| "Worth a call — renewal in 30 days and she'll pick up"      | "Added to call list"                                   |
| "Routed to you · 1:48 PM"                                   | Cut — nothing was routed; the reader already had it    |
| "Still unread after 8 hours — no response"                  | Cut — an absence isn't an event; a tile says "Unread"  |
| "Call Dana"                                                 | "Call contact"                                         |

The tells: a first name or pronoun, a parenthetical, a duration, a time the
timestamp column already shows, "you", anything after an em-dash, and a step
the system didn't actually take (a hand-off to someone who already sees it). Use
the vocabulary the app already logs (`<thing> detected`, `Email sent`,
`Demo booked`); the row's timestamp carries when, the detail panel carries why.

## Analysis panels: tiles, not prose

An explanatory panel (a diagnosis, an account summary, an insight card) has one
job per element: a headline states the finding, tiles carry the numbers, chips
carry the likely causes, a recommendation says what to do. Prose that does any
of those jobs again is cut.

| Draft                                                                                                     | Cut                                               |
| --------------------------------------------------------------------------------------------------------- | ------------------------------------------------- |
| "Dana got this email, read it, and booked on her own."                                                    | Gone — narrates what the timeline shows           |
| A "What the data shows" list under four tiles that already show the same numbers                         | The whole section                                 |
| "Which one it actually is — that's for the account manager to find out, not the data."                   | Gone — "Likely causes" already says unconfirmed   |
| "Health score 62/100 · At risk" next to a tile showing **62** in the warning tone                         | "Health score"                                    |
| "Onboarding, training, and integrations. Not a downgrade — they bought the right plan six months ago."   | "Review onboarding, training, and integrations."  |
| "The one real churn risk in this list" / "Unlike the last account…"                                       | "Churn risk" — no demo narration                  |
| "Save the relationship, not the deal"                                                                     | "Call the contact · this week"                    |

The moves: every fact becomes a tile (add another tile before you add a
sentence); a tile's value is a reading or a state the system reports
("Invoice overdue", "Sent 5:03 AM", "Inactive") and its detail a timestamp or
identifier ("Unopened", "last login Jul 17"), never a verdict ("Failing",
"collapsing", "ignored for weeks"); the recommendation is an imperative with no
justification clause; a caption never restates the value or tier the tile
already renders; the demo script's voice ("in this list", "real", "she'll pick
up") never reaches the screen, only the facts it was pointing at.

Whole sections take the same two tests. An overview block that restates the
tabs (recent activity, comparisons, notes, a metrics grid) goes unless it
drives an action from that page; it has to earn its way back.

## Before you write a line of help text

1. **Prefer structure to prose.** A run of values joined by `·` is a table wanting
   to happen.
2. **Let the error carry the constraint.** Don't preload the reader with limits
   and formats; say it when they cross the line, in the place they crossed it.
3. **Fold the extra control into the existing one.** A "New template…" button
   beside a select becomes the last option _in_ the select. A "Copy key" link
   under a field becomes a copy icon _in_ the field.

For a common pattern (2FA setup, OTP entry, address forms), check how it is
normally labelled before inventing copy. The prevailing convention is usually
terser than a first draft.

## After the cut, follow the thread

Copy is often the only reader of some state. When a line goes, check what it was
reading. A cut that only shrinks a string usually isn't finished:

- the value it displayed, the state computing that value, and the setter wrapper
  that existed only to keep it fresh
- the style block it used
- the prop that fed it, and the prop's plumbing through the component

Removing one `"10 unused"` row value can take a derived count, the state behind
it, a regenerate helper, and a wrapper function with it, collapsing a context
method back to a bare setter. Grep each removed identifier before moving on.

## Copy comes back through refactors

A cut line returns when someone later wraps the screen in a component whose API
has a required copy slot. An empty required prop invites filling, and the person
filling it wasn't there for the cut.

- Make copy props optional and conditionally render: `subtitle?: string` with
  `{subtitle != null && <Text>…</Text>}`.
- Never pass `""` to satisfy a required prop. It leaves the gap in the layout and
  hides the decision.
- Leave a one-line comment at the cut site saying what was removed and why, so
  the next refactor doesn't restore it.

## Matching an existing screen

When the app already has an equivalent screen, match its **treatment** (spacing,
colour, component, timer format) rather than its copy length. If the older screen
is loose, tighten it too; don't loosen the new one for consistency.

## Short is not the same as clear

Cutting can leave a line that is shorter and wrong. After every cut, read the
survivor cold, as someone who never saw the longer version.

| Cut too far                                                   | Problem                                                                    | Fix                                                                      |
| ------------------------------------------------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| "Ask Sam Ortiz who owns this."                                | Parses two ways: an indirect question, or "Sam Ortiz, who owns this"       | "Check with Sam Ortiz before you choose."                                |
| "The project leaves your workspace on Nov 15."                | A thing performs an action it can't; reads as a metaphor                   | "The project will no longer be in your workspace starting Nov 15."       |
| A transfer confirm with its only consequence line cut         | An irreversible action now goes through with no warning                    | Keep one line saying what changes, plus a destructive button style       |

The checks:

- **One parse.** A name followed by "who", "that" or "which" can be a relative
  clause. Reword so only one reading exists.
- **Plain verbs.** Don't make a project, an email or an account the subject of a
  verb a person does ("leaves", "asks", "wants"). Say what changes for the
  reader. A few extra words are fine when they remove a guess.
- **Irreversible actions keep their consequence.** A confirm for something the
  reader can't undo keeps exactly one line saying what changes. That is the one
  explanation the two tests don't cut.

## The final pass

Before calling any new UI done, read **only** the copy (labels, hints, empty
states, button text), ignoring the components. List it with each screen's title
beside it. Put both tests to every line:

- What does the reader learn that the screen doesn't already show? No answer means
  cut it, or show the thing instead.
- What here explains the system rather than stating the fact? Cut that part.
- Read cold, does what's left have exactly one meaning? If not, reword it rather
  than restoring the cut.

Extract the strings first. `grep -hoE '(title|label|body|subtitle|placeholder)="[^"]+"' *.tsx | sort -u`
puts restatements next to each other that sit hundreds of lines apart in source.
Adjust the pattern for your stack (string catalogs, `t("…")` calls, SwiftUI
`Text("…")`).

## Worked example: a two-step verification settings flow

Six review notes that arrived after the copy had already passed a first edit:

| Feedback                                             | The move                                                              |
| ---------------------------------------------------- | --------------------------------------------------------------------- |
| "'from your authenticator app' should go away"       | Restated the title. Cut once already, then reintroduced by a refactor |
| "'A second check when you sign in…' can also go"     | Restated the title; the two cards carried the rest                    |
| "'protecting sign-ins on new devices' as well"       | The rows already showed it was on                                     |
| "'view backup codes' can ditch the '10 unused'"      | Derived value nobody acted on; took four bits of state with it        |
| "showing `Key:` in the input seems wrong"            | Prefix duplicated the field label                                     |
| "there should be a copy icon instead of a text link" | Fold the extra control into the existing one                          |

Three of the six were the title, restated. All six had survived an explicit copy
pass. Reading copy in place is not enough. Extract it and read it cold.

## Worked example: an account summary panel and its feed

A demo storyline had been transcribed into the UI almost verbatim. Six notes,
after the panel had already passed the two tests once:

| Feedback                                                                                  | The move                                                     |
| ----------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| "the summary section is way too literal and wordy"                                        | Facts → tiles; the bullets restating them → gone             |
| "'Dana opened it (1m 12s)' … a real app would show 'Email opened'"                        | Timeline lines become system events in the app's vocabulary  |
| "'Dana got this email, read it, and booked on her own' is narrating out loud"             | The summary sentence → gone; the timeline already says it    |
| "Health score · At risk → 'Health score'"                                                 | Caption stops restating the tile's tier                      |
| "'Onboarding, training, and integrations. Not a downgrade — …' → 'Review onboarding, training, and integrations.'" | Recommendation is an imperative, no justification |
| "remove Needs attention, Overall health, … they'll have to earn their way back"           | Sections take the two tests too                              |

Three of the six were narration: the script's voice, addressed to a demo
audience, left in the product. Read the copy as the app, not as the presenter.
