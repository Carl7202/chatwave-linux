# ChatWave

A WhatsApp-inspired messaging app. The frontend is a single `index.html` hosted on GitHub Pages; Supabase provides accounts, persistent messages, and real-time updates.

## Features

- **Invite-code gated account creation** — new users must enter an existing ChatWave invite code first
- Custom **fictional ChatWave number** chosen by the user; it is not a real phone number and never receives SMS or calls
- Log in with the fictional ChatWave number and password; no email address is required from users
- Invite code is also generated for each account so members can invite new people
- Add friends by their fictional ChatWave number
- New accounts automatically open a direct conversation with the person whose invite code they used
- Persistent message history and live incoming messages
- Responsive desktop/mobile layout plus an installable Progressive Web App (PWA) shell
- Group chats with named groups and adding members (up to 20)
- Presence status (online, idle, Do Not Disturb, invisible) and custom status
- Live typing indicators, read receipts, message edit/delete, and emoji reactions
- Private file/image/GIF/audio/video/document sharing with signed URLs and a 25 MB limit
- Voice calls with incoming ringtone, voicemail recording/playback, amplified audio, and one-to-one screen sharing
- Local soundboard effects that can also be routed into a connected voice call
- Discord, Linux Mint, AMOLED, and neon-purple themes
- Desktop notifications (after permission is granted), profile controls, user blocking and reporting
- Database row-level security: only conversation members can read messages or send as themselves
- Uses a Supabase **publishable** key in the browser; the service-role key is used only inside the Edge Function

## Live site

https://carl7202.github.io/chatwave-linux/

## Backend

- Supabase project: `ChatWave`
- Project ref: `dhylbrxixjrtqufqrnjh`
- Region: Europe (London)
- Tables: `profiles`, `conversations`, `conversation_members`, `messages`; invite codes are stored separately in the non-API `private` schema
- Edge Function: `chatwave-auth` handles invite-gated registration and number/password login
- Realtime publication includes messages, reactions, presence, and read receipts
- Private `chatwave-files` storage bucket for attachments
- Group creation/member management and privacy controls use database RPCs with authenticated access

The database schema and RLS policies are configured in the ChatWave Supabase project.

## User flow

1. Open the live site and enter a friend's invite code.
2. After the code is validated, choose a username, a **fictional ChatWave number**, and a password.
3. ChatWave creates the account and starts a conversation with the inviter.
4. Share your own invite code to invite another person.
5. Friends can find you later using your fictional ChatWave number and start a direct chat.

**Important:** Do not enter your real phone number. ChatWave numbers are fictional IDs used only inside this app; there is no phone service, SMS, or calling.

## Security notes

- RLS is enabled on public tables and on the private invite-code table.
- Registration and login use the `chatwave-auth` Edge Function. Its service-role key must remain in Supabase's server-side environment and must never be added to `index.html`.
- Invite codes are validated server-side again during registration.
- This is not end-to-end encrypted: Supabase stores message text and attachment metadata in a form the service can process. Blocking restricts new direct messages, and reporting stores a report, but there is not yet a full moderation dashboard. Voice calls are currently one-to-one; group voice calls are not implemented. The installable PWA is not a native Linux desktop package. Do not use ChatWave for highly sensitive information.

## Publish / update

GitHub Actions deploys the repository root to GitHub Pages whenever a commit is pushed to `main`. Check the [Actions tab](https://github.com/Carl7202/chatwave-linux/actions) if the site has not updated yet.
