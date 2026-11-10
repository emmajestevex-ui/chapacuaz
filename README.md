# CHAPACUAZ IOS

Private client build with Supabase key activation and remote-only patches.

## What this build does

- Shows the app as `CHAPACUAZ IOS`.
- Requires a Supabase license key before opening the app.
- Consumes each key one time on the server and binds it to one iOS device ID.
- Re-checks the license on launch, foreground, and every 10 seconds while active.
- Syncs published remote files from Supabase Storage into CHAPACUAZ IOS' own app storage, using a versioned `target_path` so replacing the same route downloads only the changed file.
- Downloads only changed files, verifies SHA-256, and rolls back local content if an update fails.
- Adds a PC admin panel in `admin/` for uploading, replacing, disabling, deleting, and publishing content changes.
- Shows only the patches and files published in the remote manifest after activation.
- Lets the client use `Apply`, `Original`, and name editing only.
- Hides Files, Cleaner, Wallpapers, patch creation, import, export, and editing.

## Remote-only content

The IPA contains no base patch payloads. After activation, the app reads the
published remote manifest and downloads only the files that have been released
from the admin panel. Existing installations perform a one-time cleanup of the
old bundled projects; content published remotely is preserved and recreated
from the manifest.

Run `supabase/licenses_setup.sql` before using the app. It disables old numeric keys like `CHAPACUAZ-1`, adds secure key generation, and creates the admin RPC functions.

Run `supabase/remote_content_setup.sql` to enable remote content releases, `target_path` routing, and the `chapacuaz-content` Storage bucket. The iOS client and the PC panel both use the same Supabase project URL and publishable key; admin writes require Supabase Auth plus a row in `public.license_admins`.

See `CHAPACUAZ_BUILD_GUIDE.md` for Supabase setup and GitHub Actions build steps.
