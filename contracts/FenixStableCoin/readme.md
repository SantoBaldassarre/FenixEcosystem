# FenixStableToken

**Sommario:**

- [Introduzione](#introduzione)
- [Funzionalità Principali](#funzionalità-principali)
- [Installazione e Utilizzo](#installazione-e-utilizzo)
- [Ruoli e Controllo](#ruoli-e-controllo)
- [Limite di Velocità delle Transazioni](#limite-di-velocità-delle-transazioni)
- [Emergenza e Interruzione](#emergenza-e-interruzione)
- [Documentazione Aggiuntiva](#documentazione-aggiuntiva)
- [Licenza](#licenza)

## Introduzione

Benvenuto nel repository di FenixStableToken. Questo contratto intelligente, scritto in Solidity, offre un'ampia gamma di funzionalità per la gestione dei token Fenix (FNX). FenixStableToken consente la creazione, il deposito (stake), la riscossione e la distribuzione dei token FNX, fornendo un ecosistema flessibile per gli utenti.

## Funzionalità Principali

Le principali funzionalità del contratto FenixStableToken includono:

- **Creazione (Minting) e Riscossione (Burning)**: Gli utenti possono convertire USDC in token FNX tramite la funzione `collateralize`, e viceversa tramite `redeem`.
- **Staking e Ritiro**: Gli utenti possono depositare token FNX per guadagnare rendimenti attraverso la funzione `stake`, e ritirarli tramite `unstake`.
- **Distribuzione di Token**: FenixStableToken supporta la distribuzione di token FNX tramite funzioni come `airdrop`, `payEmployees`, `commercialRefund`, rendendo possibile la distribuzione automatica o manuale ai destinatari desiderati.

## Installazione e Utilizzo

### Ambiente di Sviluppo

Per iniziare a sviluppare e testare FenixStableToken, segui questi passaggi per configurare il tuo ambiente di sviluppo:

1. **Installazione di Node.js e npm**: Assicurati di avere Node.js e npm (Node Package Manager) installati sulla tua macchina.
2. **Truffle Framework**: Installa Truffle, un framework per lo sviluppo di contratti intelligenti Ethereum.
3. **Ganache**: Scarica e avvia Ganache, un ambiente di sviluppo Ethereum locale con una blockchain privata.
4. **Installazione delle Dipendenze**: Naviga nella cartella del progetto e installa le dipendenze.

### Compilazione e Deploy

Dopo aver configurato l'ambiente di sviluppo, puoi compilare e deployare il contratto FenixStableToken sulla tua blockchain locale.

## Ruoli e Controllo

FenixStableToken implementa un sistema di ruoli per il controllo delle operazioni critiche:

- `MINTER_ROLE`: Ruolo per la creazione (minting) di token FNX.
- `BURNER_ROLE`: Ruolo per la riscossione (burning) di token FNX.
- Altri ruoli possono essere assegnati o revocati tramite funzioni specifiche del contratto.

## Limite di Velocità delle Transazioni

Per prevenire l'abuso del contratto, FenixStableToken implementa un limite di velocità delle transazioni. Gli utenti possono eseguire transazioni solo se è trascorso un certo intervallo di tempo dall'ultima transazione. Il limite attuale è impostato a X secondi tra le transazioni per ciascun indirizzo.

## Emergenza e Interruzione

Il contratto può essere messo in modalità di emergenza o interruzione temporanea tramite la funzione `toggleEmergencyStop`. Questa modalità interrompe temporaneamente alcune delle funzioni chiave del contratto. Solo l'owner del contratto può attivare o disattivare questa modalità.

## Codice Sorgente

Ecco una parte del codice sorgente del contratto FenixStableToken:

```solidity
```solidity
// SPDX-License-Identifier: MIT
// Developer: Santo Baldassarre

pragma solidity ^0.8.19;

import "@openzeppelin/contracts/token/ERC20/IERC20.sol"; // Interfaccia standard per token ERC20.
import "@openzeppelin/contracts/token/ERC20/ERC20.sol"; // Implementazione base di un token ERC20.
import "@openzeppelin/contracts/security/Pausable.sol"; // Contratto che consente di interrompere (pausare) e riprendere l'attività del contratto.
import "@openzeppelin/contracts/access/Ownable.sol"; // Contratto che assegna un proprietario che può essere successivamente cambiato.
import "@openzeppelin/contracts/access/AccessControl.sol"; // Contratto che fornisce un sistema di controllo degli accessi basato su ruoli.
import "@openzeppelin/contracts/utils/math/SafeMath.sol"; // Libreria per operazioni matematiche sicure.
import "@openzeppelin/contracts/security/ReentrancyGuard.sol"; // Contratto che previene attacchi di reentrancy.

// Contratto del token FenixStable.
contract FenixStableToken is ERC20, Pausable, Ownable, AccessControl, ReentrancyGuard {
    using SafeMath for uint256; // Utilizza SafeMath per operazioni con uint256.

    // L'interfaccia del token USDC.
    IERC20 public usdc;

    // Definisce ruoli per le operazioni di minting e burning.
    bytes32 public constant MINTER_ROLE = keccak256("MINTER_ROLE");
    bytes32 public constant BURNER_ROLE = keccak256("BURNER_ROLE");

    // Limite di velocità per le transazioni.
    mapping(address => uint256) public lastTx;
    uint256 public rateLimit =  10 seconds;

    // Funzione per impostare il limite di velocità delle transazioni.
    function setRateLimit(uint256 newRateLimit) public onlyOwner {
        rateLimit = newRateLimit;
 
```


## Licenza

Questo contratto è rilasciato sotto la licenza MIT.
