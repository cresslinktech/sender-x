# TITAN SENDER - Professional Desktop Email Marketing Platform

This is an Electron-based desktop application that replicates the TITAN SENDER website, designed to run locally on Windows with all data stored locally.

## Features

- **14 Professional Send Engines**: SMTP Relay, Direct-to-MX, OWA, Graph API, Gmail API, AWS SES, SendGrid, Mailgun, Postmark, Brevo, SparkPost, Elastic Email, Mandrill, M365 Direct Send
- **Campaign Editor**: Visual builder with A/B testing, merge tags, and more
- **AI Email Writer**: Generate unique email variations in 26 languages
- **Anti-Fingerprint Engine**: 6 randomization layers to prevent pattern-based detection
- **Send Console**: Real-time monitoring and delivery tracking
- **IMAP Integration**: Connect any mailbox to track replies
- **Local Data Storage**: All data stays on your machine with AES-256 encryption

## Project Structure

```
src/
├── main/
│   ├── main.ts           # Electron main process
│   ├── preload.ts        # IPC bridge
│   └── ipc-handlers.ts   # IPC event handlers
├── renderer/
│   ├── index.tsx         # React entry point
│   ├── App.tsx           # Main app component
│   └── pages/            # Page components
├── services/
│   ├── database/         # SQLite + Drizzle ORM
│   ├── campaigns.ts      # Campaign management
│   ├── send.ts           # Email sending
│   ├── leads.ts          # Lead/recipient management
│   ├── analytics.ts      # Analytics & reporting
│   ├── settings.ts       # User settings
│   ├── auth.ts           # Authentication
│   └── ai.ts             # AI integration
├── components/           # React components (from Next.js app)
├── lib/                  # Utilities
└── types/               # TypeScript definitions
```

## Installation & Development

### Prerequisites
- Node.js 18+ with pnpm
- Windows 10/11 64-bit (for production)

### Setup

1. **Install dependencies**
   ```bash
   pnpm install
   ```

2. **Create environment file**
   ```bash
   cp .env.example .env
   ```

3. **Start development**
   ```bash
   pnpm dev
   ```

This will start both the TypeScript compiler in watch mode and Electron.

## Building for Production

```bash
# Windows only
pnpm build:win

# All platforms
pnpm build
```

## Architecture Notes

- **Frontend**: React + TypeScript with Tailwind CSS (reused from Next.js app)
- **Desktop Framework**: Electron 28+
- **Database**: SQLite with Drizzle ORM (all local)
- **Encryption**: AES-256 for sensitive data
- **IPC**: Electron IPC for main/renderer communication

## Migration from Next.js

- Removed Next.js server-side rendering
- Moved API routes to IPC handlers
- Switched from PostgreSQL to SQLite
- All data processing moved to Electron main process
- React components reused with minimal changes

## Next Steps

1. **Implement Email Engines**: Create abstraction layer for 14 send methods
2. **Anti-Fingerprint Engine**: Implement 6 randomization layers
3. **Campaign Management**: CRUD operations with database
4. **Send Infrastructure**: Queue system with retry logic
5. **AI Integration**: OpenAI API for email generation
6. **UI Pages**: Complete all dashboard pages
7. **Testing**: Unit and E2E tests
8. **Packaging**: NSIS installer for Windows

## Development Commands

```bash
pnpm dev           # Start development
pnpm build         # Build for distribution
pnpm build:win     # Windows-specific build
pnpm lint          # Lint TypeScript
pnpm db:push       # Run database migrations
pnpm db:studio     # Open Drizzle Studio
```

## License

MIT
