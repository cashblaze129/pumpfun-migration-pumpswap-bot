# PumpSwap Migration Bot

A high-performance Solana trading bot that executes seamless atomic transactions combining Pump.fun final purchases, automatic migration triggers, and PumpSwap first-buy operations. Built for traders who need reliable, fast execution when tokens transition from the Pump.fun bonding curve to decentralized AMM pools.

## 📩 Contact Me on Telegram

For inquiries, collaborations, or support, feel free to reach out:

[![Telegram Contact](https://img.shields.io/badge/Telegram-Contact%20Me-blue?logo=telegram&style=for-the-badge)](https://t.me/cashblaze129)

## Transaction Flow

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Pump.fun      │    │    Migration     │    │   PumpSwap      │
│   Final Buy     │───▶│    Trigger       │───▶│   First Buy     │
└─────────────────┘    └──────────────────┘    └─────────────────┘
         │                       │                       │
         └───────────────────────┼───────────────────────┘
                Single Atomic Transaction
```

## Related Link & Screenshot
- https://solscan.io/tx/2JDAAvyPnxVKKrn9HTXH6yJVwANMQivFFFZqsiMkSBYAop7qsUXgg29SFP4NzjmbRBmhzV4hiPGapZuUnmnEFqMa
![Screenshot_2](https://github.com/user-attachments/assets/485e67b1-8922-42f3-9135-7c81e9076178)


## What It Does

This bot solves a critical timing challenge in Solana token trading. When a token on Pump.fun reaches its bonding curve completion, there's a brief window where you need to:

1. **Execute the final buy** on Pump.fun to complete the bonding curve
2. **Trigger the migration** from Pump.fun to PumpSwap AMM
3. **Place the first buy** on the newly created PumpSwap pool

All of this happens in a **single atomic transaction** - ensuring you don't miss opportunities due to network delays or manual execution errors.

## Key Features

- **Atomic Transaction Execution**: All operations bundled into one transaction for guaranteed execution order
- **Intelligent Slippage Protection**: Configurable slippage controls with automatic quote calculations
- **Jito Bundle Integration**: Uses Jito for MEV protection and faster transaction processing
- **Real-time Pool Monitoring**: Tracks Pump.fun reserves and automatically detects migration opportunities
- **Security-First Design**: Built-in wallet encryption and secure private key handling
- **Comprehensive Logging**: Detailed transaction logs and error tracking with Winston
- **Fee Optimization**: Smart fee calculation to maximize profit margins

## Technical Architecture

Built with TypeScript and leveraging:
- **@solana/web3.js** for blockchain interactions
- **@pump-fun/pump-sdk** for Pump.fun integration
- **Jito bundles** for MEV protection
- **SPL Token** libraries for token account management
- **Express.js** for API endpoints (if needed)

## Prerequisites

- Node.js 20.18.0 
- A funded Solana wallet
- Basic understanding of Solana token mechanics

## Installation

1. Clone the repository:
```bash
git clone https://github.com/cashblaze127/pumpfun-migration-pumpswap.git
cd pumpfun-migration-pumpswap
```

2. Install dependencies:
```bash
npm install
```

3. Configure your environment:
```bash
cp .env.example .env
# Edit .env with your wallet private key and configuration
```

## Configuration

Edit the test configuration in `src/service/test.ts`:

```typescript
const mintAddress = "YOUR_TOKEN_MINT_ADDRESS";
const min_migration_buy_test_fee = 20;  // Minimum SOL for migration
const pumpswapBuy = 1000;               // Tokens to buy on PumpSwap
const slippage = 30;                    // Slippage tolerance (%)
```

## Usage

### Testing Mode
Run a test migration with your configured parameters:
```bash
npm run dev
```

### Production Mode
Build and run:
```bash
npm run build
npm start
```

## How It Works

1. **Pool Analysis**: Monitors Pump.fun pool reserves for your target token
2. **Migration Check**: Determines if the token is ready for bonding curve completion
3. **Quote Calculation**: Calculates optimal amounts with slippage protection
4. **Transaction Building**: Constructs atomic transaction with:
   - Pump.fun final buy instruction
   - Migration trigger instruction  
   - PumpSwap first buy instruction
5. **Jito Execution**: Submits bundle through Jito for MEV protection

## Safety Features

- **Slippage Protection**: Automatic price impact calculations
- **Reserve Validation**: Ensures sufficient liquidity before execution  
- **Fee Limits**: Configurable maximum fees to prevent overpaying
- **Error Handling**: Comprehensive error catching and logging
- **Account Checks**: Validates token accounts before transaction submission

## Monitoring & Logging

The bot includes comprehensive logging for:
- Transaction signatures and Solscan links
- Pool reserve monitoring
- Fee calculations and slippage adjustments
- Error tracking and debugging information

## Risk Disclaimer

This software is for educational purposes. Trading cryptocurrencies involves substantial risk of loss. Always:
- Test thoroughly on devnet first
- Start with small amounts
- Understand the risks involved
- Never invest more than you can afford to lose

## Contributing

We welcome contributions! Please:
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

MIT License - see LICENSE file for details

## Support

For issues or questions:
- Open a GitHub issue
- Check the logs directory for debugging information
- Review the configuration parameters

---

**Note**: This bot requires active monitoring and is not financial advice. Always do your own research and understand the risks involved in automated trading.
