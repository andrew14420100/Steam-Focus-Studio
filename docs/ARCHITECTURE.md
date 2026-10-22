# Architettura preliminare

## Principi
- Orchestratore deterministico con macchina a stati, checkpoint e retry limitati.
- Agenti basati su ruoli, strumenti espliciti e contratti JSON versionati.
- LLM locale condiviso dove possibile; FFmpeg/ffprobe per i compiti media deterministici.
- SQLite come archivio locale per notizie, fonti, asset, licenze, copioni, storyboard, produzioni, job e log.
- I media intermedi sono in cartelle di lavoro locali fuori dal controllo versione.
- Nessun asset passa alla produzione finale senza una provenienza e una condizione d'uso registrate.

## Componenti logici
1. **UI** — dashboard produzione, stato agenti, storyboard e anteprima.
2. **API locale** — avvio, cancellazione, ripresa job e risultati.
3. **Orchestratore** — dipendenze agenti, retry, checkpoint e gestione errori.
4. **Newsroom** — feed RSS/pagine consentite, deduplicazione e fonti.
5. **Asset service** — ricerca, acquisizione consentita, hashing, probe, licenze e indicizzazione.
6. **Production service** — copione, storyboard, TTS, sottotitoli e rendering.
7. **QA service** — controlli tecnici e stato dei requisiti editoriali.
8. **Packaging** — MP4, SRT/VTT, miniatura, titolo, descrizione, capitoli e report asset.

## Contratti task
Ogni task deve avere: `id`, `run_id`, `agent`, `status`, `input_refs`, `output_refs`, `started_at`, `finished_at`, `attempt`, `error_code`, `log_ref`.

Evitare di passare file binari attraverso prompt: usare percorsi e ID asset. Gli output AI devono essere validati contro schemi JSON versionati.

## Stati del job
`queued -> running -> completed | failed | blocked | cancelled`.

Usare `blocked` per requisiti non soddisfatti, per esempio `BLOCKED_MISSING_4K_ASSET` o `BLOCKED_LICENSE_UNKNOWN`.

## Decisioni tecniche
Le tecnologie concrete devono essere confermate dopo l'audit e la verifica delle licenze. Nessun componente deve essere scelto soltanto perché nominato nella specifica.
