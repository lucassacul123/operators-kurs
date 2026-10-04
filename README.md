# Operators kurs

Kurssidene til Operators på **kurs.operators.no**. Ren HTML med ett felles stilark. Ingen byggesteg.

Repoet er offentlig og skal bare inneholde det som uansett er synlig på nettsiden. Eierskap, fakturaflyt, tilganger og interne rutiner ligger ikke her. Søknader ligger i Tally og skal aldri inn i repoet.

## Struktur

```
/                     -> videresender til aktivt kurs (se vercel.json)
/b2b-salg/            -> kursside, én mappe per tema
/personvern/          -> felles personvernerklæring for alle kurs
/404.html
/assets/operators.css -> felles stilark (Operators-tokens v3.2, én lilla)
/assets/fonts/        -> Archivo og IBM Plex Mono, selvhostet (SIL OFL)
/assets/img/<tema>/   -> bilder per kurs
/vercel.json          -> videresendinger, rene URL-er, cache
```

Adressen er tema, ikke dato. Neste kull av samme kurs bruker samme adresse, slik at delte lenker fortsatt virker.

## Nytt kurs: sjekkliste

1. Kopier mappen til et eksisterende kurs, for eksempel `b2b-salg/`, til `/<tema>/`.
2. Legg bilder i `/assets/img/<tema>/`. Maks ca. 1600 px bredde, JPEG kvalitet rundt 70.
3. Skriv innholdet. Følg Operators-merkevaren: ingen utropstegn, tall fremfor adjektiver, ingen påstander som ikke er bekreftet.
4. Få innholdet godkjent før publisering.
5. Dupliser Tally-skjemaet. Sett stengedato lik søknadsfristen. Behold lenken til personvernerklæringen.
6. Bytt skjema-ID i alle `data-tally-open`- og `https://tally.so/r/`-lenker på den nye siden.
7. Oppdater `canonical`, `og:url` og `og:image` i `<head>`.
8. Skal det nye kurset være forsiden, endre videresendingen i `vercel.json`.
9. Legg lenke til kurset i Beehiiv (toppmeny eller Events).
10. Sjekk siden på mobil og desktop før den deles.

Endres behandlingen av personopplysninger, oppdater `/personvern/` og datoen øverst på siden.

## Merkevare

Kilden er Operators brand spec (v3.4-purple). Kortversjonen:

- To skrifter: Archivo (språk) og IBM Plex Mono (data: datoer, priser, etiketter).
- Tre farger: ink, paper og én lilla `#8252AB`. Ingen toner, ingen gradienter.
- Lilla er aldri tekst på mørk bakgrunn, og under fem prosent av flaten.
- Venstrejustert. Maks 4 px hjørneradius. Ingen tekst på bilder.
- Bruk `var(--op-*)` i CSS, aldri hex direkte i komponenter.

## Publisering

Push til `main` publiserer automatisk via Vercel. Domenet `kurs.operators.no` peker til Vercel med en CNAME-oppføring.
