---
name: "project-init"
description: "Stiller spørsmål om produktet og fyller inn .claude/CLAUDE.md basert på svarene."
argument-hint: "Valgfri: kort beskrivelse av produktet"
user-invocable: true
disable-model-invocation: false
---

## Brukerinput

```text
$ARGUMENTS
```

Hvis brukeren har gitt en beskrivelse via argumenter, bruk den som utgangspunkt. Ellers start fra scratch.

## Gjennomføring

Still følgende spørsmål til brukeren, ett om gangen. Vent på svar før du går videre.

### Spørsmål 1 — Produktbeskrivelse

Spør:

> **Hva er produktet, og hvem er det for?**
> (Eks: "En nettside for å holde oversikt over treningsøkter, for folk som vil trene mer strukturert")

Vent på svar. Lagre svaret som `PRODUKTBESKRIVELSE`.

### Spørsmål 2 — Mål

Spør:

> **Hva skal produktet løse? Hva er det viktigste problemet det tar tak i?**
> (Eks: "Gjøre det enkelt å logge og følge opp trening uten å bruke kompliserte apper")

Vent på svar. Lagre svaret som `MÅL`.

### Spørsmål 3 — Målgruppe

Spør:

> **Hvem er målgruppen? Beskriv gjerne en typisk bruker.**
> (Eks: "Voksne 25–45 år som er aktive mosjonister, ikke eliteutøvere")

Vent på svar. Lagre svaret som `MÅLGRUPPE`.

### Spørsmål 4 — Stack (valgfritt)

Spør:

> **Hvilken teknologi skal brukes? Trykk Enter for å hoppe over.**
> (Eks: "React, Node.js, PostgreSQL")

Vent på svar. Lagre svaret som `STACK`. Hvis tomt, behold eksisterende placeholder.

## Skriv til .claude/CLAUDE.md

Etter at alle spørsmål er besvart, oppdater filen `.claude/CLAUDE.md` med svarene.

Bruk dette som mal — erstatt kun seksjonene som er besvart:

```markdown
# Prosjektinstruksjoner

## Produktbeskrivelse
{PRODUKTBESKRIVELSE}

## Mål
{MÅL}

## Målgruppe
{MÅLGRUPPE}

## Prosjekt
[Beskriv hva prosjektet er]

## Stack
{STACK eller "[Beskriv teknologi som brukes]"}

## Koderegler
- Skriv enkelt og lesbart
- Kommenter hvorfor, ikke hva
- En funksjon gjør én ting

## Mappestruktur
- src/ — kildekode
- docs/adr/ — arkitekturbeslutninger
- tests/ — tester
```

Skriv hele filen på nytt med de faktiske svarene innsatt.

## Ferdig

Bekreft til brukeren at `.claude/CLAUDE.md` er oppdatert, og vis de tre første seksjonene i en kort oppsummering.

Foreslå at brukeren kjører `/speckit-specify` for å starte med en feature-spesifikasjon.
