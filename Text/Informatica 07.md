# ES07 Informazioni Geografiche

    Si vuole progettare una base di dati contenente informazioni di carattere geografico.

    Le informazioni da rappresentare riguardano le nazioni, i fiumi, i laghi. Di ciascuna nazione  interessa il nome, che la identifica, e la superficie. Di ciascun fiume interessa il nome, che lo identifica, le nazioni attraversate e la lunghezza del percorso del fiume in ogni nazione, nonché la lunghezza totale del fiume. Un fiume può essere affluente di un altro fiume; la base di dati deve rappresentare anche questo fatto.

    Di ciascun lago, anch’esso identificato dal nome, interessa la superficie, la profondità massima e le nazioni bagnate dal lago. Un lago può avere degli immissari e degli emissari (fiumi); la base di dati deve rappresentare anche questo fatto.

## 1. Rappresentare il diagrammi ER facendo uso, dove opportuno, di gerarchie di entità. Corredare l'ER con regole di lettura.

## 2. Trasformare poi il diagramma ER in schema logico relazionale indicando chiaramente le chiavi, i riferimenti ed i vincoli che ti sembrano degni di nota

## 3. Esprimere in SQL le seguenti richieste:

### a. Creare almeno due tabelle fra esse correlate, esprimendo tutti i vincoli degni di nota

### b. Si desidera conoscere il nome del/dei fiume/i più lungo/hi fra quelli che attraversano il territorio tedesco.

### c. Numero dei laghi presenti sul territorio italiano.

### d. Superficie media delle nazioni presenti nella base di dati.

### e. Elenco alfabetico delle nazioni attraversate dal fiume Danubio, con l'indicazione della relativa lunghezza del suo percorso in ciascuna nazione.

### f. Elenco degli emissari del Lago di Garda.

-- ES07 Informazioni Geografiche

-- 3

--- a

CREATE TABLE

    Nazione (

        Nome VARCHAR(50) PRIMARY KEY,

        Superficie FLOAT NOT NULL

    );

  

CREATE TABLE

    Fiume (

        Nome VARCHAR(50) PRIMARY KEY,

        Lunghezza FLOAT NOT NULL,

        FKNazione VARCHAR(50) NOT NULL,

        FOREIGN KEY (FKNazione) REFERENCES Nazione (Nome)

    );

  

CREATE TABLE

    Lago (

        Nome VARCHAR(50) PRIMARY KEY,

        Superficie FLOAT NOT NULL,

        Profondita FLOAT NOT NULL,

        FKNazione VARCHAR(50) NOT NULL,

        FOREIGN KEY (FKNazione) REFERENCES Nazione (Nome)

    );

  

--- b

SELECT

    N.Nome AS Nazione,

    F.Nome AS Fiume

    F.Lunghezza

FROM

    Nazione N

    JOIN Fiume F ON N.Nome = F.FKNazione

WHERE

    F.Lunghezza = (

        SELECT

            MAX(Lunghezza)

        FROM

            Fiume

    )

GROUP BY

    N.Nome,

    F.Nome,

    F.Lunghezza

ORDER BY

    F.Lunghezza DESC;

  

--- c

SELECT

    N.Nome AS Nazione,

    L.Nome AS Lago

FROM

    Nazione N

    JOIN Lago L ON N.Nome = L.FKNazione

WHERE

    N.Nome = 'Italia'

ORDER BY

    L.Superficie DESC;

  

--- d

SELECT

    N.Nome AS Nazione,

    AVG(N.Superficie) AS SuperficieMedia

FROM Nazione N

WHERE

ORDER BY

    SuperficieMedia DESC;