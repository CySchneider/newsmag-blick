# newsmag-blick

Blick sperrt Cloudflare-Server (403), der Newsmag-Worker kann die Feeds nicht selbst holen.
Dieser GitHub-Job holt sie alle 30 Minuten und schickt sie an `POST https://newsmag.ch/api/push?key=PUSH_KEY`.
Der Worker verwendet den letzten Stand, solange er jünger als 90 Minuten ist (`/api/health` zeigt den Status unter den Blick-Feeds).

Secret `PUSH_KEY` muss im Repo (Settings → Secrets → Actions) und im Worker (`npx wrangler secret put PUSH_KEY`) gleich sein.
