# Krambua – Varetelling

Eigen app for den årlege varetellinga til Krambua Bensin & Storkiosk AS.

- **Registrer sider:** éi rad per tellingsside med mva-sats (25 / 15 / 0 %) og sum inkl. mva. Summen kan skrivast som reknestykke (`12 450 + 3 210,50`).
- **Samandrag:** netto varelager (utan mva, etter avanse), fordeling per mva-sats og samanlikning med året før.
- **Eksport:** Word-samandrag, Excel-arbeidsbok og sikkerheitskopi (JSON).
- **Låsing:** ferdige år blir låste, så tala ikkje kan endrast ved eit uhell.

## Lagring
Kvart år ligg som `data/<år>.json` i dette repoet. Kvar endring blir ein commit, så heile historikken er tilgjengeleg under *History*. Appen held i tillegg ein lokal kopi i nettlesaren, og sender endringane opp når nettet er tilbake.

## Oppsett på ny eining
Opne appen og lim inn eit GitHub fine-grained token med tilgang til dette repoet (*Contents: Read and write*). Tokenet blir berre lagra i nettlesaren på den eininga, og aldri i repoet.

## Utrekning
- Eks. mva = sum inkl. mva ÷ (1 + mva-sats)
- Netto varelager = varelager utan mva × (1 − avanse). Standard avanse er 38 %.
