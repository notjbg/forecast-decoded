# 🌤️ Plaincast

**NWS Area Forecast Discussions, decoded into plain English.**

**[→ plaincast.live](https://plaincast.live)** · **[☕ Support the Project](https://buymeacoffee.com/notjbg)** · **[💡 Suggest a Feature](https://github.com/notjbg/plaincast/issues)**

---

## What Is This?

Area Forecast Discussions (AFDs) are the real forecasts - written 3-4 times daily by National Weather Service meteorologists who actually read the models and interpret what they mean for your area. They're far deeper than any weather app, but they're written in dense meteorological shorthand that's nearly unreadable for normal people.

Plaincast puts the plain English translation side-by-side with the annotated original, so you can finally read what the forecasters are actually saying.

---

## Features

### 📖 Side-by-Side Translation
Plain English on the left, original AFD with jargon annotations on the right. Every highlighted term in the original has a hover tooltip (or tap on mobile) explaining what it means. 150+ term glossary covering synoptic meteorology, aviation, marine, pressure levels, model names, and airport codes.

### ⚡ Key Takeaway
Bold 1-2 sentence summary at the top extracting what matters most from the Synopsis. Skip the details when you just need the headline.

### 📊 Forecaster Confidence
Visual indicator analyzing the AFD's language for certainty vs. uncertainty signals. Words like "high confidence" and "consistent" push it up; "uncertain", "tricky", and "wide range" push it down. Gives you a quick read on how much the forecasters trust their own forecast.

### 🔍 Smart Abbreviation Expansion
NWS shorthand translated inline - `chc` becomes "chance", `mtns` becomes "mountains", `BKN015` becomes "broken clouds at 1,500 ft", and Zulu times convert to your local timezone (DST-aware per office).

### ✏️ Bold Key Info
Days of the week, hazard terms, temperatures, rainfall amounts, and wind speeds are bolded for skimmability. Scan the forecast in seconds.

### 🗂️ Section Parsing
Synopsis, Short Term, Long Term, Aviation, Marine, Beaches, Fire Weather, and Active Alerts all rendered as separate sections with pill-style jump navigation.

### ⚠️ Active Alerts
Current watches, warnings, and advisories formatted as a clean, color-coded bullet list. Click any alert to see the full NWS detail in a modal - headline, affected areas, expiration, and complete description.

### 🏢 19 NWS Offices
Los Angeles, New York, Chicago, Houston, Phoenix, Philadelphia, Dallas/Fort Worth, San Antonio, San Diego, San Francisco, Miami, Atlanta, Washington DC, Boston, Denver, Seattle, Portland, Las Vegas, and Central California.

### 💾 Caching
15-minute sessionStorage cache with stale fallback on API errors. Fast repeat loads, graceful degradation.

---

## Technical Details

- **Single-file app** - Everything in `docs/index.html` (~1,600 lines)
- **Zero dependencies** - Vanilla HTML/CSS/JS, no frameworks, no build step
- **NWS API** - Pulls directly from `api.weather.gov` (no API key needed)
- **System fonts** - Georgia serif for body, system monospace for raw AFD, system sans for UI
- **Light mode** - Editorial design with generous whitespace
- **Mobile responsive** - Side-by-side stacks to vertical on screens under 768px
- **Accessible** - ARIA roles on modal and tooltips, focus trapping, keyboard navigation, severity icons (not color-only)
- **DST-aware** - Zulu time conversion uses IANA timezones per office, not hardcoded offsets

---

## Architecture

```
┌─────────────────────────────────────────────┐
│  docs/index.html - single-file vanilla app  │
│                                             │
│  NWS API (api.weather.gov)                  │
│    ├─ /products/types/AFD/locations/{office} │
│    ├─ /products/{id}                        │
│    └─ /alerts/active?area={state}           │
│                                             │
│  No server. No build. No API key.           │
└─────────────────────────────────────────────┘
```

---

## Run Locally

```bash
cd docs && python3 -m http.server 8765
# Open http://localhost:8765
```

---

## Why?

Weather apps give you icons and numbers. AFDs give you the *reasoning* - why the models disagree, what the forecasters are watching, where the uncertainty is. That's the forecast that matters for planning trips, events, or just understanding what's actually happening in the atmosphere.

The problem is they look like this:

```
.SYNOPSIS...DEEP SW FLOW WILL CONT TO BRING PCPN TO THE AREA
THRU TUE. TEMPS WILL REMAIN BLO NORMAL. NEXT TROF MOV THRU WED...
```

Now they look like this:

> Deep southwest flow will continue to bring precipitation to the area through **Tuesday**. Temperatures will remain below normal. Next trough moving through **Wednesday**.

---

## Credits

Built by [Jonah Berg](https://jonahberg.com). Data from the [National Weather Service](https://www.weather.gov).

---

## License

MIT - see [LICENSE](LICENSE) for details.
