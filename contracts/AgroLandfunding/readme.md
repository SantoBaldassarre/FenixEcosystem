# AgroLandfunding

## Sommario:

- [Introduzione](#introduzione)
- [Dipendenze e Librerie](#dipendenze-e-librerie)
- [Strutture e Variabili](#strutture-e-variabili)
- [Funzionalità Principali](#funzionalità-principali)
- [Eventi](#eventi)
- [Codice Sorgente](#codice-sorgente)

### Introduzione

Benvenuto nel contratto `AgroLandfunding`. Questo contratto intelligente, scritto in Solidity, funge da piattaforma di crowdfunding per progetti agricoli. Gli utenti possono investire in diverse campagne e ricevere token NFT come prova del loro investimento, oltre a ricompense in token Agro.

### Dipendenze e Librerie

Il contratto utilizza diversi contratti e librerie forniti da OpenZeppelin:

- `ERC721Enumerable`: Implementazione standard del token NFT con funzionalità di enumerazione.
- `SafeERC20`: Fornisce funzioni sicure per interagire con i token ERC20.
- `ReentrancyGuard`: Fornisce protezione contro attacchi di reentrancy.
- `Pausable`: Contratto che consente di mettere in pausa e riprendere le operazioni.
- `Strings`: Libreria per convertire uint256 in stringhe.
- `Ownable`: Assegna un proprietario al contratto.

### Strutture e Variabili

- `Campaign`: Una struttura che rappresenta una campagna di crowdfunding. Include dettagli come il proprietario, la scadenza, il nome dell'azienda, il tipo di coltura, la posizione, e molto altro.
- `nextCampaignId`: Un contatore per l'ID della prossima campagna.
- `campaigns`: Una mappa che collega gli ID delle campagne alle loro informazioni dettagliate.

### Funzionalità Principali

- `createCampaign()`: Permette agli utenti di creare una nuova campagna di crowdfunding.
- `invest()`: Consente agli utenti di investire in una campagna esistente.
- `getCampaign()`: Fornisce le informazioni dettagliate di una campagna specifica.
- `pause()`: Mette in pausa tutte le operazioni del contratto.
- `unpause()`: Riprende tutte le operazioni del contratto.

### Eventi

- `CampaignCreated`: Emette informazioni quando viene creata una nuova campagna.
- `InvestmentMade`: Emette informazioni quando un utente effettua un investimento in una campagna.
- `AgroRewardGiven`: Emette informazioni quando viene assegnata una ricompensa in token Agro a un investitore.

### Codice Sorgente

Ecco un estratto del codice sorgente del contratto:

```solidity
contract AgroLandfunding is ERC721Enumerable, Ownable, ReentrancyGuard, Pausable {
    using SafeERC20 for IERC20; 
    using Strings for uint256; 

    struct Campaign {
        address owner; 
        uint256 deadline; 
        string company; 
        ...
    }

    uint256 private nextCampaignId = 1; 
    mapping(uint256 => Campaign) private campaigns; 

    constructor() ERC721("AgroLandfunding", "AGRO") {}

    function createCampaign(
        uint256 _deadline,
        ...
    ) external whenNotPaused returns (uint256) {
        ...
    }
  
    ...
}
```


## Licenza

Questo contratto è rilasciato sotto la licenza MIT.
