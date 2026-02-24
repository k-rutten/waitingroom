# Project Spec -- Wachtkamer (Waitingroom)

## Problem Statement
Patients in a doctor's waiting room have no visibility into their queue position. They don't know how many people are ahead or when it's their turn. Doctors have no structured queue and resort to awkwardly asking "who's next?" The friction is informational, not logistical -- people just need to know where they stand.

## Target User + Context
- **Patients** -- anyone visiting a doctor's practice. They scan a QR code on their phone while sitting in the waiting room. They want clarity on wait time and position. Zero-install, no accounts.
- **Doctor/Practitioner** -- manages the queue from their phone or tablet between consultations. Needs a workflow as simple as checking off a todo list. PIN-gated access.

## Success Metrics
- Patient can join queue in under 10 seconds (scan QR + type name + tap button)
- Patient always sees an accurate, auto-updating position (2s polling)
- Doctor can process queue with single taps (no multi-step flows)
- Works on any modern phone browser (iOS Safari, Android Chrome)
- Review completion rate as engagement signal

## Chosen Concept Direction
QR-to-mobile-web-app approach. Single `index.html` with two hash-routed views (Patient and Doctor). iOS-inspired "Calm Clarity" theme. localStorage for data persistence, cross-tab sync via storage events + polling fallback.

## Prototype Scope + Flow
**Patient flow:** Splash screen -> Enter last name -> See position (auto-updates) -> "Your turn" notification -> Review (1-5 stars) -> Thank you + confetti
**Doctor flow:** PIN gate (1234) -> Queue list with Start/Complete actions -> QR code generator for printing

## Known Constraints
- Single index.html file (no build tools, no bundler)
- React 18 + Tailwind CSS + Babel via CDN
- localStorage only -- no backend (MVP/demo limitation)
- Cross-tab sync works on same device only
- Must work as mobile web-app (iOS Safari, Android Chrome)
- Dutch language (nl-NL locale)
- Daily auto-reset of queue

## Open Risks / Questions
- No backend means cross-device sync is impossible (patient and doctor must share same browser/device localStorage, or separate devices won't sync)
- Scalability limited to localStorage capacity
- No authentication for patients (by design, but could be abused)
- QR code links to same origin -- hosting/deployment strategy unclear
- What happens if multiple doctors need to manage the queue simultaneously?

## Phase History
(None yet -- starting fresh)
