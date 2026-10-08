# Architecture

## MDM engine

**Decision:** embed an open-source MDM core (Fleet or MicroMDM — choice open) behind a clean internal boundary so it can be replaced later. The engine speaks the Apple MDM protocol, holds the APNs push certificate, and handles enrollment, policy, and commands.

Rejected for now: building an engine from scratch; building on a commercial MDM's API.

Real engineering effort goes into the **enrollment experience** and the **adult-child dashboard**, not the engine.

## iOS

Every Harbor iPhone/iPad is **supervised**. Supervision is the gate to the deep restriction set.

**Enrollment:** supervision can only be applied during initial setup, so the device must be erased. Flow for an existing device: back up → erase → in Setup Assistant, enroll and restore from the parent's iCloud backup (same Apple Account). The parent keeps photos, contacts, data; apps re-download under management. Watch MDM settings that interact with restore (e.g. remove-apps-on-profile-removal). For a new device, enroll during first setup.

Enrollment is hands-on by the adult child (working assumption).

**Lockdown available when supervised:**
- Apps: block install and delete, hide/allow-list apps, Single App Mode or limited-app mode
- Settings: block account changes, erase-all, passcode changes, network/VPN changes, profile removal
- Web/content: force a single managed browser, content filter (allow/deny lists), managed DNS blocking scam and phishing domains, App Store and in-app purchase restrictions
- Misc: AirDrop, camera, and other smaller controls
- Passcode policy managed centrally (directly addresses the lockout story)

**Visibility:** iOS shows "This iPhone is supervised and managed by <org>" in Settings only. Nothing on the home screen. Apple does not permit covert monitoring.

## Windows

More fragmented: assigned access/kiosk, AppLocker/WDAC, Group Policy / MDM CSPs. Likely start: tightly configured standard user account + app allow-listing rather than full MDM.

Set SmartScreen via policy so malicious-site and download warnings are **not bypassable** (removes "run anyway") — Microsoft's free detection becomes a hard wall.

Windows permits keylogging, screen capture, and similar. **Harbor does not build any of it** (see `product-principles.md`).

## Security sources

Value comes first from the platforms' own free protective dials turned all the way up — too restrictive for normal users, right for these devices. Paid threat-intel feeds are deferred until an elder-specific gap is proven. Harbor's value is expert curation and enforcement, not reselling detection.

## Scope

iOS and Windows. Android out of scope for now.
