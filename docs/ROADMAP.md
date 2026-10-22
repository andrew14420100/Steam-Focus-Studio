# Roadmap

## Fase 0 — Audit ambiente e repository
- Esaminare codice esistente, Python, Node, Git, FFmpeg/ffprobe, GPU, Ollama e modelli locali.
- Rilevare senza divulgare segreti eventuali servizi TTS/ASR locali già attivi.
- Verificare licenze e dipendenze candidate.
- Produrre documentazione e piano riproducibile.

## Fase 1 — Fondamenta
- Configurazione, SQLite, modelli dati, macchina a stati, log, checkpoint e CLI.
- Test unitari e fixture sintetiche senza media protetti.

## Fase 2 — Newsroom
- Fonti RSS e pagine ufficiali configurabili, titolo/data/url e deduplicazione.
- Schede notizia e copione con riferimenti e stato di verifica.

## Fase 3 — Ricerca media
- Ricerca di fonti media ufficiali, catalogo asset, metadati e provenienza.
- Download solo dove consentito; ffprobe, hash, deduplicazione e stato licenza.
- Marcatura nativo 4K/upscale/risoluzione inferiore.

## Fase 4 — Voce, audio e sottotitoli
- TTS locale con adapter sostituibile.
- Audio per segmenti, timing, SRT/VTT e mixaggio.

## Fase 5 — Storyboard e rendering
- Mappa frase/scena/asset/timecode.
- Template STEAM FOCUS, grafiche, transizioni e rendering 4K.
- Distinzione tra sorgente nativa e upscale, preset di encoding.

## Fase 6 — QA e recupero
- Verifica tecnica, audio, sottotitoli, crediti, fonti e diritti.
- Retry mirati e report cause di blocco.

## Fase 7 — UI
- Dashboard, newsroom, libreria, storyboard, anteprima e log agenti.

## Fase 8 — Packaging e YouTube opzionale
- Istruzioni installazione, pacchetto Windows, OAuth facoltativo e upload privato come default.

## Definition of Done
- Codice reale implementato.
- Test eseguiti e risultati documentati.
- Nessun segreto o asset non autorizzato nel repository.
- README e documentazione aggiornati.
- Commit Git descrittivo.
