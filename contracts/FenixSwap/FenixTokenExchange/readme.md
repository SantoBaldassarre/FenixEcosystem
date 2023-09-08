
# FenixTokenExchange

## Sommario:

- [Introduzione](#introduzione-fenixtokenexchange)
- [Dipendenze e Librerie](#dipendenze-e-librerie-fenixtokenexchange)
- [Funzionalità Principali](#funzionalità-principali-fenixtokenexchange)
- [Eventi](#eventi-fenixtokenexchange)
- [Codice Sorgente](#codice-sorgente-fenixtokenexchange)

### Introduzione FenixTokenExchange

Benvenuto nel contratto `FenixTokenExchange`. Questo contratto intelligente, scritto in Solidity, serve come piattaforma per lo scambio di token supportati.

### Dipendenze e Librerie FenixTokenExchange

Il contratto utilizza diversi contratti e librerie forniti da OpenZeppelin, e fa riferimento anche al contratto `FenixSwap`.

### Funzionalità Principali FenixTokenExchange

- Gestisce una mappa di token supportati.
- Permette depositi, prelievi e scambi di token.
- Contiene vari eventi per tracciare le operazioni.

### Eventi FenixTokenExchange

- `TokensDeposited`: Emette informazioni quando i token vengono depositati.
- `TokensWithdrawn`: Emette informazioni quando i token vengono prelevati.
- `TokensExchanged`: Emette informazioni durante uno scambio di token.
- `SupportedTokenChanged`: Informa quando un token viene aggiunto o rimosso dalla lista di token supportati.
- `PausedStatusChanged`: Emette informazioni sullo stato di pausa del contratto.

### Codice Sorgente FenixTokenExchange

Ecco un estratto del codice sorgente del contratto FenixTokenExchange:

```solidity
// Contratto per lo scambio di token
contract FenixTokenExchange is Ownable, ReentrancyGuard {
    FenixSwap private fenixSwapContract;
    mapping(address => bool) private supportedTokens;
    bool private paused;
  
    event TokensDeposited(address indexed user, address indexed token, uint256 amount);
    event TokensWithdrawn(address indexed user, address indexed token, uint256 amount);
    event TokensExchanged(address indexed user, address indexed tokenFrom, address indexed tokenTo, uint256 amount);
    event SupportedTokenChanged(address indexed token, bool supported);
    event PausedStatusChanged(bool pausedStatus);

    ... [Codice troncato per brevità] ...
}
```


## Licenza

Questo contratto è rilasciato sotto la licenza MIT.
