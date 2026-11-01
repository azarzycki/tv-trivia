# TV Trivia

Jeopardy-style Toronto trivia board, served from GitHub Pages and wrapped in a tiny Android TV app.

- **Play in a browser:** https://azarzycki.github.io/tv-trivia/
- **TV app (APK):** https://github.com/azarzycki/tv-trivia/releases/latest

## Updating the questions
Edit `index.html` (the `DATA` block at the top of the script) and push to `main`. The Pages workflow redeploys the site; the installed TV app picks up the change on next launch. No new APK needed.

## Phone buzzers
Players open https://azarzycki.github.io/tv-trivia/buzz/ (or scan the QR under **Buzzers** on the TV), enter the 4-letter room code and a team, and get a buzz button. The TV arms buzzers when a clue opens, locks on the first buzz and highlights that team's award buttons.

Backed by a Firebase Realtime Database (`to-trivia`, free Spark plan, no server code). The rules in `database.rules.json` must be published in the Firebase console (Realtime Database → Rules); until then the buzzer UI stays hidden and the game plays normally.

## The Android TV app
`android/` is a bare WebView shell with a Leanback launcher entry. The `Build TV APK` workflow builds and signs it on every push that touches `android/`, and attaches the APK to the `latest` release. Build locally with `cd android && gradle assembleRelease` (needs the Android SDK, platform 34).

Sideloading on a Sony Google TV: enable *Unknown sources* for Downloader by AFTVnews, then fetch
`https://github.com/azarzycki/tv-trivia/releases/latest/download/app-release.apk`.
