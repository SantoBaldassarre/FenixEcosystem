
# FenixSwapMarketPlace

## Sommario:

- [Introduzione](#introduzione-fenixswapmarketplace)
- [Dipendenze e Librerie](#dipendenze-e-librerie-fenixswapmarketplace)
- [Funzionalità Principali](#funzionalità-principali-fenixswapmarketplace)
- [Gestione degli Ordini](#gestione-degli-ordini-fenixswapmarketplace)
- [Codice Sorgente](#codice-sorgente-fenixswapmarketplace)

### Introduzione FenixSwapMarketPlace

Benvenuto nel contratto `FenixSwapMarketPlace`. Questo contratto intelligente, scritto in Solidity, funge da marketplace per la gestione e la tracciabilità degli ordini associati ai token Fenix.

### Dipendenze e Librerie FenixSwapMarketPlace

Il contratto utilizza diversi contratti e librerie forniti da OpenZeppelin, simili a quelli nel contratto `FenixSwap`. Inoltre, fa riferimento al contratto `FenixSwap`.

### Funzionalità Principali FenixSwapMarketPlace

- Gestisce un array di token Fenix validi.
- Tiene traccia degli ordini attraverso la struttura dati `Order`.

### Gestione degli Ordini FenixSwapMarketPlace

Il contratto utilizza una struttura dati chiamata `Order` per rappresentare e gestire gli ordini. Ogni ordine contiene:

- `customer`: L'indirizzo dell'utente che ha effettuato l'ordine.
- `fruitName`: Il nome del frutto associato all'ordine.
- `typeName`: Il tipo di frutto.
- `caliberName`: Il calibro del frutto.
- `quantity`: La quantità di frutto nell'ordine.
- `timestamp`: Il timestamp di quando è stato effettuato l'ordine.

### Codice Sorgente FenixSwapMarketPlace

Ecco un estratto del codice sorgente del contratto FenixSwapMarketPlace:

```solidity
contract FenixSwapMarketPlace is Ownable, Pausable, ReentrancyGuard {
    using SafeMath for uint256;

    // Dichiarazione dell'array per tenere traccia dei token Fenix validi
    address[] public fenixTokens;
    address public paymentAddress;

    // Struttura dati per rappresentare un ordine
    struct Order {
        address customer;
        string fruitName;
        string typeName;
        string caliberName;
        uint256 quantity;
        uint256 timestamp;
    }

  
}
```


## Licenza

Questo contratto è rilasciato sotto la licenza MIT.
