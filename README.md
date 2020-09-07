# issue-typescript-eslint-4.0.1-no-use-before-define-and-no-undef

Using `@typescript-eslint/eslint-plugin` and `@typescript-eslint/parser` version 4.0.1 produces two regressions that did not happen using version 3.X.X. Those regressions are:

1. If a file exports two TypeScript `types` and the first one depends on the second one, then typescript-eslint complains about "no-use-before-define". It shouldn't given that this is pure TypeScript. See `src/index.ts`.
2. WebRTC related DOM definitions are unknown. Example: `RTCRtpEncodingParameters` in `src/index.ts` even if `tsconfig.json` has "dom" into `lib` field.

None of those happens using versions 3.X.X.

Just run `npm install` and `npm run lint` to reproduce them. Then downgrade `@typescript-eslint/eslint-plugin` and `@typescript-eslint/parser` packages to 3.8.0 and run again (no issues).
