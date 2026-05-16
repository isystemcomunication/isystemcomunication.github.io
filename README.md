# IOSx

IOSx is a GitHub Pages single-page app for Android device setup requests.

The app provides:

- Firebase Authentication with Google sign-in, email/password sign-up, email verification, and password recovery.
- A multilingual request flow in Russian, English, and Chinese.
- Device search and manual device entry.
- Request submission to a Google Apps Script endpoint.
- Telegram handoff with a request id.

## Project Structure

- `index.html` - main app, styles, translations, Firebase setup, routing, and request flow.
- `404.html` - GitHub Pages redirect shim for SPA routes such as `/login`, `/pending`, and `/success`.

## External Services

The app depends on:

- Firebase Authentication.
- Google Apps Script for request intake.
- Telegram bot handoff.
- GitHub Pages hosting.

Firebase web config is public by design, but the backend must still validate Firebase ID tokens, restrict accepted origins, and rate-limit submissions.

## Security Notes

- Do not trust client-side checks for payments, user identity, or request ownership.
- Validate `idToken` server-side before accepting a request.
- Keep Google Apps Script and Telegram bot logic defensive against duplicate or forged `requestId` values.
- Consider adding a Content Security Policy before adding more third-party scripts.

## Local Development

This is a static site. You can open `index.html` directly, but Firebase auth flows and GitHub Pages routing should be tested on the deployed domain.
