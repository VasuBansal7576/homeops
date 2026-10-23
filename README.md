# HomeOps

HomeOps is a local household operations assistant for the Alexa+ simulated-experience track of the Amazon Developer Hackathon. It remembers appliance maintenance, warranties, preferences and confirmed expenses. A real model uses household tools, durable approvals and Streamable HTTP MCP against the same saved records.

## Source and setup

The complete source, assets, lockfile, tests, MIT license and detailed setup instructions are packaged in **homeops-source.zip**. This repository distributes a reviewed source snapshot without private development history or runtime state. SOURCE_MANIFEST.json records each packaged file. The archive is source code, not a compiled binary.

```sh
git clone https://github.com/VasuBansal7576/homeops.git
cd homeops
unzip homeops-source.zip
cd homeops
```

Read the extracted README.md for all prerequisites. Use Node.js 26.12.0 and a separately authorized supported Codex CLI account.

```sh
codex login
codex login status
npm ci
npm run build
npm start
```

Open http://127.0.0.1:43110 and enter `homeops-demo`. Choose **Try a demo** and Maple, or explicitly set up a personal household. Startup inserts no demo records. Keep the terminal running for scheduled work.

For local speech on macOS, install `whisper-cpp` and `ffmpeg` with Homebrew, then run `node scripts/setup-voice.mjs` from the extracted source root. Typed and labeled recorded-audio input remain available. Current live in-app microphone capture is unresolved. Linux speech is unverified.

The actual agent entry point is `apps/agent/agent/agent.ts` within the archive; MCP channel configuration is under `apps/agent/agent/channels/`. Full tests and verification scripts are included. Run `npm test`, `npm run typecheck` and `npm run build` in the extracted source. The README documents actual model and MCP journey checks.

## Demo and boundaries

Launch film: https://youtu.be/yKQUnt9nOM8

This is an Alexa+ simulation without an Alexa device. Demo household/provider data and reservations are synthetic. Real provider contact and payment are not performed. Personal mode uses manually sourced quotes and creates a local plan awaiting contact. Completion and confirmed spending are separate records.

The film uses actual app footage, recorded computer-spoken input through real local transcription, an explanatory diagram and documentary narration. It does not prove fresh human speech or live microphone access.

The current model adapter uses local Codex app-server with the operator's own authorized account. It does not expose or share account credentials. Free evaluator inference through November 20 has not been arranged, and a paid owner run does not prove another account's entitlement. Keep this subscription-backed integration local. Do not host it using shared owner credentials.

Preserve SQLite state and Eve workflow data across normal same-build restarts. Use disposable state for mutation tests and never continue old workflows against a reset household. Detailed limitations and reset instructions are in the extracted README.

## License

Application source is MIT licensed. Dependency and model licenses remain separate.
