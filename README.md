# Nitya Sankalpam

Daily Hindu Puja Sankalpam for the Karnataka/Mysuru tradition.

## Current release
- App name: Nitya Sankalpam
- Panchanga tradition: Karnataka / Mysuru / Ontikoppal
- Reference period: 19 March 2026 – 6 April 2027
- Validated reference currently included: 5 October 2026
- Status: validation-first prototype

## Accuracy rule
The browser astronomy is a fallback/prototype. It must not be presented as official Ontikoppal data. Published annual Panchanga data should validate and override calculated values before a date is marked validated.

## Roadmap
1. Import the complete 2026–27 annual Ontikoppal-derived dataset.
2. Add validation tests for tithi, nakshatra, yoga, karana, masa, paksha and Sankalpam wording.
3. Add each annual edition as a new data package.
4. Add Mysuru and optional Karnataka city profiles.
5. Package the same PWA for Android and iOS with Capacitor.
6. Add automated annual ingestion only from a permitted/licensed source.

## Website
Use GitHub Pages with the main branch and GitHub Actions deployment.

## Mobile
The intended architecture is PWA first, then Capacitor wrappers. Android releases should be Android App Bundles (AAB). iOS releases should be built/uploaded through Xcode and App Store Connect.

## Attribution
This is an independent project and is not affiliated with Ontikoppal Panchanga Mandira. If annual published data is used, obtain appropriate permission/licensing where required and retain source attribution.