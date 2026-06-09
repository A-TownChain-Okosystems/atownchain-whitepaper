# A-TownChain Ökosystem — Offizielles Whitepaper
**Version 2.1.0** | Stand: 09. Juni 2026 | ShivaCore / A-TownChain-Okosystems

---

> *"We don't fork. We build."*
> — ShivaCore, Gründer des A-TownChain Ökosystems

---

## Inhaltsverzeichnis

1. [Executive Summary](#1-executive-summary)
2. [Vision & Mission](#2-vision--mission)
3. [Technische Architektur](#3-technische-architektur)
4. [ATCLang — Proprietäre Programmiersprache](#4-atclang--proprietäre-programmiersprache)
5. [ShivaOS — Dezentrales Betriebssystem](#5-shivaos--dezentrales-betriebssystem)
6. [ShivaConsensus — Hybrid PoH+PoS+PoW](#6-shivaconsensus--hybrid-pohposepow)
7. [ATC-Token Standards](#7-atc-token-standards)
8. [Blockchain-Protokoll-Standards](#8-blockchain-protokoll-standards)
9. [Smart Contracts](#9-smart-contracts)
10. [Wallet & Kryptographie](#10-wallet--kryptographie)
11. [API Gateway & Netzwerk](#11-api-gateway--netzwerk)
12. [Shivamon — NFT Gaming](#12-shivamon--nft-gaming)
13. [Franchise Factory](#13-franchise-factory)
14. [Gemini AI Integration](#14-gemini-ai-integration)
15. [Security Audit v2.1.0](#15-security-audit-v210)
16. [Tokenomics & Wirtschaft](#16-tokenomics--wirtschaft)
17. [Roadmap](#17-roadmap)
18. [Technische Standards](#18-technische-standards)
19. [Rechtliches & Lizenz](#19-rechtliches--lizenz)

---

## 1. Executive Summary

A-TownChain ist ein vollständig proprietäres, dezentrales Blockchain-Ökosystem bestehend aus:

- **ATCLang v0.2.0** — Eigene Blockchain-Programmiersprache (Lexer, Parser, Compiler, VM, REPL, Stdlib)
- **ShivaOS v2.1.0** — Proprietäres dezentrales Betriebssystem (Kernel, ATCFS, ATCNet, ShivaConsensus)
- **ShivaConsensus** — Hybrid-Konsensus: Proof of History + Proof of Stake + Proof of Work
- **20 GitHub-Repositories** — 10 Software + 10 Wiki | 300+ Dateien | 47+ Dokumentationsseiten
- **ATCoin (ATC)** — Native Währung, Chain-ID 9000
- **Shivamon** — NFT-Gaming-Ökosystem (ATC-9000)
- **Franchise Factory** — Dezentrales Business-Protokoll
- **Gemini AI** — KI-Orchestrator mit BYOK-Strategie

**Kern-Philosophie**: Kein POSIX-Klon. Kein EVM-Fork. Vollständig proprietär, von Grund auf neu gebaut.

---

## 2. Vision & Mission

### Vision
Eine dezentrale, KI-gestützte Wirtschafts-Infrastruktur schaffen, die Blockchain, Gaming, Business und
KI in einem proprietären Ökosystem vereint — ohne Abhängigkeit von bestehenden Chains.

### Mission
- Vollständig eigene Technologie-Stack entwickeln (ATC-0001 bis ATC-0008, ATS-1000 bis ATS-1007)
- ATCLang als erste blockchain-native Sprache außerhalb des EVM-Universums etablieren
- Dezentrale Franchise-Wirtschaft on-chain ermöglichen
- KI nahtlos in die Blockchain-Infrastruktur integrieren

### Core-Prinzipien
1. **Proprietär**: Kein Fork. Jede Zeile Code ist original entwickelt.
2. **Sicher**: Reentrancy-Guards, Rate-Limiting, ECDSA, Input-Validation in allen Schichten.
3. **Modular**: `/core`, `/ui`, `/plugins`, `/build`, `/export`, `/frontend`, `/backend`
4. **KI-nativ**: Gemini AI direkt im Orchestrator integriert.
5. **Transparent**: Vollständige Open-Source-Dokumentation via GitHub.

---

## 3. Technische Architektur

```
┌──────────────────────────────────────────────────────────────┐
│                    A-TownChain Ökosystem                     │
├──────────────┬───────────────┬───────────────┬───────────────┤
│   ATCLang    │   ShivaOS     │  Blockchain   │   Services    │
│  v0.2.0      │  Kernel       │  Core         │               │
├──────────────┼───────────────┼───────────────┼───────────────┤
│  Lexer       │  Kernel       │  HybridCons   │  Gemini AI    │
│  Parser      │  ATCFS        │  PoH/PoS/PoW  │  Gateway:4000 │
│  Compiler    │  ATCNet P2P   │  ATCoin       │  REST API     │
│  VM (30op)   │  ShivaCons    │  ECDSA Wallet │  WebSocket    │
│  REPL        │  EventBus     │  SmartContr   │  Rate-Limit   │
│  Stdlib(25+) │  ModuleLoader │  ATC-8300     │  Auth/ECDSA   │
│              │               │  ATC-9000     │               │
│              │               │  ATC-9900     │  Shivamon     │
│              │               │  Bridge       │  Franchise    │
├──────────────┴───────────────┴───────────────┴───────────────┤
│              Frontend Dashboard (Neon Dark Theme)            │
│         Port 3000 | React-less | Vanilla HTML/JS             │
└──────────────────────────────────────────────────────────────┘
```

### Repository-Übersicht
| Repository | Beschreibung | Dateien |
|-----------|-------------|---------|
| a-townchain-os | Haupt-Repo, Unified-Start | 97+ |
| atclang | Compiler-Stack | 27+ |
| shivaos-kernel | OS-Kern | 15+ |
| atcnet | P2P Stack | 6+ |
| atc-standards | ATC/ATS Standards | 5+ |
| atc-contracts | Smart Contracts | 22+ |
| shivamon | NFT Gaming | 8+ |
| atc-gateway | API Gateway | 9+ |
| atc-ui | Dashboard | 2+ |
| franchise-factory | Business-Protokoll | 8+ |

---

## 4. ATCLang — Proprietäre Programmiersprache

### Überblick
# ATCLang — Die Programmiersprache des A-TownChain Ökosystems
Version: 0.1.0-alpha
Datum: 2026-06-06

## Philosophie
ATCLang ist eine statisch typisierte, blockchain-native Sprache.
Keine Abhängigkeit von Python-Syntax. Eigene Grammatik. Eigene VM.

## Syntax-Beispiel

```atclang
// Wallet erstellen
wallet myWallet = ATC::Wallet::new("ShivaCore")
contract ShivaToken : ATC-8300 {
    state balance: Map<Address, UInt256>
    fn transfer(to: Address, amount: UInt256) -> Bool {
        require(balance[caller] >= amount)
        balance[caller] -= amount
        balance[to] += amount
        emit Transfer(caller, to, amount)
        return true
    }
}
```

## Token-Typen
- KEYWORD: wallet, contract, fn, state, emit, require, return
- TYPE: UInt256, Address, Bool, String, Map, List
- OPERATOR: +, -, *, /, >=, <=, ==, !=, ->, ::
- LITERAL: Integer, String, Bool
- SPECIAL: ATC:: (Namespace), @decorator


### Typ-System
- Ganzzahlen: `u8`, `u16`, `u32`, `u64`, `u128` (unsigned, overflow-geschützt)
- Boolean: `bool`
- Text: `string` (UTF-8, max 64 KB)
- Krypto: `bytes32` (Hash-Werte)
- Blockchain: `Address` (ATC + 32 Hex-Zeichen = 35 Zeichen)
- Collections: `Map<K,V>`, `Vec<T>`
- Custom: `struct`, `enum`

### Sicherheits-Built-ins
```atclang
safe_add(a, b)          // Overflow-Schutz
safe_sub(a, b)          // Underflow-Schutz
safe_mul(a, b)          // Overflow-Schutz
require(cond, msg)      // Guard-Assertion
is_valid_address(s)     // ATC-Adressvalidierung
caller                  // Unveränderlicher Aufrufer
```

### Compiler-Sicherheit (v2.1.0)
- `MAX_SOURCE_SIZE = 1 MB` — DoS-Schutz
- `MAX_COMPILE_DEPTH = 64` — Stack-Overflow-Schutz
- Null-Byte-Erkennung in Quellcode
- Label-Cache für O(1)-Lookups

### VM-Sicherheit (v2.1.0)
- `MAX_CALL_DEPTH = 128` — Rekursions-Schutz
- Gas-Limit: 10.000.000/TX
- Stack-Underflow-Schutz

---

## 5. ShivaOS — Dezentrales Betriebssystem

### Kernel (ATS-1000)
```
ShivaKernel
├── ProcessManager  PID, Spawn, Kill, States
├── MemoryManager   Isolation pro Prozess
├── IPC-Channels    Typisierte Kommunikation
├── EventBus        Pub/Sub, Ringbuffer (500 max)
└── ModuleLoader    Dynamisches Plugin-System
```

### ATCFS (ATS-1003)
Dezentrales Dateisystem — kein POSIX, vollständig proprietär.
- INode-Typen: FILE, DIRECTORY, SYMLINK, CHAIN_STATE, CONTRACT
- Berechtigungen: Owner/Group/Other (read/write/execute)
- Blockchain-Integration: Contract-Bytecode direkt in FS

### ATCNet (ATS-1004 + ATC-0005)
P2P Kademlia DHT — proprietäre Implementierung.
- K-Bucket Größe: 20
- Ports: P2P=4001, Bootstrap=5005, WebSocket=9944
- Rate-Limit: 100 Nachrichten/60s/Peer (v2.1.0)
- Message-Size: max 64 KB (v2.1.0)

---

## 6. ShivaConsensus — Hybrid PoH+PoS+PoW

### Phase 1: Proof of History (VDF)
Verkettete SHA-256-Sequenz beweist vergangene Zeit ohne zentralen Zeitstempel-Server.

### Phase 2: Proof of Stake (Reputation)
- Minimum-Stake: 10.000 ATC
- Validator-Auswahl: Weighted-Random via SHA-256-Seed
- Slashing bei Fehlverhalten

### Phase 3: Proof of Work (SHA3-ATC)
- Standard-Difficulty: 4
- Anpassung alle 2.016 Blöcke
- Block-Reward: halbiert alle 210.000 Blöcke

# 🔐 Hybrid Consensus — Technische Dokumentation

> **Algorithmus:** SHA-256 PoW + PoS + PoH
> **Datei:** `blockchain/consensus/hybrid_consensus.py`

---

## Überblick

A-TownChain verwendet einen **dreistufigen hybriden Konsens-Mechanismus**:

```
Schritt 1: PoH   → Kryptographischer Zeitbeweis (Proof of History)
Schritt 2: PoW   → Miner sucht SHA-256 Hash mit N führenden Nullen
Schritt 3: PoS   → Validator bestätigt Block (gewichtet nach Stake)
```

Alle drei Schritte müssen erfüllt sein, damit ein Block gültig ist.

---

## SHA-256 Proof of Work

| Parameter | Wert |
|-----------|------|
| Algorithmus | SHA-256 (doppelt) |
| Difficulty | Anfangswert: 3 führende Nullen |
| Ziel-Blockzeit | 10 Sekunden |
| Difficulty-Anpassung | Nach jedem Block |
| Halving-Intervall | 210.000 Blöcke |
| Start-Reward | 50 ATC |

### Difficulty-Anpassung

```python
def adjust_difficulty(self, avg_block_time: float, target: float = 10.0) -> int:
    if avg_block_time < target * 0.9:   # zu schnell → schwerer
        self.difficulty += 1
    elif avg_block_time > target * 1.1: # zu langsam → leichter
        if self.difficulty > 1:
            self.difficulty -= 1
    self.target = "0" * self.difficulty
    return self.difficulty
```

---

## Proof of Stake

| Parameter | Wert |
|-----------|------|
| Min. Stake | 10.000 ATC |
| Auswahl | Weighted Random (proportional zum Stake) |
| Slashing | 50% Verlust bei double-sign |
| Unstaking | Sofort möglich |

### Validator-Auswahl (deterministisch)

```python
def select_validator(self, seed: str) -> str:
    # Seed = Block-Hash → deterministisch, nicht manipulierbar
    rng = random.Random(int(hashlib.sha256(seed.encode()).hexdigest(), 16))
    total = sum(self.validators.values())
    r, cumulative = rng.uniform(0, total), 0
    for addr, stake in self.validators.items():
        cumulative += stake
        if r <= cumulative:
            return addr
```

---

## Proof of History

| Parameter | Wert |
|-----------|------|
| Algorithmus | Rekursives SHA-256 |
| Sequenz | Unbegrenzt (monoton steigend) |
| Verifikation | Unabhängig von Netzwerk möglich |
| Inspiration | Solana PoH |

```python
def tick(self, data: bytes = None) -> dict:
    combined = (self.current_hash + (data.hex() if data else "")).encode()
    self.current_hash = hashlib.sha256(combined).hexdigest()
    self.sequence += 1
    return {"sequence": self.sequence, "hash": self.current_hash}
```

---

## Block-Erstellung (Hybrid)

```
Input: transactions[], miner_address

1. poh_entry = poh.tick(json(transactions))
   → Zeitstempel-Beweis für diesen Block

2. block_data = {
     height, prev_hash,
     poh_hash, poh_sequence,
     transactions, miner, timestamp
   }

3. pow_result = pow.mine_block(block_data)
   → Nonce + gültiger Hash

4. validator = pos.select_validator(pow_result.hash)
   → Deterministisch aus Stake-Gewichten

5. block_data += { hash, nonce, validator, reward }

6. blocks.append(block_data)
   → Block final
```

---

> **Dokument:** `docs/architecture/CONSENSUS.md`
> **Datum:** 2026-05-19 · **Autor:** ShivaCoreDev × Aurora AI


---

## 7. ATC-Token Standards

### ATC-8300 — Fungible Token
```atclang
contract FungibleToken {
    state name_:         string
    state symbol_:       string
    state decimals_:     u8    = 18
    state total_supply_: u128  = 0
    state MAX_SUPPLY:    u128
    state balances:      Map<Address, u128>
    state allowances:    Map<Address, Map<Address, u128>>

    fn transfer(to: Address, amount: u128) -> bool
    fn approve(spender: Address, amount: u128) -> bool
    fn mint(to: Address, amount: u128) -> bool   // Owner only
    fn burn(amount: u128) -> bool
}
```

### ATC-9000 — NFT Standard
```atclang
contract NFT {
    state name_:         string
    state symbol_:       string
    state max_supply_:   u64
    state tokens:        Map<u64, TokenData>

    fn mint(to: Address, ...) -> u64    // DNA = sha256(owner+id+ts)
    fn transfer(to: Address, token_id: u64) -> bool
    fn owner_of(token_id: u64) -> Address
    fn tokens_of(addr: Address) -> Vec<u64>
}
```

### ATC-9900 — Governance DAO
```atclang
contract GovernanceDAO {
    fn create_proposal(title, description, options) -> string
    fn vote(voter, proposal_id, option) -> dict
    fn finalize_proposal(proposal_id) -> dict   // Nach 7 Tagen
    fn execute_proposal(caller, proposal_id)    // Nach 48h Timelock
}
```

# 🪙 ATC Token Standard — Übersicht

> Technische Kurzreferenz aller ATC Token Standards

| Standard | Typ | Datei | Status |
|----------|-----|-------|--------|
| ATC-001 | Genesis Token | `blockchain/smart_contracts.py` | ✅ |
| ATC-8300 | Fungible Token | `blockchain/atcoin/atcoin.py` | ✅ |
| ATC-9000 | NFT (Shivamon) | `blockchain/contracts/shivamon/shivamon_contract.py` | ✅ |
| ATC-9900 | Governance/DAO | geplant | ⏳ v2.1 |

→ Vollständige Dokumentation: [SHIVAMON_NFT_CONTRACT.md](./SHIVAMON_NFT_CONTRACT.md)


---

## 8. Blockchain-Protokoll-Standards

# ATC Standards — A-TownChain Core Standards
Version: 1.0.0 | Status: DRAFT | Datum: 2026-06-06
Autor: ShivaCore / Aurora

> Alle ATC-Standards sind eigenständig definiert.
> Keine Übernahme aus ERC/EIP oder anderen Blockchains.

---

## ATC-0001 — Core Identity Standard

Jede Entität im A-TownChain Ökosystem besitzt eine eindeutige Identität.

```
IDENTITY := {
    id:       Address,       // ATC-Adresse (35 Zeichen, Präfix "ATC")
    pubkey:   Bytes64,       // Öffentlicher Schlüssel (eigenes ATC-EC)
    created:  UInt64,        // Block-Nummer der Erstellung
    type:     IdentityType,  // WALLET | CONTRACT | NODE | AGENT
}
IdentityType := WALLET | CONTRACT | NODE | AGENT | VALIDATOR
```

---

## ATC-0002 — Wallet Address Format

```
PREFIX    := "ATC"
BODY      := SHA3_ATC(pubkey)[0:32]  // 32 Hex-Zeichen
CHECKSUM  := CRC8(PREFIX + BODY)[0:2]
ADDRESS   := PREFIX + BODY + CHECKSUM  // Gesamt: 37 Zeichen

Beispiel: ATC7a3f9e2b1c8d4a6e0f5b7c9d2e1f3a4b5c6d7e8f9a
```

---

## ATC-0003 — Transaction Schema

```
TX := {
    id:        Hash256,        // SHA3_ATC(Payload)
    from:      Address,        // Sender
    to:        Address,        // Empfänger
    value:     UInt256,        // Menge (in ATCoin, 18 Dezimalstellen)
    data:      Bytes,          // Contract-Calldata (optional)
    nonce:     UInt64,         // Anti-Replay
    gas_limit: UInt64,         // Max. Gas
    gas_price: UInt64,         // Gas-Preis in nano-ATC
    signature: ATCSig,         // ECDSA-Signatur (ATC-EC Kurve)
    timestamp: UInt64,         // Unix-Timestamp
    version:   UInt8 = 1,      // TX-Version
}

ATCSig := {
    r: Bytes32,
    s: Bytes32,
    v: UInt8,   // Recovery ID (0 oder 1)
}
```

---

## ATC-0004 — Block Format

```
BLOCK := {
    header:  BlockHeader,
    txs:     List<TX>,
    receipts: List<TXReceipt>,
}

BlockHeader := {
    version:      UInt8,
    height:       UInt64,
    timestamp:    UInt64,
    prev_hash:    Hash256,
    tx_root:      Hash256,    // Merkle-Root aller TXs
    state_root:   Hash256,    // State-Trie-Root
    receipt_root: Hash256,
    validator:    Address,    // Block-Produzent
    consensus:    ConsensusData,
    nonce:        UInt64,     // PoW-Nonce
    difficulty:   UInt256,
    gas_limit:    UInt64,
    gas_used:     UInt64,
    extra:        Bytes32,    // Freies Feld
}

TXReceipt := {
    tx_id:    Hash256,
    success:  Bool,
    gas_used: UInt64,
    logs:     List<EventLog>,
    error:    Optional<String>,
}
```

---

## ATC-0005 — ShivaConsensus Protocol

Hybrider Mechanismus: PoW + PoS + PoH (Proof of History)

```
Runde := {
    phase_1: PoH_Tick      // Zeitstempel-Kette (VDF-basiert)
    phase_2: PoS_Vote      // Validator-Voting (Stake-gewichtet)
    phase_3: PoW_Seal      // Finaler Hash-Beweis
}

BLOCK_TIME     := 3s
MIN_STAKE      := 1000 ATC
VALIDATOR_SET  := Top-100 nach Stake
FINALITY       := 2/3 Validator-Bestätigung
FORK_RULE      := Längste-gewichtete-Kette (Stake × Länge)
```

---

## ATC-0006 — Smart Contract Interface

```
CONTRACT := {
    address:   Address,
    code_hash: Hash256,     // Hash des Bytecodes
    abi:       List<FuncSpec>,
    state:     StateTree,   // Merkle-Patricia-Trie
    version:   UInt8,
    standard:  ATCStandard, // ATC-8300, ATC-9000, etc.
}

FuncSpec := {
    name:      String,
    inputs:    List<ParamSpec>,
    outputs:   List<ParamSpec>,
    mutates:   Bool,         // ändert State?
    payable:   Bool,         // akzeptiert ATC?
}
```

---

## ATC-0007 — P2P Message Protocol (ATCNet)

```
MSG := {
    version:   UInt8 = 1,
    type:      MsgType,
    from:      NodeID,      // Pubkey-Hash des Senders
    to:        NodeID,      // Ziel (oder broadcast = 0x00)
    payload:   Bytes,
    timestamp: UInt64,
    signature: ATCSig,
    ttl:       UInt8,       // Time-To-Live (Hops)
}

MsgType :=
    HELLO | PING | PONG |
    GET_BLOCKS | BLOCKS |
    GET_TX | TX |
    GET_STATE | STATE |
    CONSENSUS_VOTE | CONSENSUS_BLOCK |
    KI_QUERY | KI_RESPONSE |
    PEER_LIST | DISCONNECT
```

---

## ATC-0008 — KI-OS Process Standard

```
KI_PROCESS := {
    pid:       UInt32,
    name:      String,
    type:      ProcessType,    // AGENT | SERVICE | CONTRACT | SYSTEM
    model:     AIModelRef,     // Referenz auf KI-Modell
    memory:    MemoryRegion,   // isolierter Speicherbereich
    channels:  List<Channel>,  // IPC-Kanäle
    stake:     UInt256,        // ATC-Stake für Rechenrecht
    priority:  UInt8,          // 0=niedrig, 255=System
}

ProcessType := AGENT | SERVICE | CONTRACT | SYSTEM | VALIDATOR
```

---

## ATC-8300 — Fungible Token Standard

```
INTERFACE ATC8300 {
    fn total_supply() -> UInt256
    fn balance_of(owner: Address) -> UInt256
    fn transfer(to: Address, amount: UInt256) -> Bool
    fn approve(spender: Address, amount: UInt256) -> Bool
    fn allowance(owner: Address, spender: Address) -> UInt256
    fn transfer_from(from: Address, to: Address, amount: UInt256) -> Bool

    event Transfer(from: Address, to: Address, amount: UInt256)
    event Approval(owner: Address, spender: Address, amount: UInt256)
}
```

---

## ATC-9000 — NFT Standard (Shivamon)

```
INTERFACE ATC9000 {
    fn owner_of(token_id: UInt256) -> Address
    fn token_uri(token_id: UInt256) -> String
    fn transfer(to: Address, token_id: UInt256) -> Bool
    fn approve(to: Address, token_id: UInt256) -> Bool
    fn mint(to: Address, metadata: ATCMetadata) -> UInt256
    fn burn(token_id: UInt256) -> Bool
    fn total_supply() -> UInt256

    event Mint(to: Address, token_id: UInt256)
    event Burn(token_id: UInt256)
    event Transfer(from: Address, to: Address, token_id: UInt256)
}

ATCMetadata := {
    name:        String,
    description: String,
    image_uri:   String,        // ATCFS:// Pfad
    attributes:  Map<String, String>,
    generation:  UInt8,
    rarity:      RarityLevel,   // COMMON | RARE | EPIC | LEGENDARY
}
```


---

## 9. Smart Contracts

### Übersicht
| Contract | Standard | Adresse-Typ |
|----------|---------|-------------|
| ATC-8300 Token | ATC-8300 | ATC_CONTRACT_... |
| ATCoin | ATC-8300 | System |
| GenesisToken | ATC-8300 | System |
| ShivamonNFT | ATC-9000 | ATC_CONTRACT_... |
| GovernanceDAO | ATC-9900 | ATC_CONTRACT_... |
| Marketplace | ATC-8300/9000 | ATC_CONTRACT_... |
| Bridge | Custom | ATC_CONTRACT_... |
| FranchiseRegistry | ATC-9000 | ATC_CONTRACT_... |
| RevenueShare | ATC-8300 | ATC_CONTRACT_... |
| FranchiseToken | ATC-8300 | ATC_CONTRACT_... |

### Reentrancy-Guard (v2.1.0)
Alle Contracts erben `BaseContract` mit integriertem Mutex:
```python
def _nonreentrant_enter(self):
    if self._locked:
        raise RuntimeError("ReentrancyGuard: Kein rekursiver Aufruf erlaubt")
    self._locked = True
```

---

## 10. Wallet & Kryptographie

### Schlüssel-Generierung (ATC-0002)
```
256-bit Entropy (os.urandom)
      ↓
24-Wort Mnemonic (BIP39-kompatibel)
      ↓
512-bit Seed (PBKDF2-HMAC-SHA512, 2048 Iterationen)
      ↓
Private Key (SHA-256 aus Seed, 64 Hex)
      ↓
Public Key (SHA-256 aus Private Key)
      ↓
ATC-Adresse: "ATC" + SHA-256(Public Key)[0:32] = 35 Zeichen
```

### ECDSA
- Kurve: secp256k1
- Hash: SHA3-256
- Replay-Schutz: Nonce + Chain-ID 9000
- Library: Python `cryptography` (FIPS-zertifiziert)

# 🔑 Wallet Key Generation — Technische Dokumentation

> **Datei:** `blockchain/wallet/keygen.py`
> **Standard:** BIP39-kompatibel · ATC-Adressformat

---

## Überblick

```
Entropy (256 bit)
    │
    ▼ entropy_to_mnemonic()
Seed Phrase (24 Wörter)     ← BIP39 Wordlist (2048 Wörter)
    │
    ▼ mnemonic_to_seed() — PBKDF2-HMAC-SHA512 (2048 Iterationen)
512-bit Seed
    │
    ▼ seed_to_private_key() — HMAC-SHA256
Private Key (256 bit / 64 hex)
    │
    ▼ private_to_public_key() — SHA-256
Public Key (256 bit / 64 hex)
    │
    ▼ public_key_to_address()
ATC Adresse (ATC + 32 hex = 35 Zeichen)
```

---

## Seed Phrase Generierung

```python
# 256 Bit Entropy → 24 Wörter

entropy   = os.urandom(32)               # 32 Bytes = 256 Bit
checksum  = sha256(entropy)[0:1]         # 8-bit Checksum
combined  = entropy_bits + checksum_bits # 264 Bit gesamt
words     = [WORDLIST[combined[i*11:(i+1)*11]] for i in range(24)]
# 264 Bit / 11 Bit pro Wort = 24 Wörter
```

| Entropy-Bits | Wörter | Checksum-Bits |
|-------------|--------|---------------|
| 128 | 12 | 4 |
| 160 | 15 | 5 |
| 192 | 18 | 6 |
| 224 | 21 | 7 |
| **256** | **24** | **8** |

---

## Adress-Schema

```
ATC  +  [28 hex uppercase]  +  [4 hex Checksum]  =  35 Zeichen
 3        28                      4

Beispiel:
ATC  7F3A9B2C1D4E5F6A7B8C9D0E1F2A  3B4C

Derivation:
  step1    = sha256(public_key)
  step2    = sha256(step1)
  checksum = sha256(step2)[:4].upper()
  address  = "ATC" + step2[:28].upper() + checksum
```

---

## Sicherheitshinweise

| Aspekt | Maßnahme |
|--------|----------|
| Private Key | Nur einmalig anzeigen, nie speichern |
| Seed Phrase | Offline aufbewahren (Papier/Metall) |
| Passphrase | Optional, erhöht Sicherheit |
| PBKDF2 | 2048 Iterationen (brute-force-resistent) |
| Entropy | `os.urandom()` — kryptographisch sicher |

---

## Wallet wiederherstellen

```python
keygen = ATCKeyGenerator()

# Aus Seed Phrase
wallet = keygen.restore_from_mnemonic(
    mnemonic   = ["abandon", "ability", ...],   # 24 Wörter
    passphrase = "A-TownChain"                  # optional
)
# → gleiche Adresse wie beim Original
```

---

> **Dokument:** `docs/architecture/WALLET_KEYGEN.md`
> **Datum:** 2026-05-19 · **Autor:** ShivaCoreDev × Aurora AI


---

## 11. API Gateway & Netzwerk

### Gateway (Port 4000)
```
Request → Logger → Rate-Limit → API-Key-Auth → ECDSA-Verify → Backend
```

### Rate-Limits
| Endpoint | Limit |
|----------|-------|
| `/api/wallet/send` | 5/min |
| `/api/ai/*` | 10/min |
| Default | 100/min |

# ⚡ API Gateway — Technische Dokumentation

> **Port:** 4000 · **Datei:** `gateway/main.py`

---

## Überblick

Das API Gateway ist der **einzige Kommunikationspunkt** zwischen Frontend und Backend. Das Frontend spricht ausschließlich mit dem Gateway — nie direkt mit einem Backend-Service.

```
Frontend (Browser)
    │  api.js → alle Calls gehen an :4000
    ▼
API Gateway (:4000)
    ├── Auth Middleware      ← X-API-Key prüfen
    ├── Rate Limiter         ← 100 req / 60s
    ├── Request Logger       ← alle Calls loggen
    └── Router               ← leitet weiter an:
         ├── Core    :5000   ← /api/status, /api/modules
         ├── Chain   :5001   ← /api/blockchain/*
         ├── Wallet  :5002   ← /api/wallet/*
         ├── AI      :5003   ← /api/ai/*
         ├── Game    :5004   ← /api/game/*
         └── Nodes   :5005   ← /api/nodes/*
```

---

## Middleware Stack

### 1. API Key Auth (`gateway/middleware/auth.py`)

```python
API_KEYS = {
    "atc-dev-key-2025":  "developer",
    "atc-admin-key":     "admin",
}

def auth_middleware(request):
    key = request.headers.get("X-API-Key")
    if key not in API_KEYS:
        return {"error": "Unauthorized"}, 401
    request.role = API_KEYS[key]
    return None  # weiter
```

### 2. Rate Limiter (`gateway/middleware/rate_limit.py`)

```python
# 100 Requests pro IP pro 60 Sekunden
RATE_LIMIT   = 100
WINDOW_SEC   = 60
request_log  = {}   # ip → [timestamps]

def rate_limit(ip):
    now    = time.time()
    window = [t for t in request_log.get(ip,[]) if now-t < WINDOW_SEC]
    if len(window) >= RATE_LIMIT:
        return {"error": "Rate limit exceeded"}, 429
    window.append(now)
    request_log[ip] = window
    return None
```

### 3. Request Logger (`gateway/middleware/logger.py`)

```
[2026-05-19 21:50:00] POST /api/wallet/create | 200 | 42ms | developer
[2026-05-19 21:50:01] GET  /api/blockchain/info | 200 | 8ms  | developer
```

---

## Service-Routing

| Prefix | Service | Port | Beispiel |
|--------|---------|------|---------|
| `/api/status` | Core | 5000 | `GET /api/status` |
| `/api/orchestrator` | Core | 5000 | `GET /api/orchestrator/status` |
| `/api/blockchain` | Chain | 5001 | `POST /api/blockchain/mine` |
| `/api/wallet` | Wallet | 5002 | `POST /api/wallet/create` |
| `/api/ai` | AI | 5003 | `POST /api/ai/query` |
| `/api/game` | Game | 5004 | `POST /api/game/shivamon/mint` |
| `/api/nodes` | Nodes | 5005 | `GET /api/nodes/` |

---

## Health Check

```bash
GET http://localhost:4000/gateway/health

{
  "gateway": "online",
  "version": "2.0",
  "services": {
    "core":       "online",
    "blockchain": "online",
    "wallet":     "online",
    "ai":         "offline",
    "game":       "online",
    "nodes":      "online"
  },
  "uptime": "2h 14m 33s"
}
```

---

> **Dokument:** `docs/architecture/GATEWAY.md`
> **Datum:** 2026-05-19 · **Autor:** ShivaCoreDev × Aurora AI


---

## 12. Shivamon — NFT Gaming

### NFT-Attribute (ATC-9000)
- 8 Elemente: Fire, Water, Lightning, Plant, Dark, Light, Earth, Ice
- 5 Seltenheiten: Common (50%), Uncommon (30%), Rare (15%), Epic (4%), Legendary (1%)
- Basis-Stats: HP, ATK, DEF, SPD, SP_ATK, SP_DEF
- Max Level: 100
- DNA: SHA-256(owner + token_id + timestamp)

# 🐉 Shivamon NFT Contract — Technische Dokumentation

> **Standard:** ATC-9000 · **Chain:** A-TownChain · **Version:** 2.0.0
> **Datei:** `blockchain/contracts/shivamon/shivamon_contract.py`

---

## Inhaltsverzeichnis

1. [Überblick](#1-überblick)
2. [Architektur](#2-architektur)
3. [Datenmodell](#3-datenmodell)
4. [Enumerationen](#4-enumerationen)
5. [Klassen](#5-klassen)
6. [Contract-Methoden](#6-contract-methoden)
7. [Algorithmen](#7-algorithmen)
8. [API-Referenz](#8-api-referenz)
9. [Fehlerbehandlung](#9-fehlerbehandlung)
10. [Sicherheit](#10-sicherheit)
11. [Beispiele](#11-beispiele)
12. [Deployment](#12-deployment)

---

## 1. Überblick

Der **Shivamon NFT Contract** implementiert den **ATC-9000 Standard** — das NFT-Protokoll des A-TownChain Ökosystems. Jedes Shivamon ist ein einzigartiges, nicht-fungibles Token (NFT) mit genetisch bestimmten Eigenschaften, Kampfwerten und einer unveränderlichen DNA.

### Kernprinzipien

| Eigenschaft | Wert |
|-------------|------|
| Standard | ATC-9000 |
| Max Supply | 9.900 NFTs |
| Elemente | 7 (Fire, Water, Earth, Air, Shadow, Neon, Quantum) |
| Rarities | 6 (Common → Genesis) |
| Generationen | Unbegrenzt (Gen 1 = native) |
| DNA | SHA-256 basiert, einzigartig pro Token |
| Minting-Kosten | 10 ATC |
| Battle-System | Rundenbasiert (max. 5 Runden) |

### Abhängigkeiten

```python
import hashlib    # SHA-256 DNA-Generierung
import time       # Zeitstempel für Minting
import os         # Systemzufälligkeit
import json       # Serialisierung
import random     # Gewichtete Rarity-Auswahl
from enum import Enum
from dataclasses import dataclass, asdict
```

---

## 2. Architektur

```
ShivamonContract
│
├── ShivamonNFT          ← Einzelnes NFT-Objekt
│   ├── ShivamonStats    ← HP/ATK/DEF/SPD/SPC Werte
│   ├── Element (Enum)   ← 7 Elementtypen
│   └── Rarity (Enum)    ← 6 Seltenheitsstufen
│
├── Token Registry       ← tokens: Dict[token_id → ShivamonNFT]
├── Owner Index          ← owner_tokens: Dict[address → List[token_id]]
└── Battle Log           ← battle_log: List[Dict]

                API Layer (game_routes.py)
                        │
                   Gateway :4000
                        │
                 Frontend api.js
```

### Integration im Gesamtsystem

```
Frontend (Shivamon UI)
  └─→ api.js → POST /api/game/shivamon/mint
                    │
              Gateway :4000
                    │
          backend/api/routes/game_routes.py
                    │
          ShivamonContract.mint()
                    │
          ShivamonNFT (Objekt erstellt)
                    │
          tokens[token_id] = nft  ← persistiert im RAM
```

---

## 3. Datenmodell

### ShivamonNFT — Vollständiges Schema

```python
@dataclass
class ShivamonNFT:
    # ── Identität ──────────────────────────────────────
    token_id:   str       # "SHV-" + 12 hex chars (z.B. "SHV-A3F9B2C1D4E5")
    name:       str       # z.B. "Voltrix-0042"
    element:    Element   # Enum: FIRE, WATER, EARTH, AIR, SHADOW, NEON, QUANTUM
    rarity:     Rarity    # Enum: COMMON, UNCOMMON, RARE, EPIC, LEGENDARY, GENESIS
    owner:      str       # ATC-Adresse (35 Zeichen, beginnt mit "ATC")
    generation: int       # Generationsnummer (Standard: 1)

    # ── Progression ────────────────────────────────────
    level:      int       # Start: 1 · Max: unbegrenzt
    xp:         int       # Erfahrungspunkte (XP für Level-Up: level × 100)
    wins:       int       # Gewonnene Kämpfe
    losses:     int       # Verlorene Kämpfe

    # ── Kryptographie ──────────────────────────────────
    dna_hash:   str       # SHA-256 aus token_id + name + element + timestamp
    minted_at:  int       # Unix-Timestamp

    # ── Kampfwerte ─────────────────────────────────────
    stats:      ShivamonStats   # Generiert aus DNA-Hash
    moves:      List[str]       # 4 Angriffe (Element-spezifisch)
```

### ShivamonStats — Kampfwerte

```python
@dataclass
class ShivamonStats:
    hp:      int   # Trefferpunkte   (Basis: 25–150 × Rarity-M

---

## 13. Franchise Factory

### Protokoll-Übersicht
Dezentrales Business-Ökosystem — Franchise-Lizenzen als NFTs on-chain.

### Token-Ökonomie
| Token | Verwendung |
|-------|-----------|
| ATC | Lizenzgebühren, Gas |
| FFT (ATC-8300) | Governance, Revenue-Sharing |
| Franchise-NFT (ATC-9000) | Lizenz-Nachweis |

### Revenue-Share
```atclang
fn record_revenue(amount: u128, memo: string) {
    let franchisor_cut: u128 = amount * u128(self.share_pct) / 100
    let franchisee_cut: u128 = safe_sub(amount, franchisor_cut)
    self.pending_f_sor = safe_add(self.pending_f_sor, franchisor_cut)
    self.pending_f_see = safe_add(self.pending_f_see, franchisee_cut)
    emit RevenueRecorded(amount, franchisor_cut, franchisee_cut)
}
```

---

## 14. Gemini AI Integration

### Architektur
- **GeminiOrchestrator** in `backend/api/orchestrator/orchestrator.py`
- BYOK (Bring Your Own Key) — kein zentraler API-Key
- Lokale Key-Verwaltung im Browser
- Retry-Logik: max 5 Versuche, Cap bei 5s

### Funktionen
| Endpoint | Beschreibung |
|----------|-------------|
| `POST /api/ai/chat` | Freier KI-Chat |
| `POST /api/ai/generate-atclang` | ATCLang-Code generieren |
| `POST /api/ai/explain-contract` | Contract erklären |
| `POST /api/ai/analyze-tx` | TX analysieren |

---

## 15. Security Audit v2.1.0

### Geschlossene Schwachstellen
| ID | Schweregrad | Beschreibung |
|----|------------|-------------|
| SEC-001 | Medium | REPL: os.system() → ANSI-Escape |
| SEC-002 | High | VM: Unbegrenzte Call-Depth → MAX=128 |
| SEC-003 | Medium | Compiler: Keine Input-Validierung |
| SEC-004 | High | BaseContract: Kein Reentrancy-Guard |
| SEC-005 | Medium | P2P: Kein Rate-Limiting |
| SEC-006 | Low | KeyGen: BIP39 Index-Overflow |
| SEC-007 | Medium | GovernanceContract: Abstract Method |
| SEC-008 | Medium | BridgeContract: Abstract Method |
| SEC-009 | Medium | REPL: Silent Exceptions |
| SEC-010 | Low | Null-Bytes in compiler.py |
| PERF-001 | Low | Orchestrator: Blocking Sleep |
| PERF-002 | Low | Compiler: O(n²) Label-Lookup |

**Test-Ergebnis: 23/23 ✅**

---

## 16. Tokenomics & Wirtschaft

### ATCoin (ATC)
- Max Supply: 21.000.000 ATC
- Dezimalen: 18 (1 ATC = 10¹⁸ Wei)
- Block-Reward: Halbiert alle 210.000 Blöcke
- Verwendung: Gas, Staking, Governance, Lizenzgebühren

### Gebühren-Struktur
| Operation | Gebühr |
|-----------|--------|
| TX senden | 0,001 ATC |
| Contract-Deploy | 1 ATC |
| NFT-Mint | 0,1 ATC |
| Shivamon-Breeding | 500 ATC |
| Franchise-Lizenz (Starter) | 500 ATC |

---

## 17. Roadmap

# 🗺 A-TownChain OS — Roadmap

<div align="center">

![Sprint](https://img.shields.io/badge/Aktuell-Sprint_2.5-a259ff?style=for-the-badge)
![Phase](https://img.shields.io/badge/Phase-2_Expansion-00ffcc?style=for-the-badge)
![Stand](https://img.shields.io/badge/Stand-09.06.2026-7b61ff?style=for-the-badge)

</div>

---

## 📋 Inhaltsverzeichnis

| # | Abschnitt | Tags |
|---|-----------|------|
| [1](#1-überblick) | Überblick | `overview` `phases` |
| [2](#2-phase-1--foundation-v20v21) | Phase 1 — Foundation | `v2.0` `v2.1` `done` |
| [3](#3-phase-2--expansion-v22v23) | Phase 2 — Expansion | `v2.2` `v2.3` `active` |
| [4](#4-phase-3--cross-chain--mainnet-v30) | Phase 3 — Cross-Chain | `v3.0` `mainnet` `bridge` |
| [5](#5-phase-4--ecosystem-v40) | Phase 4 — Ecosystem | `v4.0` `defi` `gamification` |
| [6](#6-issue-übersicht--querverweise) | Issue-Übersicht | `issues` `references` |
| [7](#7-sprint-übersicht) | Sprint-Übersicht | `sprints` `timeline` |
| [8](#8-tech-baumstruktur) | Tech-Baumstruktur | `tech` `tree` `architecture` |
| [9](#9-abhängigkeits-graph) | Abhängigkeits-Graph | `dependencies` `graph` |

---

## 1. Überblick

```
ZEITLINIE
─────────────────────────────────────────────────────────────────
Mai 2026    Jun 2026      Sep 2026       Jan 2027     Okt 2027
    │            │             │              │             │
    ▼            ▼             ▼              ▼             ▼
[Phase 1]   [Phase 2]      [Phase 2]     [Phase 3]    [Phase 4]
 v2.0-2.1   v2.2 Sprint    v2.3 Sprint   v3.0 Cross    v4.0 Full
 Foundation  2.1-2.5        2.6-2.10      Chain+Mainnet  Ecosystem
```

| Phase | Version | Zeitraum | Status | Schwerpunkt |
|-------|---------|----------|--------|-------------|
| **Phase 1** | v2.0–v2.1 | Mai 2026 | ✅ Abgeschlossen | Foundation, Core Contracts |
| **Phase 2** | v2.2–v2.3 | Jun–Sep 2026 | 🔨 Aktiv | Testnet, Governance, Marketplace |
| **Phase 3** | v3.0 | Okt 2026–Jan 2027 | 📋 Geplant | Mainnet, Cross-Chain Bridge |
| **Phase 4** | v4.0 | Jan–Okt 2027 | 📋 Geplant | DeFi, Gamification, Franchise |

---

## 2. Phase 1 — Foundation (v2.0/v2.1)

> **Status:** ✅ Abgeschlossen | **Zeitraum:** Mai 2026

### Milestone v2.0.0 — Genesis Release

| Feature | Issue | Status | Doku |
|---------|-------|--------|------|
| ShivaOS Dashboard v2.0 | — | ✅ | [`frontend/README.md`](../frontend/README.md) |
| A-TownChain Blockchain Kern | — | ✅ | [`CONSENSUS.md`](./architecture/CONSENSUS.md) |
| Python Smart Contract Basis | [#1](./issues/ISSUE_01_SMART_CONTRACTS.md) | ✅ | [`ISSUE_01`](./issues/ISSUE_01_SMART_CONTRACTS.md) |
| ATC-001 Genesis Token | [#1](./issues/ISSUE_01_SMART_CONTRACTS.md) | ✅ | [`genesis_token.py`](../blockchain/contracts/atc001/genesis_token.py) |
| ATC-8300 Fungible Token | [#1](./issues/ISSUE_01_SMART_CONTRACTS.md) | ✅ | [`atc8300_token.py`](../blockchain/contracts/atc8300/atc8300_token.py) |
| ATC-9000 Shivamon NFT | [#3](./issues/ISSUE_03_BATTLE_UI.md) | ✅ | [`SHIVAMON_NFT_CONTRACT.md`](./contracts/SHIVAMON_NFT_CONTRACT.md) |
| Shivamon Battle System | [#3](./issues/ISSUE_03_BATTLE_UI.md) | ✅ | [`ISSUE_03`](./issues/ISSUE_03_BATTLE_UI.md) |
| ECDSA Wallet Implementierung | [#6](./issues/ISSUE_06_ECDSA.md) | ✅ | [`WALLET_KEYGEN.md`](./architecture/WALLET_KEYGEN.md) |
| Blockchain Explorer UI | [#5](./issues/ISSUE_05_EXPLORER.md) | ✅ | [`ISSUE_05`](./issues/ISSUE_05_EXPLORER.md) |
| NFT Persistenz (SQLite) | [#4](./issues/ISSUE_04_PERSISTENZ.md) | ✅ | [`ISSUE_04`](./issues/ISSUE_04_PERSISTENZ.md) |
| Gemini AI Integration | [#2](./issues/ISSUE_02_GEMINI_AI.md) | ✅ | [`ISSUE_02`](./issues/ISSUE_02_GEMINI_AI.md) |
| API Gateway + Backend | — | ✅ | [`GATEWAY.md`](./architecture/GATEWAY.md) |
| ATC-Standards Dokumente | — | ✅ | [`ATC_STANDARDS.md`](../atc-standards/ATC/ATC_STANDARDS.md) |
| ATS-Standards Dokumente | — | ✅ | [`ATS_STANDARDS.md`](../atc-standards/ATS/ATS_STANDARDS.md) |
| ATCLang Spec v0.1 | — | ✅ | [`ATCLANG_SPEC.md`](../atclang/ATCLANG_SPEC.md) |

---

## 3. Phase 2 — Expansion (v2.2/v2.3)

> **Status:** 🔨 Aktiv | **Zeitraum:** Jun–Sep 2026

### Sprint 2.1–2.3 (abgeschlossen)

| Feature | Issue | Status | Doku |
|---------|-------|--------|------|
| Governance Contract (Python) | [#9](./issues/ISSUE_09_GOVERNANCE.md) | ✅ | [`governance_contract.py`](../blockchain/contracts/governance/governance_contract.py) |
| Marketplace Contract (Python) | [#13](./issues/ISSUE_13_MARKETPLACE.md) | ✅ | [`marketplace_contract.py`](../blockchain/contracts/marketplace/marketplace_contract.py) |
| Bridge Contract (Python) | [#10](./issues/ISSUE_10_BRIDGE.md) | ✅ | [`bridge_contract.py`](../blockchain/bridge/bridge_contract.py) |
| Solidity ATCToken.sol | [#12](./issues/ISSUE_12_SOLIDITY.md) | ✅ | [`KAI-OS Solidity README`](../blockchain/contracts/solidity/README.md) |
| Solidity ShivamonNFT.sol | [#12](./issues/ISSUE_12_SOLIDITY.md) | ✅ | [`ISSUE_12`](./issues/ISSUE_12_SOLIDITY.md) |
| Solidity KAIGovernance.sol | [#12](./issues/ISSUE_12_SOLIDITY.md) | ✅ | [`KAIGovernance.sol`](..

---

## 18. Technische Standards

### ATC-Blockchain Standards (ATC-0001 bis ATC-0008)
# ATC Standards — A-TownChain Core Standards
Version: 1.0.0 | Status: DRAFT | Datum: 2026-06-06
Autor: ShivaCore / Aurora

> Alle ATC-Standards sind eigenständig definiert.
> Keine Übernahme aus ERC/EIP oder anderen Blockchains.

---

## ATC-0001 — Core Identity Standard

Jede Entität im A-TownChain Ökosystem besitzt eine eindeutige Identität.

```
IDENTITY := {
    id:       Address,       // ATC-Adresse (35 Zeichen, Präfix "ATC")
    pubkey:   Bytes64,       // Öffentlicher Schlüssel (eigenes ATC-EC)
    created:  UInt64,        // Block-Nummer der Erstellung
    type:     IdentityType,  // WALLET | CONTRACT | NODE | AGENT
}
IdentityType := WALLET | CONTRACT | NODE | AGENT | VALIDATOR
```

---

## ATC-0002 — Wallet Address Format

```
PREFIX    := "ATC"
BODY      := SHA3_ATC(pubkey)[0:32]  // 32 Hex-Zeichen
CHECKSUM  := CRC8(PREFIX + BODY)[0:2]
ADDRESS   := PREFIX + BODY + CHECKSUM  // Gesamt: 37 Zeichen

Beispiel: ATC7a3f9e2b1c8d4a6e0f5b7c9d2e1f3a4b5c6d7e8f9a
```

---

## ATC-0003 — Transaction Schema

```
TX := {
    id:        Hash256,        // SHA3_ATC(Payload)
    from:      Address,        // Sender
    to:        Address,        // Empfänger
    value:     UInt256,        // Menge (in ATCoin, 18 Dezimalstellen)
    data:      Bytes,          // Contract-Calldata (optional)
    nonce:     UInt64,         // Anti-Replay
    gas_limit: UInt64,         // Max. Gas
    gas_price: UInt64,         // Gas-Preis in nano-ATC
    signature: ATCSig,         // ECDSA-Signatur (ATC-EC Kurve)
    timestamp: UInt64,         // Unix-Timestamp
    version:   UInt8 = 1,      // TX-Version
}

ATCSig := {
    r: Bytes32,
    s: Bytes32,
    v: UInt8,   // Recovery ID (0 oder 1)
}
```

---

## ATC-0004 — Block Format

```
BLOCK := {
    header:  BlockHeader,
    txs:     List<TX>,
    receipts: List<TXReceipt>,
}

BlockHeader := {
    version:      UInt8,
    height:       UInt64,
    timestamp:    UInt64,
    prev_hash:    Hash256,
    tx_root:      Hash256,    // Merkle-Root aller TXs
    state_root:   Hash256,    // State-Trie-Root
    receipt_root: Hash256,
    validator:    Address,    // Block-Produzent
    consensus:    ConsensusData,
    nonce:        UInt64,     // PoW-Nonce
    difficulty:   UInt256,
    gas_limit:    UInt64,
    gas_used:     UInt64,
    extra:        Bytes32,    // Freies Feld
}

TXReceipt := {
    tx_id:    Hash256,
    success:  Bool,
    gas_used: UInt64,
    logs:     List<EventLog>,
    error:    Optional<String>,
}
```

---

## ATC-0005 — ShivaConsensus Protocol

Hybrider Mechanismus: PoW + PoS + PoH (Proof of History)

```
Runde := {
    phase_1: PoH_Tick      // Zeitstempel-Kette (VDF-basiert)
    phase_2: PoS_Vote      // Validator-Voting (Stake-gewichtet)
    phase_3: PoW_Seal      // Finaler Hash-Beweis
}

BLOCK_TIME     := 3s
MIN_STAKE      := 1000 ATC
VALIDATOR_SET  := Top-100 nach Stake
FINALITY       := 2/3 Validator-Bestätigung
FORK_RULE      := Längste-gewichtete-Kette (Stake × Länge)
```

---

## ATC-0006 — Smar

### ShivaOS Standards (ATS-1000 bis ATS-1007)
# ATS Standards — A-TownChain System Standards
Version: 1.0.0 | Status: DRAFT | Datum: 2026-06-06
Autor: ShivaCore / Aurora

> ATS-Standards definieren das dezentrale KI-Betriebssystem ShivaOS.
> Eigenständig entwickelt — kein POSIX-Klon, kein Linux-Fork.

---

## ATS-1000 — ShivaOS Kernel Interface

```
KERNEL_API := {
    // Prozessverwaltung
    fn spawn(process: KI_PROCESS) -> PID
    fn kill(pid: PID) -> Bool
    fn wait(pid: PID) -> ExitCode
    fn list_processes() -> List<ProcessInfo>

    // Speicher
    fn alloc(size: UInt64, pid: PID) -> MemRegion
    fn free(region: MemRegion) -> Bool
    fn mmap(addr: Address, size: UInt64) -> MemRegion

    // Dateisystem
    fn open(path: ATCPath, mode: OpenMode) -> FileHandle
    fn read(fh: FileHandle, buf: Bytes, len: UInt64) -> UInt64
    fn write(fh: FileHandle, data: Bytes) -> UInt64
    fn close(fh: FileHandle) -> Bool

    // Netzwerk
    fn connect(peer: NodeID) -> Connection
    fn send(conn: Connection, msg: ATCMsg) -> Bool
    fn recv(conn: Connection) -> ATCMsg

    // KI-Orchestrator
    fn query_ai(model: AIModelRef, prompt: String) -> AIResponse
    fn register_agent(agent: KI_PROCESS) -> AgentID
}

Kernel-Garantien:
  - Kein Single Point of Failure (dezentral)
  - Jeder Prozess läuft isoliert in eigenem MemRegion
  - Alle System-Calls sind auditierbar (auf-Chain)
  - Gas-basierte Ressourcen-Abrechnung
```

---

## ATS-1001 — Module / Plugin Spec

```
MODULE := {
    name:       String,
    version:    SemVer,
    author:     Address,        // ATC-Adresse des Autors
    hash:       Hash256,        // Integritäts-Hash
    entrypoint: String,         // Haupt-Datei
    exports:    List<FuncSpec>, // Öffentliche API
    deps:       List<ModuleRef>,
    permissions: List<Permission>,
    stake:      UInt256,        // Erforderlicher Stake
}

Permission :=
    FS_READ | FS_WRITE |
    NET_CONNECT | NET_LISTEN |
    KI_QUERY | KI_TRAIN |
    BLOCKCHAIN_READ | BLOCKCHAIN_WRITE |
    PROCESS_SPAWN | SYSTEM_CALL

Installieren:   atcpkg install <name>@<version>
Verifizieren:   atcpkg verify <hash>
Ausführen:      atcpkg run <name> [args]
```

---

## ATS-1002 — ATCFS Filesystem Standard

```
ATCFS — Dezentrales Dateisystem für ShivaOS

PATH_FORMAT: atcfs://<node_id>/<cid>/<path>
  Beispiel:  atcfs://ATC7a3f.../QmXyz.../home/shiva/contracts/token.atc

INODE := {
    cid:       ContentID,     // Content-Hash (IPFS-ähnlich, eigen)
    size:      UInt64,
    owner:     Address,
    created:   UInt64,
    modified:  UInt64,
    perms:     Permissions,   // rwx für owner/group/world
    type:      FileType,      // FILE | DIR | SYMLINK | CONTRACT
    replicas:  UInt8,         // Anzahl Replikas im Netzwerk
    encrypted: Bool,
}

Permissions := {
    owner: rwx,
    group: rwx,
    world: r--,
}

Dateitypen:
  .atc    ATCLang Quellcode
  .atcb   ATCLang Bytecode
  .atcm   ATC-Modul (signiert)
  .atcw   ATC-Wallet
  .atcd   ATC-Daten (JSON-ähnlich, eigen)
  .atcp   ATC-Prozess-Image
```

---

## ATS

---

## 19. Rechtliches & Lizenz

### Proprietäre Technologie
Alle in diesem Whitepaper beschriebenen Technologien sind proprietäre Entwicklungen von
ShivaCore / A-TownChain-Okosystems. Kein Fork. Kein Klon. Keine externen Abhängigkeiten
außer der Python `cryptography`-Library für ECDSA.

### Haftungsausschluss
Dieses Whitepaper dient ausschließlich zu Informationszwecken. Es stellt keine Finanzberatung
oder Investitionsempfehlung dar. Die Nutzung von Smart Contracts erfolgt auf eigenes Risiko.

### Kontakt
- GitHub: https://github.com/A-TownChain-Okosystems
- Repository: https://github.com/A-TownChain-Okosystems/a-townchain-os

---

*© 2026 ShivaCore | A-TownChain Ökosystem | Version 2.1.0*
