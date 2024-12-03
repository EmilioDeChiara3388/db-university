Modellare la struttura di un database per memorizzare tutti i dati riguardanti una università:
sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);
ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)
ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);
ogni Corso può essere tenuto da diversi Insegnanti;
ogni Corso prevede più appelli d'Esame;
ogni Studente è iscritto ad un solo Corso di Laurea;
ogni Studente può iscriversi a più appelli di Esame;
per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente. Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni. Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

## Tables
- dipartimenti
- corsi_di_laurea
- corsi
- insegnanti
- esami
- studenti

## Dipartimenti: table structure
- id | BIGINT - AI - PK - NOTNULL
- nome | VARCHAR (50) - NOTNULL
- indirizzo | VARCHAR () - NULL


## corsi_di_laurea: table structure
- id | BIGINT - AI - PK - NOTNULL
- id_dipartimento
- nome | VARCHAR (50) - NOTNULL
- durata | VARCHAR(20)


## corsi: table structure
- id | BIGINT - AI - PK - NOTNULL
- id_corsi_di_laurea
- id_insegnanti
- nome | VARCHAR (50) - NOTNULL
- crediti | TINYINT - NOTNULL
- appelli_esami | DATE - NULL - DEFAULT("da definire")

## insegnanti: table structure
- id | BIGINT - AI - PK - NOTNULL
- id_corso
- id_esami
- nome | VARCHAR (50) - NOTNULL
- cognome | VARCHAR (50) - NOTNULL

## esami: table structure
- id | BIGINT - AI - PK - NOTNULL
- id_insegnante
- id_corso
- appelli_esame | DATE - NULL - DEFAULT("da definire")

## studenti: table structure
- id | BIGINT - AI - PK - NOTNULL
- id_corso_di_laurea
- matricola | VARCHAR(12)
- nome | VARCHAR (50) - NOTNULL
- cognome | VARCHAR (50) - NOTNULL
- data_di_nascita | DATE - NOTNULL



