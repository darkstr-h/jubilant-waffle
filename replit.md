# Overview

"عراق جات (Iraq Chat)" is an Arabic-first social media platform inspired by Instagram, offering a secure, localized, and modern web experience. It provides a comprehensive suite of social features including posts, stories, direct messaging, and robust authentication. The platform is built as a pnpm workspace monorepo, utilizing TypeScript, Node.js 24, and PostgreSQL. The vision is to create a leading social network tailored for the Iraqi and broader Arabic-speaking audience, emphasizing security, cultural relevance, and advanced features.

# User Preferences

I want iterative development.
I prefer detailed explanations.
I want to be asked before you make any major changes.
Do not make changes to the `artifacts/mockup-sandbox` directory.

# System Architecture

The project is structured as a pnpm workspace monorepo using TypeScript.

**Core Stack:**
- **Monorepo tool**: pnpm workspaces
- **Node.js**: 24
- **TypeScript**: 5.9
- **API**: Express 5
- **Database**: PostgreSQL + Drizzle ORM
- **Validation**: Zod (`zod/v4`), `drizzle-zod`
- **API codegen**: Orval (from OpenAPI spec)
- **Frontend**: React + Vite + Tailwind CSS + shadcn/ui
- **Internationalization**: i18next + react-i18next (29 languages)
- **Authentication**: Session-based (express-session + connect-pg-simple, httpOnly cookies)
- **Security**: AES-256-CBC encryption, bcryptjs (cost 12), helmet, svg-captcha, rate limiting, 2FA via email.

**Monorepo Structure:**
- `artifacts/`: Deployable applications (`api-server`, `instagram` frontend, `mockup-sandbox`).
- `lib/`: Shared libraries (`api-spec`, `api-client-react`, `api-zod`, `db`).

**UI/UX Design:**
- **Branding:** Custom gradient brand colors.
- **Typography:** Noto Kufi Arabic for RTL.
- **Responsiveness:** 3-tier breakpoints (mobile, tablet, desktop) with adaptive navigation and `dvh` units.
- **Design System:** shadcn/ui components, Tailwind CSS styling.
- **Internationalization:** Full i18n support for 29 languages with RTL auto-application.
- **Media Editor:** Canvas-based image manipulation for posts.

**Key Technical Features:**

- **Authentication & Security:** Session-based with httpOnly cookies, AES-256-CBC encryption for session IDs and in-transit passwords, login via username/email, SVG CAPTCHA, email verification, 2FA, multi-step password recovery, inline availability checks, strong password enforcement, rate limiting, device-based registration limits, and comprehensive security headers.
- **Admin Panel:** Separate authentication, redesigned dashboard with platform status and security metrics, user management (ban, unban, delete), post management, report resolution system, configurable settings (CAPTCHA, maintenance mode, AI moderation), detailed security panel, support ticket management, and admin account management.
- **Social Features:** Posts (images, captions, hashtags, mentions, various content types), heart-only likes, threaded comments with emoji reactions and GIF integration, follow/unfollow, user profiles, 24hr stories with viewer modal and reactions, vertical video Reels, content feed with "Following," "Favorites," "For You," and "Trending" tabs, content preference selection and behavior-based tracking, share functionality, comprehensive notifications, explore page with category filters, and advanced direct messaging with attachments, privacy controls, secret conversations, voice messages, AI translation, GIF search, read receipts, online status, block/report system, close friends, and audience selectors.
- **Settings:** Redesigned UI with search, icon-badged sidebar, visual privacy cards, advanced dark mode themes, and over 25 user-configurable settings covering profile, privacy, notifications, 2FA, linked accounts, and content preferences.
- **Groups System:** Full community group functionality including creation with categories, public/private settings, admin/member roles, join requests, group posts with media, temporary posts, pinning, likes/comments, group chat, broadcast notifications, audit logs, and customizable posting permissions.
- **AI Integration:** AI-powered content classification (20 categories) for posts with keyword matching and OpenAI fallback, enhanced "For You" feed algorithm with weighted preference scoring, interests dashboard, smart trending notifications, suggested accounts, and AI-powered content moderation for posts and comments (Arabic & English).
- **File Uploads:** Multer-based uploads for post media (10MB), message attachments (images 10MB, videos 50MB, files 25MB), and avatars, with blocked dangerous file types.

# External Dependencies

- **PostgreSQL**: Primary database.
- **Drizzle ORM**: Database interaction.
- **Orval**: API code generation.
- **Zod**: Schema validation.
- **React Query**: Frontend data fetching and caching.
- **Tailwind CSS**: Styling.
- **shadcn/ui**: UI components.
- **i18next**, **react-i18next**: Internationalization.
- **express-session**, **connect-pg-simple**: Session management.
- **bcryptjs**: Password hashing.
- **helmet**: Security headers.
- **svg-captcha**: CAPTCHA generation.
- **Resend (via Replit Connector)**: Primary email service.
- **SMTP fallback**: Gmail, Outlook, Yahoo, iCloud, Zoho for email.
- **Tenor API**: GIF search (server-side proxied).
- **ip-api.com**: IP geolocation.
- **OpenAI (via Replit AI Integrations proxy)**: AI content moderation.
- **Multer**: File uploads.