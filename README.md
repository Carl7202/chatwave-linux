# opix

A fresh, minimal messaging-app rebuild.

## Current state

- New single-file frontend at `index.html`
- New opix branding, manifest, icon and service-worker cache
- The previous ChatWave application data has been cleared from the connected Supabase database
- The current website is an interface preview; authentication, friend discovery, synced messages and realtime features are not connected yet

## Hosting

GitHub Pages deploys the repository root from the existing Actions workflow.

## Backend

The existing Supabase project is retained as an empty project shell. Its old Edge Functions and private storage buckets have not been removed. A new Opix schema and backend need to be created before enabling real accounts or cross-device messaging.
