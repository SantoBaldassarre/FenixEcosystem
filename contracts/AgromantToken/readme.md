# AgroMantToken


## Sommario:

- [Introduzione](#introduzione-agromanttoken)
- [Dipendenze e Librerie](#dipendenze-e-librerie-agromanttoken)
- [Funzionalità Principali](#funzionalità-principali-agromanttoken)
- [Eventi](#eventi-agromanttoken)
- [Codice Sorgente](#codice-sorgente-agromanttoken)

### Introduzione

Benvenuto nel contratto `AgroMantToken`. Questo contratto intelligente, scritto in Solidity, rappresenta un token ERC20 con funzionalità aggiuntive come staking, farming, votazione e la capacità di creare proposte.

### Dipendenze e Librerie

Il contratto utilizza diversi contratti e librerie forniti da OpenZeppelin:

- `ERC20`: Implementazione standard del token ERC20.
- `SafeERC20`: Fornisce funzioni sicure per interagire con i token ERC20.
- `ReentrancyGuard`: Fornisce protezione contro attacchi di reentrancy.
- `Pausable`: Contratto che consente di mettere in pausa e riprendere le operazioni.
- `SafeMath`: Libreria per operazioni aritmetiche sicure.
- `Ownable`: Assegna un proprietario al contratto.

### Funzionalità Principali

- Possibilità di creare, votare e gestire proposte.
- Funzionalità di staking che permette agli utenti di bloccare i loro token e ricevere ricompense.
- Funzionalità di burning accessibile solo al proprietario del contratto.
- Funzionalità per mettere in pausa e riprendere le operazioni del contratto.

### Eventi

- `Staked`: Emette informazioni quando i token vengono bloccati (staked).
- `Withdrawn`: Emette informazioni quando i token vengono prelevati dopo lo staking.
- `RewardClaimed`: Emette informazioni quando un utente ritira le sue ricompense di staking.
- `ProposalCreated`: Informa quando viene creata una nuova proposta.
- `Voted`: Emette informazioni quando un utente vota su una proposta.

### Codice Sorgente

```solidity
contract AgroMantToken is ERC20, ReentrancyGuard, Ownable, Pausable {
    using SafeERC20 for IERC20;
    using SafeMath for uint256;

    uint256 public MAX_SUPPLY;
    uint256 public constant REWARD_RATE = 10;
    uint256 public constant BLOCKS_PER_DAY = 6500;

    uint256 private _totalStaked;
    mapping(address => uint256) private _stakedBalances;
    mapping(address => uint256) private _lastClaimed;

    event Staked(address indexed user, uint256 amount);
    event Withdrawn(address indexed user, uint256 amount);
    event RewardClaimed(address indexed user, uint256 amount);

    struct Proposal {
        string description;
        uint256 yesVotes;
        uint256 noVotes;
        mapping(address => bool) hasVoted;
    }

    uint256 public proposalCount;
    mapping(uint256 => Proposal) public proposals;
}
```


## Licenza

Questo contratto è rilasciato sotto la licenza MIT.
