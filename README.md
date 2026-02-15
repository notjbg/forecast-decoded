# Forecast Decoded

A clean, minimal website that transforms National Weather Service Area Forecast Discussions (AFDs) from meteorological jargon into readable, understandable forecasts for everyone.

## Features

### 🌤️ Two Reading Modes
- **Plain English**: AI-powered translation of weather jargon into readable prose
- **Original + Annotations**: Raw AFD text with interactive hover tooltips explaining meteorological terms

### 📍 Location Support
- Currently supports Los Angeles/Oxnard (LOX) office
- Scaffolded for easy expansion to other NWS forecast offices
- Real-time data from the NWS API

### 🎯 Smart Content Processing
- **Key Takeaway Extraction**: AI-powered summary of the most important forecast information
- **Confidence Indicator**: Visual gauge of forecaster confidence based on language analysis
- **Section Navigation**: Easy jumping between Synopsis, Short Term, Long Term, Aviation, and Marine sections
- **Comprehensive Jargon Glossary**: 70+ meteorological terms with clear definitions

### 📱 User Experience
- Ultra-minimal editorial design inspired by premium blogs
- Mobile-first responsive design
- Serif typography for readability
- Generous whitespace and clean layout
- Fast loading with client-side processing

## How It Works

1. **Data Fetching**: Pulls the latest Area Forecast Discussion from the NWS API
2. **Section Parsing**: Intelligently identifies and separates forecast sections
3. **Plain English Translation**: Uses regex-based transformations to expand abbreviations and clarify technical language
4. **Jargon Annotation**: Highlights technical terms with explanatory tooltips
5. **Key Insights**: Extracts the most important forecast information and confidence level

## Technical Details

### Architecture
- **Single File Application**: Entire site contained in `public/index.html`
- **Vanilla JavaScript**: No frameworks or build steps required
- **NWS API Integration**: Direct calls to `https://api.weather.gov/products/types/AFD/locations/LOX`
- **Client-Side Processing**: All text transformation happens in the browser

### Jargon Glossary
The comprehensive glossary includes:
- **Pressure Levels**: 300mb, 500mb, 700mb, 850mb with altitude explanations
- **Aviation Terms**: MVFR, IFR, LIFR, VFR, TAF, PIREP
- **Marine Warnings**: SCA, GALE, marine forecasting terms
- **Meteorological Concepts**: CAPE, vorticity, QPF, PWAT, thermal profiles
- **Model References**: GFS, NAM, ECMWF, ensembles, hi-res models
- **Weather Phenomena**: TSTM, FZRA, VIRGA, convergence patterns
- **Geographic Abbreviations**: csts, vlys, mtns, and regional identifiers
- **Time References**: Z/UTC, local time conversions

### Design Philosophy
- **Editorial Focus**: Design feels like reading a premium magazine article
- **Content-First**: The forecast is the hero, not the interface
- **Accessibility**: High contrast, readable typography, clear hierarchy
- **Performance**: Single file, minimal dependencies, fast loading

## Local Development

### Quick Start
```bash
# Clone the repository
git clone https://github.com/jmhb1/forecast-decoded.git
cd forecast-decoded

# Serve locally (Python 3)
python -m http.server 8000

# Or with Node.js
npx http-server public -p 8000

# Open http://localhost:8000
```

### File Structure
```
forecast-decoded/
├── public/
│   └── index.html          # Complete single-file application
├── README.md               # This file
└── SPEC.md                 # Original specifications
```

## API Reference

### NWS Area Forecast Discussion API
- **Endpoint**: `https://api.weather.gov/products/types/AFD/locations/{office}`
- **Method**: GET
- **Response**: JSON with forecast data and metadata
- **Rate Limits**: Reasonable use encouraged
- **Documentation**: [NWS API Documentation](https://www.weather.gov/documentation/services-web-api)

### Currently Supported Offices
- **LOX**: Los Angeles/Oxnard, CA

### Future Office Support
The dropdown is scaffolded for easy addition of:
- **SGX**: San Diego, CA
- **MTR**: San Francisco, CA
- **EKA**: Eureka, CA
- **GGW**: Glasgow, MT
- **BOI**: Boise, ID
- And many more...

## Contributing

### Adding New NWS Offices
1. Add office code to the location dropdown in `index.html`
2. Test API endpoint: `https://api.weather.gov/products/types/AFD/locations/{OFFICE}`
3. Update office-specific logic if needed (timezone handling, regional terms)

### Expanding the Jargon Glossary
1. Add new terms to the `JARGON_GLOSSARY` object in `index.html`
2. Include clear, accessible definitions
3. Test tooltip functionality across devices

### Improving Plain English Translation
1. Enhance regex patterns in the `translateToPlainEnglish()` function
2. Add new abbreviation expansions
3. Improve sentence structure and readability

## Deployment

### GitHub Pages (Current)
- Automatic deployment from the `main` branch
- Serves from the `public/` directory
- Custom domain support available

### Alternative Hosting
- **Vercel**: Single command deployment with `vercel`
- **Netlify**: Drag-and-drop or Git integration
- **AWS S3**: Static site hosting
- **Any HTTP Server**: Single file makes deployment trivial

## Data Sources

- **National Weather Service**: Official U.S. government weather forecasts
- **NWS API**: Real-time access to Area Forecast Discussions
- **NOAA**: Meteorological data and definitions

## Browser Support

- **Modern Browsers**: Chrome 60+, Firefox 60+, Safari 12+, Edge 79+
- **Mobile**: iOS Safari 12+, Chrome Mobile 60+
- **Features Used**: Fetch API, ES6 features, CSS Grid/Flexbox

## Performance

- **Load Time**: < 2 seconds on 3G
- **Bundle Size**: ~50KB (single HTML file)
- **API Calls**: 1 request per page load
- **Caching**: SessionStorage for forecast data

## Privacy

- **No Tracking**: No analytics or user tracking
- **No Cookies**: Stateless application
- **API Calls**: Direct to NWS, no intermediary services
- **Local Processing**: All text transformation happens client-side

## Credits

- **Built by**: [Jonah Berg](https://jonahberg.com)
- **Weather Data**: National Weather Service
- **Design Inspiration**: Editorial websites like Dario Amodei, Stefan Peipke
- **Typography**: System fonts for performance and consistency

## License

MIT License - feel free to fork, modify, and use for any purpose.

---

**Live Site**: [forecast-decoded.vercel.app](https://forecast-decoded.vercel.app) (when deployed)
**Repository**: [github.com/jmhb1/forecast-decoded](https://github.com/jmhb1/forecast-decoded)