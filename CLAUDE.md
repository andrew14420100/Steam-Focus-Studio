# CLAUDE.md — STEAM FOCUS STUDIO

## Missione
Costruire in questo repository un'applicazione Windows 11 chiamata **STEAM FOCUS STUDIO**: una redazione multi-agente per creare video giornalistici gaming professionali, con il massimo livello possibile di automazione, elaborazione locale e costo software pari a 0 €.

Claude Code deve lavorare **dentro questo repository**, versionare ogni fase, mantenere la documentazione aggiornata, eseguire test reali e non dichiarare mai completata una funzione che è soltanto simulata.

## Vincoli non negoziabili
- Nessuna API AI a pagamento obbligatoria e nessun abbonamento obbligatorio per l'uso normale.
- Prima scelta: modelli e motori eseguiti localmente. Servizi online facoltativi devono essere chiaramente marcati e disabilitati per default.
- Target: Windows 11, GPU NVIDIA RTX 5070 Ti 16 GB come configurazione di riferimento, ma l'app deve degradare in modo controllato quando una GPU o un modello non è disponibile.
- Video finale 4K UHD 3840×2160. Distinguere **sorgente nativa 4K** da upscale di sorgenti inferiori.
- Filmati pertinenti alla notizia, provenienza tracciabile e condizioni d'uso registrate. Mai aggirare DRM, login, paywall o limiti di download né violare termini di piattaforme.
- Non è garantita la disponibilità di filmati 4K riutilizzabili per ogni notizia: cercare alternative legittime e bloccare o marcare la produzione se manca un requisito.
- Pubblicazione pubblica automatica disattivata per default. Prima consegna in cartella locale e revisione; upload YouTube facoltativo.
- Mai committare segreti, token OAuth, chiavi, credenziali, modelli, cache o grandi file multimediali.
- Verificare licenze e uso commerciale di ogni dipendenza, modello e asset prima dell'integrazione.
- Non cancellare o riscrivere in blocco codice esistente senza ispezione e motivazione documentata.

## Metodo di lavoro obbligatorio
1. Ispeziona repository, ambiente, versioni degli strumenti e hardware; crea `docs/ENVIRONMENT.md` senza esporre dati sensibili.
2. Leggi README e tutti i file in `docs/`. Conferma o aggiorna architettura, roadmap, licenze e test.
3. Implementa **una fase alla volta**, con commit piccoli e descrittivi. Non fermarti alla sola pianificazione: dopo l'audit implementa la prima fase concreta e prosegui dove possibile.
4. Per ogni funzione distingui: implementata, testata, parziale, simulata o bloccata. Non aggiungere pulsanti finti o dati demo spacciati per reali.
5. Usa logging, timeout, retry limitati, cache, checkpoint, cancellazione e ripresa dopo crash.
6. Quando Internet, una fonte, una licenza o un modello manca, dichiara il limite e non inventare risultati.
7. Prima di dire che una fase è completa, esegui i test pertinenti e riporta comandi ed esiti reali.
8. Non chiedere all'utente di svolgere manualmente le fasi che il progetto promette di automatizzare. Chiedi intervento solo per autorizzazioni, diritti, credenziali o decisioni editoriali veramente necessarie.
9. Mantieni README, roadmap e documentazione di installazione aggiornati a ogni fase.

## Architettura multi-agente
Implementa ruoli specializzati coordinati da un orchestratore deterministico. Gli agenti possono condividere lo stesso LLM locale per risparmiare VRAM; usa strumenti deterministici per task che non richiedono un LLM.

1. **Direttore/Orchestratore** — macchina a stati, dipendenze, checkpoint, retry, blocchi e ripresa.
2. **News Scout** — notizie da RSS, pagine ufficiali e fonti pubbliche consentite; registra URL e date.
3. **Fact Checker** — confronta fonti, separa fatti confermati e indiscrezioni, registra evidenze.
4. **Video Scout** — cerca trailer, gameplay, press kit e video scaricabili da fonti autorizzate; registra licenza e crediti.
5. **Asset Inspector** — ffprobe e analisi locale di codec, durata, frame rate, risoluzione, audio; distingue nativo 4K/upscale/risoluzione inferiore.
6. **Story Editor** — copione originale italiano da notiziario gaming, con claim e fonti.
7. **Director/Storyboarder** — scaletta frase-per-frase con asset e timecode pertinenti; vietato usare footage casuale solo per riempire.
8. **Voice Agent** — TTS locale configurabile, rigenerazione per segmento e dizionario di pronuncia.
9. **Subtitle Agent** — SRT/VTT sincronizzati e controllati.
10. **Audio Engineer** — mix voce/musica/SFX, ducking e normalizzazione; solo audio con diritti documentati.
11. **Video Editor/Renderer** — template STEAM FOCUS, compositing, titoli, transizioni e render 4K con strumenti idonei.
12. **QA Agent** — controlla media, sincronizzazione, frame neri, durata, fonti, licenze e corrispondenza copione/scene.
13. **Packaging Agent** — thumbnail, titolo, descrizione, capitoli, sottotitoli e crediti; upload YouTube opzionale.

Gli agenti comunicano tramite oggetti strutturati versionati e database locale, non solo testo libero. Registrare input, output, stato, durata, errori e file generati di ogni task.

## Stack da valutare, non adottare alla cieca
- Python per orchestrazione, agenti, API locali e job runner.
- SQLite per notizie, fonti, asset, licenze, copioni, storyboard, produzioni e log.
- UI desktop o web locale con dashboard, stato agenti, storyboard e anteprima; scegliere stack semplice e mantenibile su Windows.
- Ollama per LLM locale, selezionando modelli che funzionino con 16 GB VRAM senza scaricare modelli enormi automaticamente.
- FFmpeg/ffprobe per media probe, montaggio deterministico, encoding, mixaggio e QA.
- Rilevare CosyVoice e Whisper/faster-whisper già eventualmente installati, ma riutilizzarli solo dopo aver verificato installazione, endpoint, licenza e qualità italiana.
- OpenMontage/OpenFilm possono essere valutati ma non devono diventare dipendenze obbligatorie prima di aver verificato licenza, stabilità, installazione e utilità reale.
- Per ricerca media preferire feed, pagine ufficiali e fonti pubbliche consentite. Non promettere una ricerca web universale gratuita.

## Workflow end-to-end richiesto
Un comando principale **Genera notiziario** deve:
1. raccogliere notizie per intervallo e argomenti configurabili;
2. deduplicare e classificare rilevanza;
3. verificare fonti e date;
4. selezionare notizie e produrre copione con riferimenti;
5. cercare media pertinenti a ogni claim;
6. registrare licenza/diritti e qualità tecnica degli asset;
7. creare storyboard e decision list di montaggio;
8. generare voce e sottotitoli;
9. montare video, titoli, grafica, musica e SFX;
10. renderizzare 3840×2160 con frame rate configurabile;
11. eseguire QA e correggere automaticamente errori correggibili;
12. produrre MP4, SRT, VTT, thumbnail, descrizione, capitoli e report delle fonti;
13. salvare il progetto per modifiche e ripresa del render;
14. registrare provenienza e condizioni d'uso di ogni asset.

Supportare sia una singola notizia sia un notiziario multi-notizia. Durata configurabile. Mostrare progresso, stato agenti, errori e risorse utilizzate.

## Requisiti 4K e stati di blocco
- Output richiesto 3840×2160.
- Distinguere risoluzione sorgente, risoluzione render e upscale; verificare con ffprobe.
- Non usare asset con diritti sconosciuti come se fossero autorizzati.
- Se mancano asset 4K richiesti o diritti verificabili, usare `BLOCKED_MISSING_4K_ASSET`, `BLOCKED_LICENSE_UNKNOWN` o stati simili. Mai sostituire silenziosamente un asset inferiore.
- Non dichiarare un controllo semantico o visivo AI se è stato eseguito soltanto un controllo tecnico.

## UI e identità
- Brand: STEAM FOCUS.
- Stile: dark premium, nero/antracite, bianco e blu elettrico; editoriale, leggibile, sobrio.
- Sezioni: Dashboard, Newsroom, Libreria media, Copioni, Storyboard, Produzioni, Template, Modelli locali, Licenze, Impostazioni, Log.
- Card degli agenti con stati `idle`, `running`, `waiting`, `failed`, `completed`, `blocked`.
- Supportare pausa, annullamento, ripresa, riesecuzione di un singolo agente e visualizzazione dei file intermedi.

## Sicurezza e pubblicazione
- Segreti solo in variabili d'ambiente o archivio credenziali locale; `.env` ignorato da Git.
- Non caricare video, cache, modelli, token o grandi media su GitHub.
- Upload YouTube disattivato finché l'utente non configura OAuth ufficiale; default solo export locale.
- La presenza di un video online non equivale a permesso di riutilizzo.

## Roadmap
- Fase 0: audit repository/ambiente/hardware/modelli e documentazione.
- Fase 1: fondazioni, configurazione, SQLite, macchina a stati, log, checkpoint, CLI e test.
- Fase 2: newsroom, RSS, dedupe, fact-check assistito e copione con fonti.
- Fase 3: media research, diritti, indicizzazione, ffprobe e download consentito.
- Fase 4: TTS locale, SRT/VTT e audio.
- Fase 5: storyboard, template e rendering 4K.
- Fase 6: QA, retry e report.
- Fase 7: UI completa.
- Fase 8: packaging Windows e YouTube opzionale.

## Regola finale
Leggi prima `README.md` e `docs/`. Esegui audit e aggiorna la roadmap, poi implementa la prima fase concreta e prosegui in modo incrementale. Al termine riporta file modificati, comandi eseguiti, test passati/falliti e prossimo passaggio. Non dichiarare mai completamento senza prove.
