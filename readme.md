# Database

Un database è un **sistema organizzato** per la **memorizzazione**, **gestione** e **recupero** efficiente di dati strutturati.

I dati all'interno di un database vengono presentati in **righe** e **colonne** in delle **tabelle** in modo da garantire l'efficienza di elaborazione e query dei dati. La maggior parte dei database utilizza il linguaggio SQL per scrivere, manipolare, definire dati ed eseguirne query. (E' comunque utile ricordare che il linguaggio SQl non è generalmente case sensitive quindi se scrivessi SELECT o select o Select esegue tranquillamente la query.)

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

Qui sto dicendo che deve mettere nella tabella tea_shop **(dei valori che si aspetta)** dei valori **(valori che voglio inserire)**

```sql
INSERT INTO tea_shop () VALUES ()
```

(Per le stringhe puoi usare sia ' che " ma ognuno presenta particolarità se associato a caratteri di escape, ti conviene controllare qui per avere una visione d'insieme più precisa: https://dev.mysql.com/doc/refman/8.4/en/string-literals.html)

```sql
INSERT INTO tea_shop (tea_name, tea_type, price, aviable)
VALUES
("Masala Chai", "Spiced", 30.00, true),
("Green Chai", "Herbal", 15.00, true),
("Black Chai", "Classic", 20.00, true),
("Iced Chai", "Cold", 35.00, false),
("Oolong Chai", "Speciality", 40.00, true);
```

# RICERCA DATI USANDO QUARY

## Per visualizzare tutti gli elementi che ho aggiunto nella mia tabella devo scrivere una quary.

##### Seleziona TUTTO da tea_shop

```sql
SELECT * FROM tea_shop;
```

Ecco quello che mi uscirà:

```markdown
| id  | tea_name    | tea_type   | price | available |
| --- | ----------- | ---------- | ----- | --------- |
| 1   | Masala Chai | Spiced     | 30.00 | 1         |
| 2   | Green Chai  | Herbal     | 15.00 | 1         |
| 3   | Black Chai  | Classic    | 20.00 | 1         |
| 4   | Iced Chai   | Cold       | 35.00 | 0         |
| 5   | Oolong Chai | Speciality | 40.00 | 1         |
```

## Se volessi selezionare e visualizzare solamente le colonne con il nome ed il tipo del tè scrivo:

##### Seleziona tea_name e tea_type da tea_shop

```sql
SELECT tea_name, tea_type from tea_shop
```

```markdown
| tea_name    | tea_type   |
| ----------- | ---------- |
| Masala Chai | Spiced     |
| Green Chai  | Herbal     |
| Black Chai  | Classic    |
| Iced Chai   | Cold       |
| Oolong Chai | Speciality |
```

## Se volessi invece mostrare i nomi delle colonne momentaneamente per una visione migliore posso usare AS:

##### Seleziona tea_name come "Tea Name" e tea_type come "Tea Type" da tea_shop

```sql
SELECT tea_name AS "Tea Name", tea_type AS "Tea Type" from tea_shop
```

```markdown
| Tea Name    | Tea Type   |
| ----------- | ---------- |
| Masala Chai | Spiced     |
| Green Chai  | Herbal     |
| Black Chai  | Classic    |
| Iced Chai   | Cold       |
| Oolong Chai | Speciality |
```

## Se volessi ricercare il valore preciso di una stringa:

(esempio "Ciao mondo" e provo a cercare "ciao" lui non mi restituisce nulla, solo se cercassi "ciao MonDo" mi restituirebbe la stringa se presente nella tabella):

##### Seleziona tutto da tea_shop DOVE chai_name = "Black Chai"

```sql
SELECT * FROM tea_shop WHERE chai_name = "Black Chai"
```

```markdown
| id  | tea_name   | tea_type | price | available |
| --- | ---------- | -------- | ----- | --------- |
| 3   | Black Chai | Classic  | 20.00 | 1         |
```

Se provassi a cercare solo "Chai" non mi restituirebbe nulla.

```sql
SELECT * FROM tea_shop WHERE chai_name = "Chai"
```

```markdown
| id   | tea_name | tea_type | price | available |
| ---- | -------- | -------- | ----- | --------- |
| null | null     | null     | null  | null      |
```

Per ricercare una stringa o un testo devo usare l'operatore **LIKE** ed il simbolo della percentuale **%**, esso mi dice "non mi interessa quello che viene prima (se lo metto prima di una parola) o dopo (se lo metto dopo), l'importante è che mi mostri se esiste una stringa che abbia quello che cerco io grazie all'operatore di confronto **LIKE**

(In PostgresSQL ricercare per doppi apici (" ") a volte provoca errore e devi ricercare per apici singoli (' '). Ovviamente tutto è scritto nella sua documentazione e leggere sempre essa scioglie ogni dubbio -> https://www.postgresql.org/docs/current/)

##### "%Chai" -> Trova stringhe che terminano con "Chai"

##### "Chai%" -> Trova stringhe che iniziano con "Chai"

##### "%Chai%" -> Trova stringhe che contengono "Chai"

##### Seleziona tutto da tea_shop dove tea_name **DEV'ESSERE UGUALE A** "%Chai%"

```sql
SELECT * FROM tea_shop WHERE tea_name LIKE "%Chai%";
```

```markdown
| id  | tea_name    | tea_type   | price | available |
| --- | ----------- | ---------- | ----- | --------- |
| 1   | Masala Chai | Spiced     | 30.00 | 1         |
| 2   | Green Chai  | Herbal     | 15.00 | 1         |
| 3   | Black Chai  | Classic    | 20.00 | 1         |
| 4   | Iced Chai   | Cold       | 35.00 | 0         |
| 5   | Oolong Chai | Speciality | 40.00 | 1         |
```

## Se volessi ricercare per prezzo potrei scrivere una quary del genere:

##### Seleziona tutto da tea_shop dove price DEVE ESSERE PIU' PICCOLO DI 30

```sql
SELECT * FROM tea_shop WHERE price < 30;
```

```markdown
| id  | tea_name   | tea_type | price | available |
| --- | ---------- | -------- | ----- | --------- |
| 2   | Green Chai | Herbal   | 15.00 | 1         |
| 3   | Black Chai | Classic  | 20.00 | 1         |
```

## Se volessi ricercare per ordine di prezzo potrei scrivere:

##### Seleziona tutto da tea_shop ORDINATO PER price

```sql
SELECT * FROM tea_shop ORDER BY price;
```

```markdown
| id  | tea_name    | tea_type   | price | available |
| --- | ----------- | ---------- | ----- | --------- |
| 2   | Green Chai  | Herbal     | 15.00 | 1         |
| 3   | Black Chai  | Classic    | 20.00 | 1         |
| 1   | Masala Chai | Spiced     | 30.00 | 1         |
| 4   | Iced Chai   | Cold       | 35.00 | 0         |
| 5   | Oolong Chai | Speciality | 40.00 | 1         |
```

Per scriverlo in maniera inversa, quindi dal prezzo più grande al più piccolo invece posso scrivere:

##### Seleziona tutto da tea_shop ORDINATO PER price DESC

```sql
SELECT * FROM tea_shop ORDER BY price DESC;
```

```markdown
| id  | tea_name    | tea_type   | price | available |
| --- | ----------- | ---------- | ----- | --------- |
| 5   | Oolong Chai | Speciality | 40.00 | 1         |
| 4   | Iced Chai   | Cold       | 35.00 | 0         |
| 1   | Masala Chai | Spiced     | 30.00 | 1         |
| 3   | Black Chai  | Classic    | 20.00 | 1         |
| 2   | Green Chai  | Herbal     | 15.00 | 1         |
```

# AGGIORNAMENTO DATI

## Se volessi aggiornare dei dati nella mia tabella devo seguire:

```sql
UPDATE nome_database
SET dati aggiornati
WHERE dati che voglio che vengano modificati
```

Prima gli dico su quale tabella deve operare, poi su set aggiorno i dati che voglio che vengano aggiornati ed infine in where gli specifico che dato deve aggiornare.

Se non mettessi la condizione di WHERE mi andrà a modificare tutta la tabella con i valori scritti in set, che detto fra noi, è l'ultima cosa che vorremmo fare nel nostro database, quindi devo prestare attenzione quando scrivo la quary.

```sql
UPDATE tea_shop
SET price = 38.00, available = TRUE
WHERE tea_name = "Iced Chai";
```

Controllo con una quary per controllare l'effettivo aggiornamento dei dati:

```sql
SELECT * FROM tea_shop;
```

```markdown
| id  | tea_name    | tea_type   | price | available |
| --- | ----------- | ---------- | ----- | --------- |
| 1   | Masala Chai | Spiced     | 30.00 | 1         |
| 2   | Green Chai  | Herbal     | 15.00 | 1         |
| 3   | Black Chai  | Classic    | 20.00 | 1         |
| 4   | Iced Chai   | Cold       | 38.00 | 1         |
| 5   | Oolong Chai | Speciality | 40.00 | 1         |
```

# ELIMINAZIONE DATI

## Se volessimo eliminare dei dati da una tabella seguo:

```sql
DELETE FROM nome_tabella
WHERE dato che voglio eliminare
```

Come prima, gli dico su che tabella deve operare e in WHERE gli elenco che dato deve andare a considerare.

```sql
DELETE FROM tea_shop
WHERE tea_name = "Black Chai";
```

```markdown
| id  | tea_name    | tea_type   | price | available |
| --- | ----------- | ---------- | ----- | --------- |
| 1   | Masala Chai | Spiced     | 30.00 | 1         |
| 2   | Green Chai  | Herbal     | 15.00 | 1         |
| 4   | Iced Chai   | Cold       | 38.00 | 1         |
| 5   | Oolong Chai | Speciality | 40.00 | 1         |
```
