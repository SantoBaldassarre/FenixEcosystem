# AgroTokenFactory

**Sommario:**

- [Introduzione](#introduzione)
- [Funzionalità Principali](#funzionalità-principali)
- [Installazione e Utilizzo](#installazione-e-utilizzo)
- [Codice Sorgente](#codice-sorgente)
- [Licenza](#licenza)

## Introduzione

Benvenuto nel repository di AgroTokenFactory. Questo contratto intelligente, scritto in Solidity, consente la creazione di nuovi token AgroToken. AgroTokenFactory offre una soluzione per la creazione e la gestione di token personalizzati nel mondo dell'agricoltura.

## Funzionalità Principali

Le principali funzionalità del contratto AgroTokenFactory includono:

- **Creazione di AgroToken**: Gli utenti possono creare nuovi token AgroToken specificando il nome, il simbolo e l'offerta iniziale. I nuovi token creati vengono assegnati all'owner.
- **Controllo degli Accessi**: Il contratto implementa un sistema di controllo degli accessi, consentendo all'owner di gestire l'aggiunta e la rimozione degli indirizzi dalla blacklist e dalla whitelist.
- **Pausa e Ripresa**: Il contratto può essere messo in pausa e ripreso per gestire le transazioni di token. Solo l'owner può attivare queste operazioni.

## Installazione e Utilizzo

### Ambiente di Sviluppo

Per iniziare a sviluppare e testare AgroTokenFactory, segui questi passaggi per configurare il tuo ambiente di sviluppo:

1. **Installazione di Node.js e npm**: Assicurati di avere Node.js e npm (Node Package Manager) installati sulla tua macchina.
2. **Truffle Framework**: Installa Truffle, un framework per lo sviluppo di contratti intelligenti Ethereum.
3. **Ganache**: Scarica e avvia Ganache, un ambiente di sviluppo Ethereum locale con una blockchain privata.
4. **Installazione delle Dipendenze**: Naviga nella cartella del progetto e installa le dipendenze.

### Compilazione e Deploy

Dopo aver configurato l'ambiente di sviluppo, puoi compilare e deployare il contratto AgroTokenFactory sulla tua blockchain locale.

## Codice Sorgente

Ecco una parte del codice sorgente del contratto AgroTokenFactory:

```solidity
// SPDX-License-Identifier: MIT
// Developer: Santo Baldassarre

pragma solidity ^0.8.19;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/security/Pausable.sol";
import "@openzeppelin/contracts/security/ReentrancyGuard.sol";
import "@openzeppelin/contracts/utils/math/SafeMath.sol";

// Il contratto AgroTokenFactory può creare nuovi token AgroToken.
contract AgroTokenFactory is Ownable, ReentrancyGuard {
    // Evento emesso quando un nuovo token AgroToken viene creato.
    event AgroTokenCreated(address indexed tokenAddress, string name, string symbol);

    // Funzione per creare un nuovo AgroToken.
    // Solo l'owner può creare nuovi token.
    // Emite un evento AgroTokenCreated.
    function createAgroToken(string memory name, string memory symbol, uint256 initialSupply) external onlyOwner nonReentrant returns (address) {
        AgroToken newToken = new AgroToken(name, symbol, initialSupply, msg.sender);
        emit AgroTokenCreated(address(newToken), name, symbol);
        return address(newToken);
    }
}
```


## Licenza

Questo contratto è rilasciato sotto la licenza MIT.
