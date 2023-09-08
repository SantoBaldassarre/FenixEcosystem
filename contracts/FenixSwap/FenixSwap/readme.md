# FenixSwap

## Sommario:

- [Introduzione](#introduzione-fenixswap)
- [Dipendenze e Librerie](#dipendenze-e-librerie-fenixswap)
- [Funzionalità Principali](#funzionalità-principali-fenixswap)
- [Gestione del Lotto](#gestione-del-lotto-fenixswap)
- [Gestione dei Token Fenix](#gestione-dei-token-fenix-fenixswap)
- [Controllo e Gestione](#controllo-e-gestione-fenixswap)
- [Eventi](#eventi-fenixswap)
- [Codice Sorgente](#codice-sorgente-fenixswap)

### Introduzione FenixSwap

Benvenuto nel contratto `FenixSwap`. Questo contratto intelligente, scritto in Solidity, gestisce operazioni legate a lotti e token Fenix.

### Dipendenze e Librerie FenixSwap

Il contratto utilizza diversi contratti e librerie forniti da OpenZeppelin:

- `IERC20`: Interfaccia standard per i token ERC20.
- `Pausable`: Contratto che consente di mettere in pausa e riprendere le operazioni.
- `ReentrancyGuard`: Fornisce protezione contro attacchi di reentrancy.
- `SafeMath`: Libreria per operazioni aritmetiche sicure.
- `Ownable`: Assegna un proprietario al contratto.

### Funzionalità Principali FenixSwap

- Gestione di un token chiamato `fenixToken`.
- Funzionalità legate alla gestione dei lotti.
- Funzionalità per depositare e prelevare token Fenix.
- Controllo del contratto tramite funzioni di pausa e riattivazione.

### Gestione del Lotto FenixSwap

- `addLot`: Aggiunge un nuovo lotto.
- `removeLot`: Rimuove un lotto esistente.
- `getLotInfo`: Fornisce informazioni su un lotto specifico.
- `selectCaliber` & `deselectCaliber`: Seleziona o deseleziona un calibro per un lotto.

### Gestione dei Token Fenix FenixSwap

- `getAgroTokenBalance`: Restituisce il saldo di `AgroToken` per un tipo di frutto.
- `getFenixTokenBalance`: Restituisce il saldo di `FenixToken`.
- `depositFenixTokens`: Deposita token `Fenix`.
- `withdrawFenixTokens`: Preleva token `Fenix`.

### Controllo e Gestione FenixSwap

- `pause` & `unpause`: Mette in pausa e riattiva il contratto.

### Eventi FenixSwap

- `AgroTokensWithdrawn`
- `FenixTokensDeposited`
- `FenixTokensWithdrawn`
- `LotAdded`
- `LotRemoved`
- ... [Altri eventi correlati alle funzioni del lotto]

### Codice Sorgente FenixSwap

Ecco un estratto del codice sorgente del contratto FenixSwap:

```solidity
// Definizione del contratto FenixSwap
contract FenixSwap is Ownable, Pausable, ReentrancyGuard {
    // Utilizzo di SafeMath per gestire operazioni aritmetiche evitando overflow
    using SafeMath for uint256;

    // Definizione del token stabile Fenix che verrà utilizzato per lo scambio
    IERC20 public fenixToken;

    // Eventi per tracciare operazioni sul contratto
    event AgroTokensWithdrawn(address indexed user, uint256 amount);
    event FenixTokensDeposited(address indexed user, uint256 amount);
    event FenixTokensWithdrawn(address indexed user, uint256 amount);
    event LotAdded(string fruitName, uint256 quantity);
    event LotRemoved(string fruitName);

  
}
```


## Licenza

Questo contratto è rilasciato sotto la licenza MIT.
