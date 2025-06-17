# Database

Un database è un **sistema organizzato** per la **memorizzazione**, **gestione** e **recupero** efficiente di dati strutturati.

I dati all'interno di un database vengono presentati in **righe** e **colonne** in delle **tabelle** in modo da garantire l'efficienza di elaborazione e query dei dati. La maggior parte dei database utilizza il linguaggio SQL per scrivere, manipolare, definire dati ed eseguirne query.

- **SQL** = Structured Query Language
- **Quary** = "Domanda" al database per ottenere informazioni specifiche

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

# CREAZIONE DATABASE E TABELLA IN MYSQL

## - DOCUMENTAZIONE -> (https://dev.mysql.com/doc)

Per creare un database dovrò semplicemente scrivere una query:

```sql
CREATE DATABASE nome_database;
```

Per creare una tabella bisogna fare:

```sql
CREATE TABLE (

);
```

Per inserire dati posso fare:

```sql
CREATE TABLE nome_tabella (
    id PRIMARY KEY,
    nome variabile,
    nome1 variabile2
);
```

La maggior parte delle tabelle presenta una **primary key**, essa permette di ricercare sempre un elemento quando voglio e soprattutto di dargli un indice.

La nostra pimary key dovrà avere questi attributi per indicizzare la nostra tabella:

- **Nome** - Un nome identificativo, nella maggior parte dei casi conciso in modo tale da sapere cosa sto indicizzando senza troppi giri di parole

- **Int** - Valore intero

- **NOT NULL** - Il valore della nostra colonna indicizzata non può essere nullo, se fosse nullo non avrebbe senso e ci intralcerebbe nella indicizzazione

- **AUTO_INCREMENT** - Il database assegna automaticamente un valore crescente

- **PRIMARY KEY** - Questo valore permette di identificare le righe sottostanti indicizzandole univocamente

```sql
CREATE TABLE nome_tabella (
    id int not null auto_increment primary key,
    nome proprietà,
    nome1 proprietà2
);
```

Le proprietà di ciascun elemento ovviamente cambiano in base all'utilizzo, le più comuni possono essere:

```sql
CREATE TABLE nome_tabella (
    id          int not null auto_increment primary key,
    nome        varChar(20);
    cognome     varChar(25);
    età         int;
    peso        decimal(5, 2);
    haBambini   tinyint
);
```

Ogni proprietà ha la sua documentazione, utilizzo e tutto il resto, quindi leggila e tieniti sempre aggiornato. Per esempio in realtà il boolean in MySql, esso viene semplicemente convertito in tinyint che è un altro tipo che include sempre numeri e via dicendo.

# INSERIMENTO DI DATI IN TABELLA

Ho creato una tabella tea_shop dove dobbiamo aggiungere degli elementi tea da vendere, ecco la tabella:

```sql
CREATE TABLE tea_shop (
    id          int not null auto_increment primary key,
    tea_name    varChar(20),
    tea_type    varChar(20),
    price       decimal(5,2),
    aviable     boolean
);
```

Dovrò inserire una query per aggiungere dei dati nella mia tabella. Ecco la query:
(se magari la query non funziona è perchè non ho selezionato il database da cui prendere la tabella, quindi posso selezionarlo con la quary "USE DATABASE nome_database")

Qui sto dicendo che deve mettere nella tabella tea_shop (dei valori che si aspetta) dei valori (valori che voglio inserire)

```sql
INSERT INTO tea_shop () VALUES ()
```

```sql
INSERT INTO tea_shop (tea_name, tea_type, price, aviable) VALUES ()
```
