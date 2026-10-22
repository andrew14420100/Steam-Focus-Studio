# Prompt operativo per Claude Code — STEAM FOCUS STUDIO

Lavora esclusivamente nella repository GitHub corrente **andrew14420100/Steam-Focus-Studio**. Prima di ogni modifica controlla `git status` e non sovrascrivere modifiche dell'utente. Leggi `CLAUDE.md`, `README.md` e tutti i documenti in `docs/`.

Costruisci una redazione multi-agente che produca video giornalistici gaming in italiano. Deve usare strumenti locali gratuiti dove possibile, senza API AI a pagamento obbligatorie. Gli agenti specializzati possono condividere un modello LLM locale, coordinati da un orchestratore con macchina a stati, checkpoint, log, retry limitati e interfacce strutturate.

## Ruoli
Direttore/orchestratore; ricerca notizie; verifica fatti; ricerca filmati; verifica asset/risoluzione/licenze; giornalista/copione; regia/storyboard; voce italiana; sottotitoli; tecnico audio; montaggio/rendering; controllo qualità; packaging YouTube.

## Requisiti non negoziabili
- Output finale 3840×2160; verificare la risoluzione effettiva con ffprobe.
- Distinguere sorgente nativa 4K da upscale.
- Cercare filmati specifici e pertinenti, preferendo fonti ufficiali/press kit e download legalmente consentiti.
- Non aggirare DRM, login, paywall, restrizioni di download o termini delle piattaforme.
- Conservare provenienza, licenze e crediti di ogni asset.
- Se manca un asset 4K nativo riutilizzabile o una prova sufficiente dei diritti, registrare uno stato blocked con motivo; non usare casualmente un video generico né fingere il completamento.
- Voce, sottotitoli, musica ed effetti devono essere gestiti da moduli distinti con test.
- Upload pubblico YouTube disabilitato di default; export locale sempre disponibile.
- Non committare video, modelli, database locali, cache o credenziali.

## Lavoro richiesto adesso
1. Esegui audit del repository, sistema Windows, versioni Python/Node/Git, FFmpeg/ffprobe, GPU, Ollama, modelli locali e possibili TTS/ASR già installati. Non includere token o dati sensibili nei report.
2. Crea o aggiorna `docs/ENVIRONMENT.md`, `docs/ARCHITECTURE.md`, `docs/ROADMAP.md`, `docs/LICENSING.md` e `docs/ACCEPTANCE_TESTS.md`.
3. Implementa subito una prima fase funzionante, non limitarti a scrivere una proposta. Inizia da configurazione, modelli dati, SQLite, orchestratore e test, poi prosegui con la prima integrazione reale compatibile con l'ambiente.
4. Mantieni commit piccoli e descrittivi. Esegui test dopo ogni fase e annota nel README i risultati effettivi.
5. Non costruire subito una grande UI se il backend non funziona. Nessun pulsante finto, nessun risultato mock spacciato per reale.
6. Se una dipendenza è costosa, ha licenza incompatibile o richiede un servizio a pagamento, cerca un'alternativa locale e documenta la decisione.
7. Non dichiarare una fase completata finché i test non sono passati. Se un test non può essere eseguito, riporta il motivo e lo stato parziale.
8. Alla fine riporta file cambiati, commit, test e prossimo step.

Il prodotto finale deve poter ricevere un comando come **Genera notiziario**, ricercare notizie e filmati, scrivere copione, generare voce e sottotitoli, montare e renderizzare in 4K, controllare il risultato e preparare i metadati. Procedi incrementando il sistema per fasi reali e verificabili.
