# STEAM FOCUS STUDIO

Redazione multi-agente per la produzione automatizzata di video gaming news, con priorità a strumenti locali gratuiti, fonti tracciabili, voce italiana, sottotitoli e rendering 4K.

> Stato iniziale: specifica e scaffolding. Non è ancora una pipeline funzionante. Le funzionalità devono essere implementate e testate progressivamente.

## Obiettivo

Costruire su Windows 11 un'applicazione desktop/local web che coordini agenti specializzati per ricerca notizie, verifica, ricerca di filmati autorizzati, scrittura del copione, voce, sottotitoli, regia, montaggio, controllo qualità e preparazione alla pubblicazione.

## Requisiti principali

- Nessun servizio AI o API a pagamento obbligatorio.
- Elaborazione locale dove possibile.
- Output 4K UHD (3840×2160), con distinzione esplicita tra sorgente nativa 4K e upscale.
- Fonti e condizioni di riutilizzo tracciate per tutti gli asset.
- Nessun aggiramento di restrizioni dei siti.
- Upload YouTube facoltativo; pubblicazione disattivata di default.
- Nessun modello, video, cache, token o segreto versionato nel repository.

## Avvio dello sviluppo con Claude Code

1. Clona questa repository sul PC Windows.
2. Apri un terminale nella cartella del progetto e avvia `claude`.
3. Chiedi a Claude Code di leggere `CLAUDE.md`, `docs/ROADMAP.md` e `docs/ARCHITECTURE.md`, quindi di seguire la fase 0.
4. Non dare per completata una fase finché i test e i criteri di accettazione non sono stati eseguiti.

## Documentazione

- `CLAUDE.md`: istruzioni operative complete per Claude Code.
- `docs/ARCHITECTURE.md`: architettura preliminare.
- `docs/ROADMAP.md`: fasi di sviluppo.
- `docs/LICENSING.md`: vincoli per software, modelli e media.
- `docs/ACCEPTANCE_TESTS.md`: criteri e test del progetto.

## Avvertenza

Il progetto non può garantire che ogni notizia abbia filmati 4K legalmente riutilizzabili. La pipeline deve segnare il blocco quando mancano asset idonei, senza inventare risorse o presentare upscale come sorgente nativa 4K.
