# TimeCapsule# TimeCapsule — On-chain Time-Locked Messages

## Problem
People need a trust-minimized way to seal messages until a specific future date without leaking content early.

## Solution
Store only the keccak256 hash + unlockTime on-chain. Before unlock, reveal is impossible. After unlock, the contract verifies the hash and discloses via event—plaintext is never stored in storage.

## How it works
1. Frontend computes keccak256(utf8(message)).
2. Call createCapsule(hash, unlockTime).
3. After time elapses, call reveal(id, plaintext) → hash check → CapsuleRevealed event.
4. UI listens to the event and displays the plaintext.

## Features
- Time lock by timestamp
- Privacy by design (hash-only storage)
- Minimal API: create + reveal
- Event-based disclosure
- Optional: encrypted IPFS/Arweave backup

## Tech Stack
- Solidity (EVM)  
- Base Sepolia testnet  
- Ethers.js frontend  
- (Optional) Account Abstraction / 4337 Paymaster  

## Use Cases
- Embargoed announcements or giveaways  
- Personal notes & celebrations  
- Community time capsules  
- Fair reveal of contest answers  

## Roadmap
- v1: Concept & pitch video  
- v2: Prototype on Base Sepolia  
- v3: Full dApp with gasless UX

## License
MIT
