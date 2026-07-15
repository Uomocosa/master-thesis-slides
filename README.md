# Slide della Tesi Magistrale — Samuele Maggiori

Presentazione di discussione della tesi magistrale (Università di Siena) su una pipeline
computazionale per **predire e generare polimeri adsorbenti** ("spugne molecolari") per la
rimozione di contaminanti dalle acque reflue.

**➡️ Presentazione web (GitHub Pages):** <https://uomocosa.github.io/master-thesis-slides/>

**📎 Codice e metodologia completi:** [Uomocosa/master-thesis](https://github.com/Uomocosa/master-thesis)
— la tesi, la pipeline computazionale e il pacchetto `create_slides` che genera queste slide.

---

## Cosa contiene questo repo

| Percorso | Contenuto |
|----------|-----------|
| `Slide_Samuele_Maggiori.pptx` | La presentazione PowerPoint originale (con animazioni video incorporate). |
| `docs/` | La versione web statica servita da GitHub Pages (reveal.js). |
| `.github/workflows/pages.yml` | Workflow che pubblica `docs/` su GitHub Pages. |

## Come usare la versione web

Apri il sito e **clicca** (o usa le frecce / la barra spaziatrice) per avanzare.
Sulle slide con animazioni, il **click avvia il video** in sovrimpressione: un click lo fa
partire, il click successivo passa (all'eventuale seconda animazione e poi) alla slide
seguente — esattamente come nella modalità presentazione di PowerPoint.

## Come è stata creata

La presentazione è generata programmaticamente con **`python-pptx`** e le animazioni con
**`manim`**, nel pacchetto [`create_slides`](https://github.com/Uomocosa/master-thesis/tree/main/create_slides)
del repo `master-thesis` (vedi il relativo `CLAUDE.md` per i dettagli dello stile UniSi,
degli sfondi con lo skyline di Siena e delle scene manim).

La versione web è prodotta dallo script **`create-web-export`** dello stesso pacchetto, che:

1. renderizza ogni slide del `.pptx` in un PNG tramite l'automazione COM di PowerPoint
   (`create_slides/tools/render_pptx.ps1`);
2. estrae i video `.mp4` incorporati e la loro posizione esatta sulla slide;
3. genera un sito **reveal.js** completamente autonomo (nessuna CDN) in cui ogni slide è
   l'immagine renderizzata e i video sono sovrapposti come elementi cliccabili nella loro
   posizione originale.

Poiché il rendering richiede PowerPoint, il sito in `docs/` è **costruito in locale e
committato**; il workflow di GitHub Actions si limita a pubblicarlo (non compila nulla).

Per rigenerarlo, dal repo `master-thesis`:

```bash
cd create_slides
uv run create-web-export   # scrive in ../../master-thesis-slides/docs/
```

## Abilitare GitHub Pages

1. Crea il repository su GitHub e fai `git push`.
2. **Settings → Pages → Build and deployment → Source: GitHub Actions.**
3. Al primo push su `main` il workflow pubblica il sito; l'URL compare nella pagina Pages.

> Nota: le slide della versione web sono immagini, quindi il testo non è selezionabile — è
> una scelta voluta per riprodurre fedelmente l'impaginazione di PowerPoint.
