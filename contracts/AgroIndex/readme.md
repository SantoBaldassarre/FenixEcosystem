# AgroIndex

## Sommario:

- [Introduzione](#introduzione)
- [Dipendenze e Librerie](#dipendenze-e-librerie)
- [Variabili Principali](#variabili-principali)
- [Funzionalità Principali](#funzionalità-principali)
- [Codice Sorgente](#codice-sorgente)

### Introduzione

Il contratto `AgroIndex` rappresenta un indice basato sulla media dei prezzi degli AgroToken disponibili nel contratto `FenixSwap`. Il contratto consente di aggiornare il prezzo dell'AgroIndex, calcolare il prezzo medio degli AgroToken e impostare il prezzo.

### Dipendenze e Librerie

Il contratto utilizza diversi contratti e librerie forniti da OpenZeppelin:

- `ERC20`: Implementazione standard del token ERC20.
- `Pausable`: Contratto che consente di mettere in pausa e riprendere le operazioni.
- `Ownable`: Assegna un proprietario al contratto.
- `SafeMath`: Libreria per operazioni aritmetiche sicure.

Inoltre, il contratto importa l'interfaccia del contratto `FenixSwap`.

### Variabili Principali

- `fenixSwap`: Una variabile per il contratto `FenixSwap`.
- `MAX_SUPPLY`: La fornitura massima di token AgroIndex, definita come 21 milioni di token.

### Funzionalità Principali

- `updateAgroIndexPrice()`: Aggiorna il prezzo dell'AgroIndex.
- `calculateAverageAgroTokenPrice()`: Calcola la media dei prezzi di tutti gli AgroToken nel contratto `FenixSwap`.
- `_setPrice()`: Imposta il prezzo dell'AgroIndex.
- `pause()`: Sospende le operazioni del contratto.
- `unpause()`: Riattiva le operazioni del contratto.
- `burn()`: Distrugge una certa quantità di token AgroIndex.

### Codice Sorgente

Ecco un estratto del codice sorgente del contratto:

```solidity
contract AgroIndex is ERC20, Pausable, Ownable {
    using SafeMath for uint256;

    FenixSwap public fenixSwap;
    uint256 public constant MAX_SUPPLY = 21000000 * 10**18;

    constructor(address fenixSwapAddress) ERC20("AgroIndex", "AGIX") {
        ...
    }

    function updateAgroIndexPrice() public {
        ...
    }

    function calculateAverageAgroTokenPrice() internal view returns (uint256) {
        ...
    }
    ...
}
```


## Licenza

Questo contratto è rilasciato sotto la licenza MIT.
