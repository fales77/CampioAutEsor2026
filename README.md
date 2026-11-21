# Esordienti 2° anno – Girone L – Autunno 2026

Pagina web in un unico file HTML che mostra calendario, risultati e classifica automatica del campionato **Esordienti 2° anno, Girone L, Autunno 2026** (sola andata, 9 squadre, 9 giornate).

Nessuna dipendenza esterna: basta aprire il file `.html` con un qualsiasi browser.

## Contenuto

- **Calendario**: le 9 giornate (dal 10/10/26 al 05/12/26) con le partite e la squadra che riposa.
- **Classifica**: calcolata in automatico dai risultati inseriti.
- **Giornata corrente**: viene evidenziata con l'etichetta "OGGI" in base alla data del giorno in cui si apre la pagina. Le giornate passate sono leggermente attenuate.

## Come inserire i risultati

Tutti i dati si trovano nel blocco `DATA` all'inizio dello `<script>`. Ogni partita è scritta così:

```js
["SQUADRA CASA", "SQUADRA OSPITE", "gol casa", "gol ospite"]
```

- Partita giocata: numeri interi maggiori o uguali a 0, ad esempio `"9","5"`.
- Partita non ancora giocata: `"-","-"`.

Attenzione: un valore negativo come `"-9"` non è valido e fa considerare la partita come non giocata.

## Criteri di classifica

Vittoria 3 punti, pareggio 1, sconfitta 0. A parità di punti si applicano nell'ordine:

1. scontro diretto (punti negli incontri tra le squadre interessate)
2. gol fatti (GF)
3. differenza reti (DR)
4. nome della squadra, in ordine alfabetico

Le colonne mostrate sono: Pu (punti), G, V, N, P, GF, GS, DR.

## Personalizzare i colori

I colori sono definiti nel CSS in formato `rgba(R,G,B, trasparenza)`. Gli accenti principali sono:

- **Colore primario** (sfondo sfumato, header, "OGGI", numero di giornata): `13,148,136` (teal).
- **Colore secondario** (punti in classifica e alone dello sfondo): `251,113,133` (corallo).

Per cambiarli basta cercare quei valori nel file e sostituirli con altri tre numeri RGB.

## Versioni

| File | Palette |
|------|---------|
| `v01` | Verde scuro |
| `v02` | Blu elettrico + arancio |
| `v03` | Azzurro + lime |
| `v04` | Teal + corallo |

## Struttura del file

- `<style>`: tutta la grafica (tema scuro, layout responsive).
- `DATA`: squadre, giornate e risultati.
- Funzioni JavaScript: `renderCalendar()`, `computeStandings()`, `renderStandings()` e `highlightCurrentRound()`, richiamate da `refresh()`.
