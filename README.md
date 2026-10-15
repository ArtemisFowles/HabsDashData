# Sports Day Recorder

A simple phone-friendly web page for recording race finishing positions. Results are stored in Supabase.

## How it works

1. Enter a runner code (or switch to "Enter name" if they've forgotten it) and a finishing position.
2. Tap **Add to list**. Entries wait in a list on the phone so mistakes can be removed before sending.
3. Tap **Submit results** to send everything to Supabase. Each row stores the code or name, the position, and the date and time it was recorded.

If a submit fails (e.g. poor signal), the list is kept and can be retried. The list also survives a page refresh.

## Setup

1. In Supabase, open **SQL Editor**, paste in `supabase-setup.sql` and run it.
2. In Supabase, go to **Project Settings -> API** and copy the **Project URL** and the **anon public key**.
3. Open `index.html` and replace the two values at the top of the script:
   ```js
   const SUPABASE_URL = "https://YOUR-PROJECT-REF.supabase.co";
   const SUPABASE_ANON_KEY = "YOUR-ANON-PUBLIC-KEY";
   ```
4. Host it. GitHub Pages works well: repo **Settings -> Pages -> Deploy from branch -> main**. Then open the Pages link on a phone.

## Security note

The anon key is visible to anyone who opens the page, which is normal for Supabase. The database is protected by Row Level Security: the anon key can only **insert** rows, not read, change or delete them. View results from the Supabase dashboard. Never put the `service_role` key in this file.
