# Asset and Handle

In the Zentra ecosystem, `Asset` and `Handle` are fundamental concepts designed to provide more intuitive, readable, and secure abstractions compared to traditional blockchain primitives like smart contract addresses.

---

## Asset

An **Asset** is a core, versatile on-chain entity in Zentra. It can represent a wide range of items, such as a brand, a company, a decentralized application, or a token. Think of it as a multi-purpose digital container or identity on the blockchain.

### Key Characteristics of an Asset

*   **Unique Identifier (Tick):** Every Asset is identified by a unique "tick," which serves as its human-readable on-chain address.
    *   **Naming Convention:** An Asset tick must start with an uppercase letter. It can contain uppercase letters (A-Z), digits (0-9), and the underscore character (`_`).
    *   **Examples:** `MY_APP`, `GOLD_RESERVE`, `DEFI_PROTOCOL_V2`.

*   **Asset as a Container:** An Asset can own other Assets. This allows for the creation of complex and meaningful on-chain relationships. For example, an Asset representing a company (`THE_ACME_CORP`) could own other Assets representing its liquid cash (`USD_CASH`) and its equity in another project (`INVESTMENT_IN_XYZ`).

*   **Decoupled from Tokens:** The creation of an Asset does not automatically mean a token is created. An Asset is an identity and a container first. It can be programmed to behave as a token (fungible or non-fungible) by associating it with specific **Functions**, but it does not have to be.

*   **Controlled Interaction via Functions:** An Asset's behavior is defined by the **Functions** it is associated with. When an Asset is created, its owner explicitly chooses which Functions are permitted to operate on it. This opt-in mechanism enhances security by ensuring that only audited and approved code can modify the Asset's state, moving away from a model where any contract can interact with another by default.

*   **Readable Address:** In practice, an Asset serves as a human-readable and programmable replacement for the cryptic hexadecimal addresses used for smart contracts on other blockchains.

---

## Handle

A **Handle** is a human-readable alias for an Externally Owned Account (EOA), which is controlled by a user's private key. It makes user accounts recognizable and easier to interact with.

### Key Characteristics of a Handle

*   **EOA Control:** A Handle is directly controlled by an EOA. Any action performed by the Handle must be authorized and signed by the EOA's corresponding private key.

*   **Ownership Capability:** Both raw EOA addresses and Handles can own Assets. This means you can send an Asset directly to a Handle like `alice` instead of a long, error-prone address, making transactions safer and more user-friendly.

*   **Naming Convention:** A Handle must consist of lowercase letters (a-z), digits (0-9), and the underscore character (`_`).
    *   **Examples:** `alice`, `trader_joe`, `wallet_123`.


