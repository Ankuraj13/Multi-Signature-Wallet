# Multi-Signature Wallet

A secure, decentralized multi-signature wallet smart contract built on Ethereum that requires multiple signatures to execute transactions, providing enhanced security for managing funds.

## 🔐 Overview

This Multi-Signature Wallet contract allows multiple owners to collectively control a shared wallet. Transactions require a minimum number of confirmations from the owners before they can be executed, preventing single points of failure and unauthorized transfers.

## ✨ Features

- **Multi-Owner Control**: Support for multiple wallet owners
- **Configurable Threshold**: Set the minimum number of confirmations required
- **Transaction Proposals**: Any owner can propose new transactions
- **Confirmation System**: Owners can confirm or revoke confirmations
- **Automatic Execution**: Transactions execute automatically when threshold is met
- **Event Logging**: Comprehensive event emissions for transparency
- **View Functions**: Easy access to wallet state and transaction history

## 🚀 Getting Started

### Prerequisites

- Solidity ^0.8.19
- Hardhat or Truffle for development
- MetaMask or similar wallet for interaction

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd multisig-wallet
```

2. Install dependencies:
```bash
npm install
```

3. Compile the contract:
```bash
npx hardhat compile
```

### Deployment

Deploy the contract with initial configuration:

```solidity
// Example deployment parameters
address[] memory owners = [
    0x1234..., // Owner 1
    0x5678..., // Owner 2
    0x9ABC...  // Owner 3
];
uint256 requiredConfirmations = 2; // 2 out of 3 signatures required

MultiSigWallet wallet = new MultiSigWallet(owners, requiredConfirmations);
```

## 📖 Usage

### 1. Deposit Funds

Send ETH directly to the contract address:
```solidity
// The contract automatically accepts ETH deposits
```

### 2. Submit a Transaction

Any owner can propose a new transaction:
```solidity
wallet.submitTransaction(
    0x1234...,  // recipient address
    1 ether,    // amount to send
    "0x"        // optional data
);
```

### 3. Confirm a Transaction

Owners must confirm transactions before execution:
```solidity
wallet.confirmTransaction(0); // confirm transaction at index 0
```

### 4. Execute a Transaction

Once enough confirmations are received, execute the transaction:
```solidity
wallet.executeTransaction(0); // execute transaction at index 0
```

### 5. Revoke Confirmation

Owners can revoke their confirmation before execution:
```solidity
wallet.revokeConfirmation(0); // revoke confirmation for transaction 0
```

## 🔧 Contract Functions

### Main Functions

| Function | Description | Access |
|----------|-------------|---------|
| `submitTransaction()` | Propose a new transaction | Owners only |
| `confirmTransaction()` | Confirm a pending transaction | Owners only |
| `executeTransaction()` | Execute a confirmed transaction | Owners only |
| `revokeConfirmation()` | Revoke transaction confirmation | Owners only |

### View Functions

| Function | Description | Returns |
|----------|-------------|---------|
| `getOwners()` | Get all wallet owners | `address[]` |
| `getTransactionCount()` | Get total transaction count | `uint256` |
| `getTransaction()` | Get transaction details | Transaction data |
| `getPendingTransactions()` | Get unexecuted transactions | `uint256[]` |
| `getBalance()` | Get wallet balance | `uint256` |

## 📊 Events

The contract emits the following events:

- `Deposit(address sender, uint256 amount, uint256 balance)`
- `SubmitTransaction(address owner, uint256 txIndex, address to, uint256 value, bytes data)`
- `ConfirmTransaction(address owner, uint256 txIndex)`
- `RevokeConfirmation(address owner, uint256 txIndex)`
- `ExecuteTransaction(address owner, uint256 txIndex)`

## 💡 Use Cases

### Corporate Treasury Management
- **Scenario**: A company with 5 executives managing treasury funds
- **Setup**: 5 owners, 3 confirmations required
- **Benefit**: Prevents unauthorized access while maintaining operational efficiency

### Joint Personal Accounts
- **Scenario**: Married couple managing shared savings
- **Setup**: 2 owners, 2 confirmations required
- **Benefit**: Both parties must agree on all transactions

### DAO Fund Management
- **Scenario**: Decentralized organization managing community funds
- **Setup**: 7 council members, 4 confirmations required
- **Benefit**: Democratic control over fund allocation

### Investment Fund Management
- **Scenario**: Investment partners managing a fund
- **Setup**: 3 partners, 2 confirmations required
- **Benefit**: Consensus-based investment decisions

## 🛡️ Security Features

- **Access Control**: Only designated owners can interact with the wallet
- **Confirmation Threshold**: Configurable minimum confirmations required
- **Execution Prevention**: Transactions cannot be executed without sufficient confirmations
- **Duplicate Protection**: Prevents owners from confirming the same transaction twice
- **Revocation System**: Owners can change their mind before execution

## ⚠️ Security Considerations

1. **Owner Key Management**: Secure storage of private keys is crucial
2. **Owner Compromise**: If threshold number of owners are compromised, funds are at risk
3. **Gas Optimization**: Large owner lists may increase gas costs
4. **Upgrade Path**: Consider implementing upgrade mechanisms for long-term use

## 🧪 Testing

Run the test suite:
```bash
npx hardhat test
```

Example test scenarios:
- Deployment with valid/invalid parameters
- Transaction submission and confirmation
- Execution with sufficient/insufficient confirmations
- Confirmation revocation
- Access control enforcement

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📚 Additional Resources

- [Ethereum Documentation](https://ethereum.org/developers/)
- [Solidity Documentation](https://docs.soliditylang.org/)
- [OpenZeppelin Contracts](https://openzeppelin.com/contracts/)
- [Multi-Signature Wallet Best Practices](https://consensys.github.io/smart-contract-best-practices/)

## 📞 Support

For questions or support, please:
- Open an issue on GitHub
- Contact the development team
- Join our community Discord

---

contracts detail: 0xeb8b1bA5A9B1C668cBa6D964FaC3Dfc7F1bb2bab

![image](https://github.com/user-attachments/assets/39ce74e5-fb36-47e5-82b8-849c86be6936)
