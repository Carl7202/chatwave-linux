# ChatWave Linux

A WhatsApp-inspired, phone-free chat interface hosted on GitHub Pages.

## Included in this first version

- Display-name setup without a phone number
- Create local conversations
- Search chats and filter unread chats
- Send messages, emoji, and timestamps
- Saves demo data in this browser using localStorage
- Responsive desktop and mobile layout

## Important limitation

This is currently a **local demo**, not yet an internet messaging service. Messages are stored in this browser on this device; other people cannot see them. GitHub Pages hosts static files and does not provide a shared database or live messaging by itself.

For real online conversations between friends, the next step is to connect a shared backend such as Supabase (database, authentication, and Realtime), configure row-level security, and add friend/chat membership rules. Never put a Supabase service-role key or other secret in frontend code.

## Publish with GitHub Pages

1. Open this repository's **Settings**.
2. Choose **Pages** from the sidebar.
3. Under **Build and deployment**, choose **Deploy from a branch**.
4. Select branch `main` and folder `/(root)`, then click **Save**.
5. Wait for GitHub to publish the site.

Expected site URL: https://carl7202.github.io/chatwave-linux/

The app is in `index.html` at the repository root.
