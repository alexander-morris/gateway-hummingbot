# Koii Network Integration Scope

This document outlines the scope of modifications needed to integrate Koii Network support into the gateway, including a new fork called 'Tancho' with Raydium compatibility.

## 1. Configuration Changes

### 1.1 New Configuration Files
- Create `conf/koii.yaml` with network configurations:
  ```yaml
  koii:
    networks:
      mainnet:
        nodeURL: "https://api.koii.network"
        tokenListType: "FILE"
        tokenListSource: "conf/tokens/koii-tokens.json"
        nativeCurrencySymbol: "KOII"
      testnet:
        nodeURL: "https://testnet-api.koii.network"
        tokenListType: "FILE"
        tokenListSource: "conf/tokens/koii-testnet-tokens.json"
        nativeCurrencySymbol: "tKOII"
    defaultComputeUnits: 200000
    basePriorityFeePct: 0
    priorityFeeMultiplier: 1
    maxPriorityFee: 1000000
    minPriorityFee: 0
    retryIntervalMs: 1000
    retryCount: 3
  ```

### 1.2 Tancho Fork Configuration
- Add Tancho-specific configuration in `conf/koii.yaml`:
  ```yaml
  koii:
    networks:
      tancho:
        nodeURL: "https://tancho.koii.network"
        tokenListType: "FILE"
        tokenListSource: "conf/tokens/tancho-tokens.json"
        nativeCurrencySymbol: "TANCHO"
        raydiumProgramId: "<new-raydium-program-id>"
  ```

## 2. New Classes and Files

### 2.1 Core Classes
- Create `src/chains/koii/koii.ts`:
  - Extend base chain functionality
  - Implement Koii-specific transaction handling
  - Add Tancho fork support

- Create `src/chains/koii/koii.config.ts`:
  - Configuration management for Koii networks
  - Network-specific settings

- Create `src/chains/koii/koii.routes.ts`:
  - API endpoints for Koii operations
  - Tancho-specific endpoints

### 2.2 Tancho Integration
- Create `src/chains/koii/tancho/`:
  - `tancho.ts`: Tancho-specific implementation
  - `raydium.ts`: Raydium fork implementation
  - `routes/`: API endpoints for Tancho operations

### 2.3 Raydium Fork
- Create `src/chains/koii/tancho/raydium/`:
  - Copy and modify relevant Raydium code
  - Update program IDs and addresses
  - Implement Tancho-specific modifications

## 3. Testing

### 3.1 Unit Tests
- Create `test/chains/koii/`:
  - `koii.test.ts`: Basic Koii functionality
  - `tancho.test.ts`: Tancho fork functionality
  - `raydium.test.ts`: Raydium fork operations

### 3.2 Integration Tests
- Create `test/integration/koii/`:
  - Network connection tests
  - Transaction flow tests
  - Raydium operation tests

### 3.3 Configuration Tests
- Create `test/config/koii/`:
  - Configuration loading tests
  - Network validation tests

## 4. Documentation

### 4.1 API Documentation
- Update API documentation with Koii endpoints
- Document Tancho-specific features
- Add Raydium fork documentation

### 4.2 Configuration Guide
- Create configuration guide for Koii networks
- Document Tancho setup process
- Add Raydium fork configuration guide

## 5. Implementation Phases

### Phase 1: Basic Koii Integration
- Implement core Koii classes
- Add basic configuration
- Set up testing framework

### Phase 2: Tancho Fork
- Implement Tancho-specific code
- Add Tancho configuration
- Create Tancho tests

### Phase 3: Raydium Fork
- Port Raydium code to Tancho
- Update program IDs
- Test Raydium operations

### Phase 4: Testing and Documentation
- Complete test coverage
- Update documentation
- Performance testing

## 6. Dependencies

### 6.1 New Dependencies
- Koii SDK
- Tancho-specific libraries
- Updated Raydium dependencies

### 6.2 Configuration Dependencies
- Token list files
- Network configuration files
- Program ID mappings

## 7. Security Considerations

### 7.1 Network Security
- RPC endpoint security
- Transaction signing security
- Program ID verification

### 7.2 Configuration Security
- Secure storage of program IDs
- Network configuration validation
- Token list validation

## 8. Monitoring and Maintenance

### 8.1 Monitoring
- Network status monitoring
- Transaction monitoring
- Error tracking

### 8.2 Maintenance
- Configuration updates
- Program ID updates
- Token list updates 