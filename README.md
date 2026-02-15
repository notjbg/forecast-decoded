# Plaincast

**[plaincast.live](https://plaincast.live)** — NWS Area Forecast Discussions, decoded into plain English.

## What Is This?

Area Forecast Discussions (AFDs) are the real forecasts — written 3–4 times daily by National Weather Service meteorologists who read the models and interpret what they mean for your area. They offer far deeper insight than any weather app, but they're written in dense meteorological shorthand that's nearly unreadable for normal people.

Plaincast translates them into plain English, side by side with the annotated original.

## Features

- **Side-by-side layout** — Plain English translation on the left, original AFD with jargon annotations on the right
- **Key Takeaway** — Bold 1–2 sentence summary of what matters most, extracted from the Synopsis
- **Forecaster Confidence** — Visual indicator analyzing the AFD language for certainty vs. uncertainty signals
- **150+ term jargon glossary** — Hover any highlighted term in the original to see a plain definition. Covers synoptic meteorology, aviation (MVFR/IFR/VFR/TAF), marine (SCA/GALE), pressure levels, model names, airport codes, and more
- **Smart abbreviation expansion** — Translates NWS shorthand (chc → chance, mtns → mountains, BKN015 → broken clouds at 1,500 ft, Zulu times → local times)
- **Bold key info** — Days, hazard terms, temperatures, rainfall amounts, and wind speeds are bolded for skimmability
- **Section parsing** — Synopsis, Short Term, Long Term, Aviation, Marine, Beaches, and Active Alerts all rendered separately with jump navigation
- **Active Alerts** — Current watches/warnings/advisories formatted as a clean bullet list
- **Multi-office support** — LOX (Los Angeles), SGX (San Diego), HNX (Hanford), VEF (Las Vegas), MTR (San Francisco), SEW (Seattle), PQR (Portland), OKX (New York)
- **Caching** — 15-minute sessionStorage cache with stale fallback on API errors
- **DST-aware timezone conversion** — Zulu times converted using proper IANA timezones per office

## Technical Details

- **Single-file app** — Everything in `public/index.html` (~1,200 lines)
- **Zero dependencies** — Vanilla HTML/CSS/JS, no frameworks, no build step
- **NWS API** — Pulls directly from `api.weather.gov` (no API key needed)
- **System fonts** — Georgia serif for body, system monospace for raw AFD, system sans for UI
- **Light mode** — Editorial design with generous whitespace, inspired by premium blogs
- **Mobile responsive** — Side-by-side stacks to vertical on screens under 768px

## Run Locally

```bash
cd public && python3 -m http.server 8765
# Open http://localhost:8765
```

## Credits

Built by [Jonah Berg](https://jonahberg.com). Data from the [National Weather Service](https://www.weather.gov).
