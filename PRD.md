# PRD — Sito Matrimonio Valeria & Jacopo

## 1. Obiettivo
Sito a pagina singola, semplice, per:
1. Presentare l'invito e le informazioni dell'evento.
2. Mostrare il menù del ricevimento.
3. Raccogliere conferma/rifiuto presenza (RSVP) con dettagli utili al conteggio invitati per il catering.

Uso interno: strumento di misurazione presenze per gli sposi (non serve gestione avanzata, no login admin).

## 2. Informazioni evento
- Sposi: Valeria & Jacopo (Pipitone - Sant)
- Data: lunedì 24 agosto 2026
- Cerimonia: ore 17:00, Santa Venera
- Ricevimento: Villa Favorita
- Annuncio: fatto a nome del figlio (tono usato nell'invito, vedi immagine)
- IBAN lista nozze (da invito): IT56H0623025900000015258689 — Crédit Agricole, int. Pipitone Valeria Maria Sant Jacopo

## 3. Contenuti pagina

### 3.1 Hero
- Immagine invito fornita (`Partecipazione (115 x 175 mm).png`) come sfondo/hero, oppure ricomposizione degli stessi elementi (chiesa acquerello, frase annuncio, nomi in corsivo, data) se serve adattare il formato a schermo full-width.
- Data, luogo cerimonia e ricevimento in evidenza.
- Countdown al 24 agosto 2026 (nice-to-have, non bloccante).

### 3.2 Sezione "Il Menù"
Fonte: `nozze sant.pdf` (Villa Favorita). Contenuto pubblico da mostrare (senza prezzi — i prezzi p.p. restano informazione privata catering/sposi, non vanno pubblicati):

**Cocktail di benvenuto in Corte**
Mandorle, Canapè, Grana, Crostineria con mousse assortite, Tartine, Patatine, Verdure in pastella, Prosecco, Cocktails

**Angoli gastronomici in Giardino**
- *Fritti*: Cappuccetto pastellato, Polpette con seppie gamberi e sarde
- *Crudité*: Ghiacciate di gambero rosso e scampi, Tartare di tonno agli agrumi e menta, Tartare di ricciola al pepe, Tartare di gamberi con bufalina, Carpaccio di pesce spada al balsamico e mandorle, Carpaccio di salmone al pepe rosa, Carpaccio di spigola ai frutti di bosco
- *Angolo delle Tradizioni*: Caponata alle mandorle, Millefoglie di parmigiana in fonduta di Ragusano e pistacchi, Tortino di alici zafferano e finocchietto, Peperonata con mandorle e menta, Sarde allinguate / a beccafico, Arancini al Marsala e rosmarino, Arabetti con panelle, Polpo in bellavista
- Selezione di formaggi tipici con miele e marmellate, Prosciutto crudo in bellavista, Coppe di gamberi agli agrumi e verdurine

**Primi e Secondi**
Linguine al Passito, ricciola, code di gambero rosso e mandorle · Ruota di pesce spada in caponata di agrumi · Spiedino di gamberi · Patate duchessa · Cubotto di melanzana al rosmarino · Coppa di frutta fresca (pesche, melone, cantalupo, anguria)

**In Corte — Dolci**
Torta Mariage · Millefoglie ai frutti di bosco · Parfait di mandorle · Bavarese al limone · Savarin con panna e pesche · Profitterol al cioccolato · Torte gelato al caffè e nocciola · Angolo Cassata Siciliana e cannoli (live) · Torta di ricotta con gelatina e canditi all'arancia · Semifreddo

**Da bere**: Vino, Spumante

**Menù bambini**: Anelletti, Cotoletta e patatine

Nota: Menù Staff (€ 80,00 p.p.) non va mostrato sul sito, è solo per fornitori/catering.

### 3.3 Sezione RSVP (form)
Campi form:
- Nome e cognome (chi risponde)
- Presenza: Sì / No
- Numero totale persone del gruppo (se sì)
- Nome di ogni accompagnatore/figlio (campi dinamici "aggiungi persona")
- Bambino? (flag per capire se serve menù baby, dato 10 baby previsti nel conteggio catering)
- Allergie/intolleranze (campo testo libero, opzionale)
- Messaggio agli sposi (opzionale)

Deadline risposta: **10 agosto 2026** — visibile chiaramente vicino al form ("Rispondi entro il 10 agosto 2026").

Conferma a schermo dopo invio (messaggio di ringraziamento), niente riepilogo dati sensibili.

## 4. Raccolta e visualizzazione dati (lato sposi)
- Implementazione: **Google Form** embeddato/collegato nella sezione RSVP del sito statico.
- Risposte confluiscono automaticamente in un **Google Sheet** collegato al Form (conteggio/filtraggio facile da telefono o PC).
- Attivare su Google Form l'opzione "**Ricevi notifiche email per ogni nuova risposta**" così da avere sia il foglio aggregato sia l'avviso in tempo reale.

## 5. Stack tecnico
- Sito **statico** (HTML/CSS/JS, nessun framework necessario data la semplicità richiesta).
- Nessun backend/database da mantenere: il "backend" RSVP è il Google Form/Sheet nativo.
- Hosting: da definire in base al dominio già posseduto dall'utente (dominio non ancora comunicato — placeholder `[dominio]` da sostituire). Compatibile con qualunque hosting statico (Netlify, Vercel, GitHub Pages, hosting tradizionale con solo file HTML).
- Accesso: pagina **pubblica**, nessuna password. Da aggiungere meta tag `noindex` per evitare indicizzazione sui motori di ricerca; link condiviso privatamente via WhatsApp/email agli invitati.

## 6. Design/UI
- Palette e stile coerenti con l'invito fornito: tonalità rosa/oro, illustrazione acquerello della chiesa, font corsivo elegante per i nomi "Valeria & Jacopo", font serif per i testi.
- Layout mobile-first (la maggior parte degli invitati aprirà da smartphone).
- Struttura a singola pagina con scroll: Hero → Dettagli evento → Menù → RSVP → (eventuale) info bonifico/lista nozze, riprendendo il contenuto già presente nell'invito.

## 7. Fuori scope (per ora)
- Login/dashboard amministrativa custom (si usa Google Sheet come "dashboard").
- Scelta multipla di portate/menù alternativo (il menù è fisso, unica variante è il menù bambini).
- Password/protezione accesso sito.
- Multi-lingua.

## 8. Da definire in seguito
- Dominio definitivo da collegare all'hosting.
- Eventuali foto aggiuntive oltre all'immagine invito.
