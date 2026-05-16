# OpenClaw USB Portable ⚡

Esegui OpenClaw da un workspace portabile su Windows, Linux e macOS.

<p>
  <img alt="Windows" src="https://img.shields.io/badge/Windows-run.bat-0078D4?style=flat-square">
  <img alt="Linux" src="https://img.shields.io/badge/Linux-run.sh-FCC624?style=flat-square">
  <img alt="macOS" src="https://img.shields.io/badge/macOS-run.sh-000000?style=flat-square">
  <img alt="Portable Node" src="https://img.shields.io/badge/Node.js-portable-339933?style=flat-square">
  <img alt="License" src="https://img.shields.io/badge/license-MIT-blue?style=flat-square">
</p>

OpenClaw USB Portable è un progetto launcher per chi vuole lo stesso workspace OpenClaw disponibile su più computer, senza installare Node.js, npm o OpenClaw globalmente su ogni macchina.

I punti d'ingresso sono volutamente semplici:

```text
run.bat   Windows
run.sh    Linux e macOS
Tutto il resto è runtime interno, configurazione o dati del workspace portabile.

Cosa fa ✨
Scarica un runtime Node.js portabile nella cartella del progetto al primo avvio.
Installa OpenClaw in una cartella locale al progetto.
Mantiene config, sessioni, file del workspace, memoria e stato generato sotto data/.
Usa un unico workspace portabile condiviso su Windows, Linux e macOS.
Esclude da Git i file runtime generati, i log, le credenziali e la cronologia delle chat.
Questo è un workspace portabile, non un singolo binario universale. Ogni sistema operativo ha il proprio runtime perché Windows, Linux e macOS usano binari diversi.

Avvio rapido 🚀
Windows
Doppio clic su:

run.bat
Oppure da PowerShell:

.\run.bat
Linux e macOS
sh run.sh
Il primo avvio su ogni sistema operativo richiede una connessione internet per scaricare il runtime e installare OpenClaw. Successivamente, lo stesso sistema può riutilizzare il runtime portabile dall'unità.

Menu principale
Portable OpenClaw
1. Setup / Cambia AI
2. Chat
3. Dashboard
4. Strumenti
5. Esegui comando OpenClaw
0. Esci
Usa Setup / Cambia AI per prima cosa per configurare il provider del modello. Poi usa Chat o Dashboard per il lavoro quotidiano.

Esegui comando OpenClaw è disponibile per i comandi mostrati da OpenClaw stesso, ad esempio:

openclaw pairing approve telegram R2F8ZL5S
Modello dati portabile
Lo stato condiviso si trova sotto data/:

data/
  config/       Configurazione OpenClaw
  openclaw/     Stato OpenClaw, sessioni, log, memoria, dati canvas
  home/         Home directory portabile usata dagli strumenti
  workspace/    File su cui lavora l'agente
  temp/         File temporanei
I file specifici per piattaforma si trovano fuori da data/:

runtime/        Runtime Node.js portabili
packages/       Installazioni OpenClaw e cache npm
logs/           Log del launcher e dell'installazione
Queste cartelle sono ignorate da Git perché possono contenere binari grandi, log locali, credenziali, cronologia delle chat o stato specifico della macchina.

Struttura del progetto
OpenClaw-USB-Portable/
  run.bat
  run.sh
  README.md
  LICENSE
  .gitignore
  .gitattributes
  bin/
    windows.ps1
    unix.sh
    portable-env.ps1
    portable-env.sh
  templates/
    openclaw.portable.json
  data/
    .gitkeep
Perché è incluso .gitattributes
I launcher richiedono terminazioni di riga corrette:

*.bat  CRLF
*.ps1  CRLF
*.sh   LF
Questo mantiene gli script Windows compatibili su Windows e gli script shell eseguibili su Linux/macOS.

Cosa non viene committato
Il repository esclude intenzionalmente:

runtime/
packages/
logs/
data/config/
data/openclaw/
data/home/
data/workspace/
data/temp/
Non committare queste cartelle a meno che tu non voglia pubblicare intenzionalmente file runtime locali o dati privati del workspace.

Casi d'uso tipici
Portare lo stesso workspace OpenClaw tra laptop diversi.
Usare OpenClaw su una macchina pulita senza installare Node.js globalmente.
Tenere insieme configurazione del modello, sessioni e file del workspace in una cartella portabile.
Registrare demo o tutorial senza dipendere dall'ambiente di sviluppo specifico della macchina.
Note
Il primo avvio per ogni OS richiede internet.
Il launcher usa l'accesso Gateway in loopback locale per Chat e Dashboard.
Chiavi API, token bot, sessioni e stato generato appartengono alle cartelle data/ ignorate da Git.
