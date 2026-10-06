# Kumgang Taekwondo – lokal prototyp

En komplett responsiv webbprototyp med startsida, träningsgrupper, schema, nyheter,
tävling/resultat, om klubben, kontakt/prova-på och en interaktiv medlemssida.

## Starta lokalt

Krav: Node.js 22 eller senare.

```bash
npm install
npm run dev
```

Öppna adressen som visas i terminalen, normalt `http://localhost:5173`.

## Publicera på Cloudflare

Sidan körs som en Cloudflare Worker med statiska bilder och typsnitt kopplade som
Workers Assets. Node.js 22.13 eller senare ska användas vid bygget.

### Från din dator

```bash
npm install
npx wrangler login
npm run deploy:cloudflare
```

Cloudflare visar den publicerade `workers.dev`-adressen när uppladdningen är klar.

### Från GitHub i Cloudflare

Skapa en Worker från ett Git-repository och använd:

- Build command: `npm run build`
- Deploy command: `npx wrangler deploy --config dist/server/wrangler.json`
- Root directory: `/`
- Node.js: `22.13.0` eller senare

Koppla sedan den riktiga domänen under **Workers & Pages → kumgang-taekwondo →
Settings → Domains & Routes**.

Detta projekt ska publiceras som en **Worker**, eftersom bygget innehåller
serverdelen som senare kan anslutas till Svenskalag. Ladda därför inte bara upp
en lös HTML-mapp i Pages.

## Svenskalag-integration

All föreningsdata går genom `lib/svenskalag/SvenskalagClient`. Nu används
`mock-client.ts`. När API- och SSO-uppgifter finns ersätts implementationen med
en serverbaserad klient. API-nycklar ska lagras på serversidan och aldrig i
webbläsarkoden.

Demofunktioner:

- filtrerbart träningsschema
- demo-inloggning till Mina sidor
- personligt schema och svarsbar kallelse
- prova-på-formulär med lokalt bekräftelseläge
