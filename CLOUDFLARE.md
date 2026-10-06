# Publicera Kumgang på Cloudflare

## Snabbast från Terminal

Öppna projektmappen och kör:

```bash
npm install
npx wrangler login
npm run deploy:cloudflare
```

Efter inloggningen bygger kommandot hela sidan och publicerar Workern
`kumgang-taekwondo`. Terminalen visar den färdiga `workers.dev`-adressen.

## Automatisk publicering från GitHub

1. Lägg projektmappen i ett GitHub-repository.
2. Välj **Workers & Pages** i Cloudflare och anslut repositoryt.
3. Ange `npm run build` som build command.
4. Ange `npx wrangler deploy --config dist/server/wrangler.json` som deploy command.
5. Använd `/` som root directory och Node.js 22.13 eller senare.

## Koppla domänen

Öppna Workern `kumgang-taekwondo` och välj **Settings → Domains & Routes**.
Lägg därefter till Kumgangs domän som custom domain.

Publicera projektet som en Cloudflare Worker. Serverdelen behövs för den framtida
Svenskalag-integrationen, även om dagens data fortfarande är mockad.
