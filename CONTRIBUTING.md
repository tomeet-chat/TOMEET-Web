# Contributing to TOMEET Web

Thanks for contributing to **TOMEET Web**!

## Local Verification

Before opening a pull request, ensure both lint and production build succeed:

```sh
npm install
npm run lint
npm run build
```

## Guidelines

- **Keep i18n in sync**: Update both `src/messages/en.json` and `src/messages/zh.json` whenever adding or editing user-facing copy.
- **Respect server-only secrets**: Route backend requests through `/api/tomeet/[...path]` using `TOMEET_API_BASE_URL` rather than exposing private credentials to the client bundle.
- **Mobile & PWA first**: Verify responsive layouts on narrow viewports (e.g., 375px–430px) in addition to desktop.
- **Visual changes**: Attach before/after screenshots or short clips in your PR description.
