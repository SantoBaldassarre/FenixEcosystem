# FenixFidelity

## Sommario:

- [Introduzione](#introduzione)
- [Dipendenze e Librerie](#dipendenze-e-librerie)
- [Strutture e Variabili](#strutture-e-variabili)
- [Funzionalità Principali](#funzionalità-principali)
- [Eventi](#eventi)
- [Codice Sorgente](#codice-sorgente)

### Introduzione

Il contratto `FenixFidelity` è progettato per gestire un programma di fedeltà. Gli utenti possono guadagnare punti attraverso acquisti e scambi, e riscattarli per ricompense o per accedere a eventi esclusivi. Alcune ricompense possono anche includere un token NFT come voucher.

### Dipendenze e Librerie

Il contratto utilizza diversi contratti e librerie forniti da OpenZeppelin:

- `IERC20`: Interfaccia standard del token ERC20.
- `SafeMath`: Libreria per operazioni aritmetiche sicure.
- `Ownable`: Assegna un proprietario al contratto.
- `Pausable`: Contratto che consente di mettere in pausa e riprendere le operazioni.
- `ERC721`: Implementazione standard del token NFT.

### Strutture e Variabili

- `Reward`: Una struttura per rappresentare una ricompensa o un evento nel programma di fedeltà.
- `points`: Una mappa che collega gli indirizzi degli utenti ai loro punti guadagnati.
- `redeemedPoints`: Una mappa che collega gli indirizzi degli utenti ai punti già riscattati.
- `rewards`: Una mappa che collega gli ID delle ricompense ai dettagli delle ricompense.

### Funzionalità Principali

- `addPoints()`: Consente agli utenti di aggiungere punti al loro saldo.
- `redeemPoints()`: Consente agli utenti di riscattare punti per ricompense.
- `checkExclusiveEventAccess()`: Controlla se un utente ha accesso a un evento esclusivo.
- `grantExclusiveEventAccess()`: Concede l'accesso a un evento esclusivo.
- `addReward()`: Aggiunge una nuova ricompensa al programma.
- `setMinimumBalance()`: Imposta il saldo minimo per accedere a un evento.
- `setExchangeRate()`: Imposta il tasso di cambio per convertire i token in punti.

### Eventi

- `PointsAdded`: Emette informazioni quando vengono aggiunti punti a un utente.
- `PointsRedeemed`: Emette informazioni quando un utente riscatta i punti.
- `ExclusiveEventAccess`: Emette informazioni quando a un utente viene concesso l'accesso a un evento esclusivo.
- `RewardAdded`: Emette informazioni quando viene aggiunta una nuova ricompensa.
- `RewardDistributed`: Emette informazioni quando una ricompensa viene distribuita.
- `NFTIssued`: Emette informazioni quando viene emesso un nuovo NFT come voucher.

### Codice Sorgente

Ecco un estratto del codice sorgente del contratto:

```solidity
contract FenixFidelity is Ownable, Pausable {
    using SafeMath for uint256;

    struct Reward {
        string eventType;
        ...
    }
  
    address public tokenAddress;
    mapping(address => uint256) public points;
    ...
  
    function addPoints(uint256 _amount) public whenNotPaused {
        ...
    }
  
    function redeemPoints(uint256 _amount) public whenNotPaused {
        ...
    }
  
    ...
}
```


## Licenza

Questo contratto è rilasciato sotto la licenza MIT.
