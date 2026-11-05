# PRH Account Setup

The sign-in and account-creation forms on `index.html` use Supabase Auth. Configure the Supabase project before creating or signing in to an account.

## Configure account sign-in

1. In Supabase project settings, enable Email authentication. Set the site URL and allowed redirect URLs to the HTTPS address where you host this app. If email confirmation is enabled, new users must confirm their email before signing in.
2. Set the project URL and public anon/publishable key in [`supabase-config.js`](supabase-config.js). Never put a `service_role` key in browser code.
3. Host this folder on an HTTP(S) origin and open `index.html`. Supabase Auth is not intended to be used from `file://`.
4. Google and Apple sign-in are optional; enable and configure those providers in Supabase before using their buttons.

Existing browser-only accounts can be connected when signing in from the browser where they were created, using the same email and password. New account passwords are managed by Supabase Auth, not stored in the app's local account list.

## Dashboard limitations

The jobs, tasks, spins, referrals, balances, and request/admin screens are the original browser-local simulator. Their data is stored in that browser and is not synced to the Supabase account. No bank or mobile-money payment is processed. Do not treat displayed balances or rewards as cash.

The SQL schema in [`supabase/schema.sql`](supabase/schema.sql) defines a separate Supabase wallet ledger, but the original dashboard and local admin page do not use that ledger.
