# Product principles & positioning

## Why Harbor exists

Elders are being pushed into online systems whether they like it or not (example: a 55+ community that stopped accepting paper checks and forced online bill pay). It's a minefield of scams and confusing UI. Motivating incident: a parent locked out of an iPhone after repeated wrong passcodes, forcing a full reset.

**Mission:** protect seniors from scams. Patagonia-style — cover costs and earn a sustainable margin, but profit is fuel, not the destination.

## Trust is the product

Lockdown serves two goals: **usability** (keep the parent from breaking the device) and **security** (block bad installs, phishing, scams). A non-technical buyer cannot evaluate security, so trust must be proven through proxies — see the validator ladder in `business.md`.

## Personas

| | Parent | Adult child |
|---|---|---|
| Role | Owns and uses the device | Sets up and looks after it; pays |
| Sees | Almost nothing of Harbor | A simple, forgiving dashboard |
| Feels | Pride *and* fear (scams, losing independence, being a burden) | Fear (scams, the panicked call, being IT forever) |

"Adult child" is a defined term: anyone with an interest in keeping another person's device in good state, more technical than the person they help, not necessarily tech-savvy. Both personas are shielded from the MDM machinery.

## Dignity, not deficit

Competitors like GrandPad are deficit-framed: a simplified device that announces "you can't cope." Harbor is dignity-framed: the parent keeps the real, aspirational device (the latest iPhone with the great camera) and Harbor is the invisible layer that makes it safe. We sell permission to keep the nice thing, not a cage.

Message to the parent: *keep living your life on the device you love, with a safety net you don't have to think about.*

## Protect, don't watch

Bright line: blocking a scam site or clearing a lockout is protection. Reading texts, continuous location, screen capture, keystroke or browsing logs is watching — and Harbor never does it.

iOS enforces this for us (supervision is visible; no covert monitoring). On Windows, which would allow far more, we voluntarily hold the same line. Positioning: *Harbor behaves the same everywhere — it protects, it never spies — even on platforms that would let us cross that line.*

This is a written, auditable capability boundary: the capabilities are not built, so they cannot be enabled, misused, breached, or subpoenaed. The deal with the parent: you accept invisible management; we guarantee it can never become spying.

Supervision's only visible trace on iOS is a row in Settings ("This iPhone is supervised and managed by …"). We choose that organization name — it should read as protective.

## Support boundary

Harbor supports the device's configured state — lockouts, restrictions that are too tight, threats that slipped through. It does not teach general tech skills. Those requests route gently to community resources (AARP Senior Planet / OATS, Cyber-Seniors, local libraries and senior centers). Hardware failures route to Apple or the carrier.

Support is AI-assisted to keep fixed costs down, but must feel warm and actually resolve things, with clear hand-off to a human — never a cold dead-end chatbot.
