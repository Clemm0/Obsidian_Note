![[A038_SUP24.pdf]]
## Prima Parte – Gestione eventi con grandi folle

---
## 1. Architettura della rete della sede operativa

La sede operativa è distribuita su due piani collegati da uno switch centrale (o router interno):
- **1° piano (biglietteria):** workstation degli operatori, server per la gestione delle vendite/prevendite, stampanti per biglietti fisici. Collegati in LAN via switch.
- **2° piano (sala controllo):** workstation degli addetti alla sorveglianza, monitor wall per visualizzare i feed delle telecamere, NVR (Network Video Recorder) per la registrazione.
- **VLAN separate** per isolare il traffico: una VLAN per la videosorveglianza (alto traffico), una per la biglietteria, una per la gestione dei dispositivi remoti.
- **Firewall** a protezione del perimetro, con DMZ per i servizi esposti all'esterno (es. totem, personale in loco).
- **Server centrale** con database biglietti, gestione eventi, e dashboard di controllo dei dispositivi remoti.
- Connessione a Internet tramite router & AP generici **e doppio ISP** (ridondanza).

---
## 2. Comunicazione sede - personale in loco
Il personale in loco (validatori, assistenti, pronto intervento) usa **smartphone o tablet** con connessione **4G/5G** alla rete dati mobile.

- **App dedicata** installata sui dispositivi che permette di:
    - Ricevere aggiornamenti in tempo reale sullo stato dei dispositivi remoti (barriere, semafori, pannelli)
    - Comunicare con la sala controllo tramite messaggistica o VoIP
    - Consultare la mappa dell'area evento con indicazioni sul flusso
- **Validazione biglietti:** il personale usa il dispositivo mobile per scansionare il **QR code** presente sul biglietto (cartaceo o digitale). Il dispositivo si collega in tempo reale al server centrale per verificare la validità e segnare il biglietto come utilizzato, evitando duplicati.
- **Comunicazione voce:** oltre all'app, si può prevedere un sistema **PTT (Push-To-Talk)** su rete 4G/5G come alternativa ai classici walkie-talkie, più affidabile in aree affollate.
- **Sicurezza delle comunicazioni:** tutto il traffico tra app e server avviene su **HTTPS/TLS**, con autenticazione degli operatori tramite credenziali o token.    

---
## 3. Connessione ai totem
I totem sono distribuiti sull'intera area del comune, quindi non sempre raggiungibili via cavo:
- Dove possibile: **connessione cablata** (fibra o Ethernet) tramite la rete comunale
- Altrove: **connessione 4G/5G** con SIM dedicata per ogni totem
- Comunicazione via **HTTPS** per sicurezza delle transazioni di acquisto
- Aggiornamenti dei contenuti (eventi, disponibilità biglietti) gestiti centralmente dal server

---
## 4. Alta disponibilità
- **Doppio ISP** con failover automatico in caso di guasto di una linea
- **UPS** (gruppi di continuità) su tutti i dispositivi critici (server, switch, NVR)
- **Server in cluster** o con replica: se un server cade, un altro prende il suo posto senza interruzioni
- **Backup periodico** del database biglietti su storage separato o cloud
- **Connessione mobile come backup** anche per la sede operativa in caso di guasto della linea fissa

---
## Seconda Parte
### Quesito I – Salvataggio filmati
- _In sede_: NAS/SAN → controllo totale, bassa latenza, costi hw elevati
- _Cloud_: scalabile, accessibile ovunque, dipendente dalla banda, costi ricorrenti
- Soluzione ibrida: archivio recente in sede, storico su cloud
### Quesito II – Dispositivi remoti con server HTTP
- Ogni dispositivo espone API REST
- `GET /status` → legge lo stato (es. semaforo rosso/verde)
- `POST /command` con body JSON → invia un comando (es. `{"action":"open"}` per barriera)
- Autenticazione con token (es. Bearer token) per sicurezza
- Esempio: `POST http://192.168.x.x/barrier {"action":"lower"}`