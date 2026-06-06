* **SQL** in modalità
   * _embedded_
      * SQL scritto all'interno di un **programma host** (C, Java, Python…), eseguito tramite il linguaggio ospite
   * _standalone_
      * SQL eseguito direttamente, senza un linguaggio ospite che lo contenga
   * _batch_
      * insieme di comandi SQL preparati in anticipo ed eseguiti in blocco, senza intervento dell'utente
   * _interattivo_
      * l'utente digita un comando alla volta e riceve risposta immediata (es. psql, MySQL shell)

* **DDL** _(Data Definition Language)_
   * definisce la struttura del database (schema)
   * **CREATE** — crea tabelle, indici, viste, schemi
   * **ALTER** — modifica la struttura di oggetti esistenti
   * **DROP** — elimina oggetti dal database
   * **TRUNCATE** — svuota una tabella (più veloce di DELETE)

* **DML** _(Data Manipulation Language)_
   * manipola i dati contenuti nelle tabelle
   * **INSERT** — inserisce nuove righe in una tabella
   * **UPDATE** — modifica valori di righe esistenti
   * **DELETE** — rimuove righe da una tabella

* **DCL** _(Data Control Language)_
   * modifica i diritti di accesso alle basi di dati
   * **GRANT**
      * _concede_ privilegi a un utente o ruolo (es. GRANT SELECT ON tabella TO utente)
   * **REVOKE**
      * _revoca_ privilegi precedentemente concessi (es. REVOKE SELECT ON tabella FROM utente)

* **QL** (Query Language)
   * interroga il database per recuperare dati
   * **SELECT** — estrae righe da una o più tabelle
   * **FROM** — indica la/e tabella/e di origine
   * **WHERE** — filtra le righe in base a condizioni
   * **JOIN** — combina dati da tabelle diverse
   * **GROUP BY / HAVING** — aggrega e filtra gruppi
   * **ORDER BY** — ordina il risultato
   * **LIMIT / OFFSET** — limita le righe restituite
   * **COUNT** — conta il numero di righe restituite
   * **MIN** — restituisce il valore minimo di una colonna
   * **MAX** — restituisce il valore massimo di una colonna
   * **SUM** — restituisce la somma dei valori di una colonna
   * **AVG** — restituisce la media dei valori di una colonna

* **La Proiezone**
	* _Altera il grado_
* **La Restrizione**
	* _Altera la cardinalità_
* **JOIN**
	* _Cross Join_ o _Join_
	* _Inner Join_ o 
	* _Outer Join_
		* _Left Join_
		* _Right Join_
	* _Self Join_
* 