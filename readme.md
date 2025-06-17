# Database

Un database è un **sistema organizzato** per la **memorizzazione**, **gestione** e **recupero** efficiente di dati strutturati.

I dati all'interno di un database vengono presentati in **righe** e **colonne** in delle **tabelle** in modo da garantire l'efficienza di elaborazione e query dei dati. La maggior parte dei database utilizza il linguaggio SQL per scrivere, manipolare, definire dati ed eseguirne query.

**SQL** = Structured Query Language
**Quary** = "Domanda" al database per ottenere informazioni specifiche

La maggior parte dei database (di solito) richiede un software completo per fornire un'interfaccia grafica per permettere agli utenti di recurepare e gestire dati nei database, esso agevola la supervisione ed il controllo dei database. (Per farla breve è come un ide che usi di solito).
Questo software è chiamato DBMS.

**DBMS** = Database Management System

Ogni database supporta quattro operazioni **fondamentali** che può utilizzare per manipolare dati seguendo l'acronimo **CRUD**:
(è come se fosse il dna del database)

- **C** - Create -> Inserire nuovi dati
- **R** - Read -> Leggere dati
- **U** - Update -> Modificare dati esistenti
- **D** - Delete -> Cancellare dati

-> Perchè non utilizzo un foglio di dati tipo excel invece di un database?

Principalmente per questioni di accesso, performance, sicurezza e scalabilità.
Excel ha un limite fisico di righe e colonne per un foglio di lavoro il che lo rende lento ed instabile se il nostro database cresce mentre il database si adatta alla quantità di dati gestiti anche con numeri enormi garantendo stabilità e velocità. Di solito i fogli di calcolo sono pensati per un utente singolo o un numero limitato di utenti che non deve eseguire complesse procedure di organizzazioni di dati dove, al contrario, un database è appunto pensato per fare ciò, consentono a più utenti di accedere a dati, eseguire quary in modo rapido, sicuro mediante una logica e un linguaggio.

## Diversi tipi di database

### Database relazionale (SQL)

Sono organizzati da molte tabelle composte da righe e colonne seguendo schemi rigidi per mantenere coerenza.

### Database non relazionale (NoSQL)

Consente di archiviare e manipolare dati non strutturati e semi-strutturati.

I più comuni sono questi ma puoi seguire questo link per magari approfondire meglio (https://www.oracle.com/it/database/what-is-database/).

# CREAZIONE TABELLA

(L'ho fatta in sql ma penso che funzioni ovunque in sistemi sql)

Per creare una tabella bisogna fare:

`
CREATE TABLE nome_tabella (

    );

`

Per inserire dati posso fare:

`
CREATE TABLE nome\*tabella (
nome variabile
nome1 variabile2
);

`
