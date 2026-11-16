# Krambua – Varetelling

App for den årlege varetellinga til Krambua Bensin & Storkiosk AS. Rot-adressa sender vidare til appen.

- **Administrator:** https://kristoffertungesvik-stack.github.io/Krambua-varetelling/telling/ – butikkart med rom og reolar som kan redigerast og plasserast, teljing med strekkode, vekt → tal for skruar, mva-sats per linje, rapport til revisor/rekneskap (PDF og Excel), tellelister med strekkode, dobbelttelling-kontroll, lagerverdi mot sal per reol og plakatar med kople-kode.
- **Tilsette:** https://kristoffertungesvik-stack.github.io/Krambua-varetelling/telling/tilsett/ – berre kart og teljing, ingen kronebeløp. Telefonen blir kopla til med QR-koden «Kople til telefon» (Oppsett i administrator-versjonen) eller kople-plakaten. På iPhone må appen på heimeskjermen koplast til for seg med «📷 Skann kople-koden».
- Brukarhandbok: trykk **?** øvst i appen.

## Lagring
- Teljinga ligg i `data/telling-<kode>/` med éi fil per seksjon per eining (`J10__<eining>.json`) og `_meta__<eining>.json` for status, oppsett, rom og reolar. Kvar eining skriv berre sine eigne filer, så ingen kan skrive over kvarandre. Kvar endring blir ein commit, så heile historikken er tilgjengeleg under *History*.
- Varelista frå PCK ligg i `data/vareliste.json`.
- Kvar linje blir lagra med ein gong i databasen i nettlesaren (IndexedDB), sendt til GitHub høgst eitt minutt seinare, og appen tek lokale kopiar kvart 15. minutt. Ventande linjer blir viste med ⏳.
- `data/arkiv/2025.json` er varetellinga for 2025 frå den førre appen (173 tellingssider, låst). Ho blir teken vare på som rekneskapsdokumentasjon.

## Oppsett på ny eining
Opne administrator-versjonen og lim inn eit GitHub fine-grained token med tilgang til dette repoet (*Contents: Read and write*). Tokenet blir berre lagra i nettlesaren på den eininga, aldri i repoet.

## Utrekning
- Eks. mva = sum inkl. mva ÷ (1 + mva-sats)
- Kostverdi = eks. mva × (1 − avanse). Standard avanse er 38 %, med eigen avanse per rom. Har vara innkjøpspris frå PCK, blir den brukt.

## Teknisk
`telling/tilsett/index.html` er same fil som `telling/index.html`, berre med `const MODUS = 'tilsett';`.
