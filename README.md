# Ricordati di comprare… — Spesa Smart

Progressive Web App per lista della spesa, dispensa, offerte presenti nel database e storico acquisti.

## Pubblicazione su GitHub Pages (da iPhone o computer)

1. Crea un repository GitHub nuovo, ad esempio `spesa-smart`.
2. Imposta il repository come **Public** (necessario per GitHub Pages gratuito).
3. Carica nella radice del repository TUTTI questi file e cartelle:
   - `index.html`
   - `manifest.webmanifest`
   - `sw.js`
   - `icon.svg`
4. Vai in **Settings → Pages**.
5. In **Build and deployment**, scegli **Deploy from a branch**.
6. Seleziona `main` e `/ (root)`, poi **Save**.
7. Attendi la pubblicazione. L'indirizzo sarà `https://TUO-UTENTE.github.io/spesa-smart/`.

## Supabase già configurato

L'app punta al progetto Supabase `RicordatiDiComprare` in regione Francoforte. Nel codice è inserita esclusivamente la chiave publishable (client-side), mai una service-role key.

## Account e sincronizzazione familiare

- Crea un account dalla schermata iniziale e conferma l'email se Supabase lo richiede.
- Per usare la stessa lista sui telefoni dei familiari, accedi con lo stesso account su ogni dispositivo.
- Il database attuale applica le policy RLS per proprietario (`user_id`): questa prima versione non implementa ancora inviti/ruoli familiari separati.
- Non condividere l'account fuori dal nucleo familiare. Per accessi separati servirà una successiva modifica del database con membership di famiglia e relative policy.

## Funzionalità incluse

- Login e registrazione email/password Supabase.
- Creazione automatica della lista attiva.
- Inserimento, spunta e cancellazione prodotti.
- Sincronizzazione in tempo reale degli elementi della lista.
- Dispensa personale e trasferimento di un prodotto nella lista.
- Visualizzazione offerte esistenti non scadute; nessuna offerta viene inventata.
- Storico prodotti spuntati e registrazione manuale dei prezzi.

## Limiti noti da risolvere in una fase successiva

- Le fonti offerte sono presenti nel database, ma non esistono ancora funzioni automatiche di raccolta/aggiornamento.
- La categoria selezionata nell'inserimento lista è attualmente solo un filtro/interfaccia predisposta; lo schema `shopping_items` non contiene un campo categoria.
- L'app richiede connessione internet per le operazioni e l'autenticazione. La cache PWA conserva solo la struttura dell'interfaccia, non rende offline i dati.
- Per condivisione familiare con account distinti va implementata una tabella household_members e aggiornate con attenzione le policy RLS.

## Sicurezza

Non inserire mai nel frontend chiavi `service_role`, password o segreti. La chiave `sb_publishable_...` è progettata per essere usata nel client insieme a RLS.
