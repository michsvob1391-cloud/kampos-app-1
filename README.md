
# Kampos App (PWA prototyp)

Jednoduchá appka s přihlášením (Supabase), stránkami **Oznámení**, **Rezervace** a **Admin**.
Pro produkční použití nastavte ještě doménu a notifikace; tohle je prototyp.

## Rychlý start

1) Vytvoř `.env` soubor v kořeni projektu a doplň:
```
VITE_SUPABASE_URL=https://YOUR-PROJECT.supabase.co
VITE_SUPABASE_ANON_KEY=YOUR_ANON_KEY
```
2) Instalace a spuštění (lokálně):
```
npm i
npm run dev
```
3) Nasazení na Vercel:
- Připoj repo (GitHub) ve Vercelu → New Project → Import.
- V **Project → Settings → Environment Variables** nastav `VITE_SUPABASE_URL` a `VITE_SUPABASE_ANON_KEY`.
- Deploy.

## Přihlášení
- Přihlaš se přes **magický odkaz** (e-mail).
- Do tabulky `users` vlož svůj e-mail s rolí `admin`:
```
insert into users (email, role) values ('tvuj@email.cz', 'admin');
```

## RLS očekávání
- announcements: čtení všichni, vkládání jen admin.
- reservations: čtení všichni, vkládání/mazání jen uživatel pro své záznamy.
- users: správa jen admin (nepoužívá se z UI, jen pro kontrolu role).

## Poznámky
- Jednoduchý service worker je aktivní a spolu s manifestem dělá z appky PWA.
- Ikony jsou placeholdery; nahraď je svým logem v `public/icons/`.
