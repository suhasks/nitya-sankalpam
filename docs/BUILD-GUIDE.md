# Nitya Sankalpam — Build & Accuracy Guide

## 1. What we built
Nitya Sankalpam is a small, installable web app for generating a daily Hindu Puja Sankalpam using Karnataka/Mysuru (Ontikoppal) Panchanga conventions.
The current reference period is 19 March 2026 through 6 April 2027.

## 2. The most important design decision
We separated three things:
1. Tradition rules — Karnataka/Mysuru Chandra-mana, Amavasyanta month naming, and Sankalpam structure.
2. Annual Panchanga data — the date-by-date calendar record.
3. Astronomical fallback — a backup calculation used only when an annual record is unavailable.
This prevents the app from pretending that a mathematical estimate is an official Panchanga value.

## 3. Where the calendar data came from
The annual calendar is derived from a public machine-readable calendar whose description identifies Ontikoppal Panchanga Mandira, Mysore as its source. It is stored locally in data/ontikoppal-2026-27.ics.
The extraction is not perfect. It contains OCR/extraction gaps and anomalies. Therefore the app labels annual-reference data as such and does not call the application official Ontikoppal.

## 4. Why we did not blindly calculate everything
A Panchanga is not just what the Moon is doing today. Tithi, Nakshatra, Yoga, Karana and sunrise depend on exact astronomical conventions, location, time and boundary handling.
If published annual data and a rough browser calculation disagree, silently choosing the calculation would make the app look precise while being wrong.
The safe rule is: published/validated annual data first; calculation second; uncertainty is visible.

## 5. How the app works
Step A — You choose a date. The browser reads the selected date.
Step B — The app looks in its calendar box. It loads data/ontikoppal-2026-27.ics and finds the matching date.
Step C — It fills the traditional fields. It uses the annual record for Masa, Paksha, Tithi and festival information when present.
Step D — It calculates a fallback when necessary. A compact Sun/Moon calculation can estimate Tithi, Paksha and Nakshatra. This is clearly marked as fallback data.
Step E — It builds the Sankalpam. The app combines Samvatsara, Ayana, Ritu, Masa, Paksha, Tithi, Vara and Nakshatra into the displayed text.
Step F — You can copy or share it. Copy uses the browser clipboard; Share uses the phone/browser share sheet when available.

## 6. Why it is a web app
A web app is the simplest first version: one codebase, phone and computer support, PWA installation, no App Store approval, and easy annual updates.
Android and iPhone wrappers can be added later without rebuilding the Panchanga logic.

## 7. Why the files are small
The app intentionally avoids a large framework. It uses HTML for the page, CSS for appearance, JavaScript for logic, ICS for annual calendar data, and a service worker for offline/PWA behaviour.

## 8. What was tested
The project was checked for annual date coverage, duplicate dates, missing dates, the reference-date comparison, browser-side annual data loading, fallback behaviour, copy/share behaviour, and GitHub Pages deployment structure.
A key validation reference used during development was 5 October 2026: Bhadrapada, Krishna Paksha, Dashami, Monday and Pushya.

## 9. Important accuracy limitation
The public Ontikoppal-derived ICS does not reliably provide every field needed for a fully authoritative daily Panchanga, especially exact Tithi-ending time, Nakshatra-ending time, Yoga, Karana and sunrise for every date.
Therefore this release should be described as: Karnataka/Mysuru Sankalpam app using an Ontikoppal-derived annual reference dataset, with clearly labelled astronomical fallback.
It should NOT be described as Official Ontikoppal Panchanga.

## 10. What would make a future release fully authoritative
The ideal annual data pack should contain, for every date: Samvatsara, Ayana, Ritu, Masa, Paksha, Tithi, Tithi ending time, Nakshatra, Nakshatra ending time, Yoga, Yoga ending time, Karana, Sunrise, Sunset, festivals/observances, location/timezone, and source edition/version.
Then the browser does almost no astronomy. It simply reads the verified calendar. That is safer for religious use.

## 11. Why the app uses a source layer
Imagine two boxes.
Box 1: Rules — how Karnataka names months and writes Sankalpam.
Box 2: Calendar — what happened on a particular date.
Rules rarely change. The calendar changes every year. Keeping them separate means a new annual data file can replace the old one without rewriting the whole app.

## 12. Deployment
The source lives in GitHub and GitHub Pages publishes the web app.
Public application: https://suhasks.github.io/nitya-sankalpam/

## 13. Beginner explanation
If you are five years old: the app is a little calendar robot.
You ask: Robot, what should I say for puja today?
The robot looks at the Karnataka calendar, finds today's row, picks the important words, puts them in the correct Sankalpam order, shows them, and lets you copy them.
It also has a calculator in its pocket. If the calendar does not have a value, the calculator can make an estimate. The robot tells you that it is an estimate instead of pretending it is the printed Panchanga.
That last part is the most important safety feature.

## 14. Future roadmap
1. Obtain a publisher-approved annual data source.
2. Add exact ending times and all daily Panchanga fields.
3. Add city profiles while preserving Mysuru as the default.
4. Add Kannada display.
5. Add selectable Sankalpam wording variants only after validating them against the intended tradition.
6. Add automated date-by-date regression tests.
7. Package the same codebase as Android/iOS.

## 15. Final principle
For a religious calendar, being honest about uncertainty is better than displaying a beautiful but invented number.