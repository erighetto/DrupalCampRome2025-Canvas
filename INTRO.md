# Drupal Canvas: Guida per Developer

## Cos'è Drupal Canvas

Drupal Canvas (precedentemente noto come Experience Builder) è un page builder di nuova generazione per Drupal che mira a rivoluzionare l'esperienza di costruzione dei siti web. Non è semplicemente un page builder, ma una piattaforma completa per costruire esperienze digitali che include:

- Costruzione di componenti
- Design visuale del sito
- Gestione dell'intero workflow di sviluppo

Il progetto è nato dalla necessità di colmare il gap tra le soluzioni esistenti (Layout Builder, Paragraphs) e le aspettative moderne degli utenti, offrendo un'esperienza che compete con soluzioni come Squarespace/Webflow ma mantenendo la potenza e l'estensibilità di Drupal.

## Architettura e Tecnologie

### Stack Tecnologico
- **Frontend**: Costruito con **React** invece del tradizionale PHP
- **Componenti**: Basato su **Single Directory Components (SDC)**
- **Editor**: Include un editor di codice integrato nel browser

Questa nuova architettura apre opportunità per integrare funzionalità avanzate, inclusa l'AI.

## Componenti: Il Cuore di Canvas

### Tipi di Componenti

**1. Code Components**
- Creabili direttamente nell'interfaccia di Canvas
- Utilizzano l'editor integrato nel browser
- Non richiedono IDE o ambiente di sviluppo locale

**2. SDC Components**
- Qualsiasi componente SDC diventa automaticamente disponibile in Canvas
- A partire da Drupal 11.3, sarà possibile indicare se un componente SDC deve apparire in Canvas
- Esiste un'interfaccia UI per disabilitare componenti specifici

**3. Blocks**
- I block Drupal tradizionali possono essere utilizzati in Canvas
- Utili per percorsi di migrazione da Layout Builder

### Gestione dei Componenti

Canvas NON include componenti di default. Questi sono stati spostati in un submodule opzionale. L'idea è che:
- Per testare: si può abilitare il submodule con componenti di esempio
- Per siti reali: i componenti arrivano da design system specifici (es. SDDS, Mercury)
- Per Drupal CMS: i componenti arriveranno dai "site templates"

## Modalità di Utilizzo

Canvas supporta due approcci principali:

### 1. Pagine Flessibili (stile Squarespace)
- Massima libertà di layout
- Ogni pagina può avere una struttura unica
- I componenti controllano centralmente aspetto e comportamento
- Gestione CSS centralizzata

### 2. Template Strutturati

**Page Templates**
- Header e footer consistenti
- Simile a Block Layout ma con componenti SDC
- Utilizzano gli stessi componenti delle pagine flessibili

**Content Templates**
- Template per Content Type o Taxonomy
- Applicati a cascata su tutti i nodi di un tipo
- Aggiornamenti centralizzati
- **Non supportano override per singola pagina** (questo è intenzionale, basato su ricerca UX)

### 3. Template Ibridi (Roadmap Futura)
Caso d'uso: prodotti e-commerce
- Parte superiore strutturata (SKU, prezzo, immagini)
- Parte inferiore flessibile per storytelling marketing
- Implementato come "slot" dove inserire componenti

## Funzionalità SDC Avanzate

Canvas estende la specifica SDC con nuove capability:

### Slot Restrictions
- I componenti possono definire quali altri componenti accettare nei loro slot
- Configurazione a livello di componente, non globale

### Variants Support
- Supporto per varianti di componenti

### Internal Components
- Flag per indicare componenti interni (non visibili nei builder)
- Specifica condivisa con UI Suite per interoperabilità

## Data Model e Limitazioni Conosciute

### Punti di Forza
- **Versioning delle props**: possibilità di aggiornare schema dei componenti
- **Supporto multilingua progettato**: il data model supporta sia traduzioni simmetriche che asimmetriche
- **Flessibilità futura**: architettura pensata per evitare i problemi di Layout Builder

### Limitazioni Correnti (v1.0)

**Traduzioni**
- Non supportate nella v1.0
- Previste per Q1 2026
- Il data model è pronto per supportare sia traduzioni simmetriche che asimmetriche
- Possibilità di scegliere il tipo di traduzione per singolo contenuto

**Modifiche Post-Creazione**
- Attualmente limitate per garantire integrità dei dati
- Roadmap per permettere più modifiche (es. modifica props dei componenti)
- Sistema di versioning per gestire upgrade degli schema

## Integrazione AI

### Stato Attuale
Canvas include strumenti AI per:
- **Generazione componenti da immagini**: prende un'immagine di design e genera il codice del componente
- **Composizione pagine**: utilizza componenti esistenti per creare layout

### Livello di Maturità
- **Per developer frontend**: ~70-80% del lavoro (gestisce boilerplate)
- **Per non-developer**: utilità limitata (la parte difficile rimane il match con il design)
- **Composizione pagine**: risultati migliori, spazio del problema più limitato
- **Obiettivo**: agenti autonomi, ma ancora non raggiunto

**Importante**: L'AI accelera ma non sostituisce il developer. Il controllo umano rimane essenziale per qualità e precisione.

## Migrazione da Soluzioni Esistenti

### Strategia Consigliata: Adozione Graduale

Canvas può coesistere con altre soluzioni:
- Abilitarlo solo per specifici content type
- Utilizzare Canvas Pages per nuovi contenuti
- Mantenere Paragraphs/Layout Builder per contenuti esistenti

### Migrazione da Layout Builder
**Conceptualmente possibile**:
- Uno slot Canvas = un campo Paragraphs
- Potrebbero essere visualizzati paragraphs in Canvas (da provare)
- Mapping paragraph component → Canvas component

**Priorità del team**:
1. Completare feature set per nuovi siti
2. Raccogliere feedback
3. Poi focus su migrazioni

## Timeline e Roadmap

### Release Schedule
- **Luglio 2024**: Completati tutti i beta blocker (poi rinviato per questioni legali sul nome)
- **Fine Ottobre 2024**: Target per release stabile 1.0
- **Q1 2026**: Supporto multilingua previsto

### Utilizzo in Produzione
- **Acquia Source**: già in produzione con Canvas da Luglio 2024
- **Siti client**: stabile abbastanza per progetti con timeline flessibile (fine 2024)
- **Feature gap**: v1.0 non avrà tutte le capability di Layout Builder/Paragraphs

## Team e Risorse

- **Team size**: ~20+ persone full-time (dipendenti + contractor)
- **Include**: design, sviluppo, product management
- **Test coverage**: secondo utilizzo più alto su GitLab CI dopo Core
- **Collaborazioni**: UI Suite, Drupal CMS, govCMS

## Design System di Riferimento

### Starshot Demo Design System (SDDS)
- Creato da Kristen Pol (Salsa Digital)
- Basato su Civic Theme
- Utilizzato per demo e Dries Notes
- Include Figma e Storybook UI kits
- WCAG 2.2 compliant

### Mercury
- Design system per Drupal CMS
- Stack tecnologico differente da SDDS
- In sviluppo

### Civic Theme
- Base per SDDS
- Sistema di design component-based atomico
- Ottimo punto di partenza per chi vuole usare Canvas in produzione

## Best Practices per Developer

### Persona Target
Canvas è pensato con il **frontend developer come persona chiave**:
- Site builder usa componenti creati da frontend dev
- Oppure site builder è anche frontend dev
- Molta logica spostata nei componenti invece che nel sistema

### Estensibilità
Il punto di forza di Canvas vs soluzioni proprietarie:
- Integrazioni custom
- Componenti custom
- Estensioni per developer
- Sistema aperto per collaborazione dev/site builder/content creator

### Naming Conventions
- **Elements**: componenti built-in (roadmap futura)
- **Components**: quelli che costruisci tu
- Distinzione chiara tra ciò che è interno e ciò che è del progetto

## Connessione con l'Ecosistema

### Drupal CMS
- Canvas è parte integrante di Drupal CMS
- I componenti arriveranno dai "site templates" di Drupal CMS 2.0
- Vision: singola piattaforma condivisa

### Acquia Source
- SaaS basato su Drupal CMS
- Include Canvas out-of-the-box
- **Export path**: Acquia Source → Drupal CMS
- Pricing: tra Squarespace e Acquia Enterprise
- Ideale per landing page e siti veloci

## Risorse e Documentazione

### Repository
- **In transizione**: da `drupal.org/project/experience_builder` a `drupal.org/project/canvas`
- Migrazione prevista per fine settembre 2024

### Community
- Canale Drupal Slack
- Issues su drupal.org
- Dries Notes mensili con demo

### Contact
- Lauri Timmanee (laaa su Drupal.org)
- Product Manager per Canvas e Acquia Source
- Core committer dal 2017

## Conclusioni

Drupal Canvas rappresenta un cambio di paradigma per Drupal:
- **Non solo page building**: piattaforma completa per experience building
- **Developer-friendly**: estensibilità mantenendo facilità d'uso
- **Future-proof**: architettura moderna con React, AI-ready
- **Community-driven**: obiettivo di unificare l'ecosistema frammentato

Il successo sarà misurato dalla crescita della community di site builder, rendendo Drupal accessibile a un pubblico più ampio senza sacrificare la potenza che lo contraddistingue.
