# Round Table

A multiplayer role-playing table in the browser: a shared chronicle, a codex of the world, player actions, and an AI game master that writes the world's response. Everyone at the table sees the same state live.

**Open it:** https://calvinslinde.github.io/roundtable/

## How it works

- **SvelteKit** front end; `src/routes/+page.svelte` is the table itself.
- **Yjs** keeps the game state identical between players, over WebRTC with IndexedDB persistence (`src/lib/stores/gameStore.ts`); a Cloudflare Durable Object in `server/` relays and persists each world so a table can be rejoined by its room code.
- **The game master** is Gemini, called with the live codex as context (`src/lib/ai/`). The host supplies the key.
- **Three.js** dioramas for scenes (`src/lib/components/CinematicDiorama.svelte`).

`ARCHITECTURE.md` maps the codebase in detail. `research/` holds design notes on the visual language the generator follows.

## Run it locally

```
npm ci
npm run dev
```

Deploys to GitHub Pages from `main` through `.github/workflows/deploy.yml`.

Built with Claude.
