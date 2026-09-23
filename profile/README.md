<div align="center">
  <img src="https://raw.githubusercontent.com/concile-dev/concile/main/.github/assets/hero.svg" alt="Concile. Your entire backend. Realtime by default." width="100%" />
</div>

<div align="center">

**Your entire backend. Realtime by default.**

Concile is the open source backend you host yourself. You write one plain TypeScript function.
Every screen that shows its data updates on its own. No polling, no cache to clear, no glue code.

[Website](https://concile.dev) · [Docs](https://concile.dev/docs) · [Quickstart](https://concile.dev/docs/get-started/quickstart) · [Blog](https://concile.dev/blog)

</div>

---

## Ten lines, no step three

On the server, plain functions in one file:

```ts
// concile/tasks.ts
import { query, mutation } from "./_generated/server";

export const list = query(async (ctx) => ctx.db.query("tasks").collect());

export const add = mutation(async (ctx, { text }) => {
  await ctx.db.insert("tasks", { text, done: false });
});
```

In the browser, one hook that stays live:

```tsx
const tasks = useQuery(api.tasks.list);
// Call add() from any device, anywhere. This list re-renders here at once.
```

## What you get

- **Live queries.** Every query is a subscription. When the data behind it changes, connected clients get fresh results over WebSocket.
- **A transactional database.** Every mutation is one serializable transaction. SQLite for zero-config local dev, Postgres for production.
- **Auth.** Sessions, email flows, OAuth, passkeys and MFA, built in.
- **File storage.** S3 or local disk, behind one API.
- **Cron jobs and durable workflows.** Multi-step work that survives restarts, with compensation on failure.
- **Offline first.** Optimistic updates and a durable outbox that replays exactly once.
- **A dashboard.** Data browser, logs and functions, in the same binary.
- **Deploy anywhere.** A single compiled binary, `docker compose up`, Cloudflare Workers, or your own Postgres.
- **100% open source, self-hosted.** There is no Concile cloud. Your data stays on your infrastructure.

## Get started

```bash
npm i concile        # or: bun add concile
npx concile dev      # watches your functions, serves live sync, boots the dashboard
```

## Repositories

| | |
|---|---|
| 🚀 **[concile](https://github.com/concile-dev/concile)** | The monorepo: engine, CLI, client SDK, dashboard, docs and the website |

## Licence

Free to use and self-host under [FSL-1.1-Apache-2.0](https://fsl.software). It converts to Apache 2.0 after two years.
