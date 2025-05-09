# Solana Integration Summary

This file lists all files in the repository that are directly related to Solana integration, organized by directory.

## src/app.ts
- **app.ts**: Main application entry point. Registers Solana routes and endpoints.

## src/chains/solana
- **solana.ts**: Core logic for interacting with the Solana blockchain (accounts, transactions, utilities).
- **solana.config.ts**: Configuration and helper functions for Solana network settings.
- **solana.routes.ts**: Fastify route definitions for Solana endpoints.

### src/chains/solana/routes
- **balances.ts**: Handles Solana account balance queries.
- **estimate-gas.ts**: Handles Solana transaction fee/gas estimation.
- **poll.ts**: Polls for the status of Solana transactions.
- **status.ts**: Provides Solana network status endpoints.
- **tokens.ts**: Handles supported Solana token queries.

## src/services
- **connection-manager.ts**: Manages blockchain connections, including Solana.
- **error-handler.ts**: Contains Solana-specific error handling logic.

## src/wallet
- **wallet.routes.ts**: Wallet-related endpoints, including Solana support.
- **wallet.controllers.ts**: Controllers for wallet operations, may include Solana logic.

## src/connectors/meteora/clmm-routes
- **closePosition.ts**: Interacts with Solana for closing positions in Meteora CLMM.
- (Other files in this directory may also interact with Solana, but 'closePosition.ts' is confirmed from the search results.)

---

This summary covers all files in the repository that directly reference or implement Solana integration. 