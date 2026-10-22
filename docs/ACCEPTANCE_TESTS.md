# Criteri di accettazione e test

## Test automatici iniziali
- Configurazione caricata con default sicuri; segreti ignorati dal controllo versione.
- Stato job persistente e riprendibile dopo riavvio.
- Errori e retry con numero massimo configurato.
- Deduplicazione fonti e asset tramite URL normalizzato/hash.
- Parsing RSS con fixture locali.
- ffprobe invocato senza interpolazione shell vulnerabile; gestione file assente/corrotto.
- Asset con licenza sconosciuta non selezionabile per la pubblicazione finale.
- Output verificato per risoluzione e durata reali.
- SRT/VTT validi e timestamp monotoni.
- Render 4K non etichettato nativo quando le sorgenti sono inferiori; upscale dichiarato.
- Blocco specifico se mancano asset 4K richiesti o licenza.

## Test end-to-end pilota
1. Acquisire una notizia da una fonte reale supportata.
2. Salvare URL/data e generare copione con fonti di supporto.
3. Cercare e validare almeno un asset riutilizzabile pertinente.
4. Generare voce e sottotitoli con motori locali disponibili.
5. Eseguire il rendering.
6. Verificare il file con ffprobe e controlli audio/video.
7. Salvare report fonti, asset, licenze, qualità sorgenti e test.

Se il test non può completarsi per mancanza di media o modelli, il report deve indicare il requisito mancante e non marcare la produzione come riuscita.
