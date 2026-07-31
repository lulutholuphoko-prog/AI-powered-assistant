- Progress tracking with completion percentage and AI productivity recommendations

### 4. AI Research Assistant (`/research`)
- Summarize a topic, question, or pasted article
- Depth and audience controls
- Overview, key findings, insights with implications
- Recommendations table scored by impact and effort, plus risks and open questions
- Copy or PDF export

### Responsible AI (`/responsible-ai`)
- Disclaimer that AI-generated content should be reviewed before professional use
- Guidance to verify legal, financial, and business-critical information
- Privacy note: no sensitive information is stored server-side
- Explanation that AI outputs may contain inaccuracies or omissions

### Experience
- Fully responsive desktop and mobile layouts
- Pink/purple gradient palette, rounded cards, soft shadows
- Dark and light mode toggle
- Smooth animations, loading indicators during generation
- Toast notifications and a `⌘K` / `Ctrl+K` search command palette
- Accessible typography and color contrast

## Tools used

| Area | Technology |
| --- | --- |
| Framework | TanStack Start v1 (React 19, TanStack Router) |
| Build tool | Vite 8 |
| Language | TypeScript |
| Styling | Tailwind CSS v4 (OKLCH tokens in `src/styles.css`) |
| UI components | shadcn/ui + Radix UI primitives |
| Icons | lucide-react |
| Notifications | sonner |
| Command palette | cmdk |
| Data fetching | TanStack Query |
| AI SDK | Vercel AI SDK (`ai`, `@ai-sdk/openai-compatible`) |
| AI provider | Lovable AI Gateway (`openai/gpt-5.4-mini`, OpenAI-compatible) |
| Validation | Zod |
| Persistence | Browser `localStorage` |

## Project structure

```text
src/
  components/       app shell, sidebar, shared AI UI pieces
  hooks/            theme + responsive helpers
  lib/
    ai.functions.ts     server functions for each AI module
    ai.schemas.ts       Zod schemas for structured AI output
    ai-gateway.server.ts AI gateway provider/model config
    store.ts            localStorage stats + task persistence
  routes/           file-based routes (index, email, meetings, tasks, research, responsible-ai)
  styles.css        Tailwind v4 theme tokens
```

## Setup instructions

### Prerequisites
- Node.js 20+ and npm (or bun)

### Install and run

```sh
git clone <this-repository-url>
cd <repository-name>
npm i
npm install
npm run dev
```

## Built with
The dev server starts on http://localhost:8080.

- TanStack Start
- TypeScript
- React
- Tailwind CSS
### Environment variables

The AI modules call the Lovable AI Gateway from server functions and need one key:

```sh
# .env
LOVABLE_API_KEY=your_gateway_api_key
```

In Lovable this key is provisioned automatically. Running locally, add it to a `.env`
file at the project root. It is read server-side only and never exposed to the browser.

To use a different OpenAI-compatible provider, change the `baseURL`, headers, and model
id in `src/lib/ai-gateway.server.ts`.

### Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Start the dev server |
| `npm run build` | Production build |
| `npm run preview` | Preview the production build |
| `npm run lint` | Run ESLint |
| `npm run format` | Format with Prettier |

## Disclaimer

AI-generated emails, summaries, plans, and research briefs may contain inaccuracies or
omissions. Always review output before professional use, and independently verify legal,
financial, and business-critical information.

