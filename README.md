# ChatWave

A WhatsApp-inspired, phone-free messaging app. The frontend is a single `index.html` hosted on GitHub Pages; Supabase provides email/password accounts, persistent messages, and real-time updates.

## Features

- Email + password accounts (no phone number)
- Unique username that friends can search for
- Direct conversations created in the shared database
- Persistent message history and live incoming messages
- Responsive desktop/mobile layout
- Database row-level security: only conversation members can read messages or send as themselves
- Uses a Supabase **publishable** key in the browser; never expose a service-role/secret key

## Live site

https://carl7202.github.io/chatwave-linux/

## Backend

- Supabase project: `ChatWave`
- Project ref: `dhylbrxixjrtqufqrnjh`
- Region: Europe (London)
- Tables: `profiles`, `conversations`, `conversation_members`, `messages`
- Realtime publication includes `public.messages`

The database schema and RLS policies have been applied to the separate ChatWave project.

## One-time Supabase Auth setup

1. Open [ChatWave Auth URL Configuration](https://supabase.com/dashboard/project/dhylbrxixjrtqufqrnjh/auth/url-configuration).
2. Set **Site URL** to `https://carl7202.github.io/chatwave-linux/`.
3. Under **Redirect URLs**, add `https://carl7202.github.io/chatwave-linux/` and save.
4. In Authentication settings, leave email confirmation enabled if you want confirmation before first sign-in. A new account may need to click the confirmation link before signing in.

## Publish / update

GitHub Actions deploys the repository root to GitHub Pages whenever a commit is pushed to `main`. Check the [Actions tab](https://github.com/Carl7202/chatwave-linux/actions) if the site has not updated yet. The site URL is https://carl7202.github.io/chatwave-linux/.

## User flow

1. Open the live site and create an account with an email, password, and username (3–20 lowercase letters, numbers, or underscores).
2. Confirm the email if Supabase asks you to.
3. Sign in.
4. Use **＋** to search for a friend's username and start a direct chat.
5. Your friend creates their own account and signs in on their own device. Messages should appear live while both users are connected.

## Security notes

- RLS is enabled on every public table.
- Direct-conversation creation is handled by a restricted database function; clients cannot insert arbitrary conversation memberships.
- The browser key is intentionally a publishable key. Never paste a Supabase service-role key into `index.html`.
- This is a straightforward chat app, not end-to-end encrypted messaging. Do not use it for highly sensitive information.
