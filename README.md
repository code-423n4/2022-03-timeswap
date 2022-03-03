# ✨ So you want to sponsor a contest

This `README.md` contains a set of checklists for our contest collaboration.

Your contest will use two repos: 
- **a _contest_ repo** (this one), which is used for scoping your contest and for providing information to contestants (wardens)
- **a _findings_ repo**, where issues are submitted. 

Ultimately, when we launch the contest, this contest repo will be made public and will contain the smart contracts to be reviewed and all the information needed for contest participants. The findings repo will be made public after the contest is over and your team has mitigated the identified issues.

Some of the checklists in this doc are for **C4 (🐺)** and some of them are for **you as the contest sponsor (⭐️)**.

---

# Contest setup

## ⭐️ Sponsor: Provide contest details

Under "SPONSORS ADD INFO HERE" heading below, include the following:

- [x] Name of each contract and:
  - [x] source lines of code (excluding blank lines and comments) in each
  - [x] external contracts called in each
  - [x] libraries used in each
- [x] Describe any novel or unique curve logic or mathematical models implemented in the contracts
- [x] Does the token conform to the ERC-20 standard? In what specific ways does it differ?
- [x] Describe anything else that adds any special logic that makes your approach unique
- [ ] Identify any areas of specific concern in reviewing the code
- [x] Add all of the code to this repo that you want reviewed
- [ ] Create a PR to this repo with the above changes.

---

# Timeswap contest details
- $28,500 USDC main award pot
- $1,500 USDC gas optimization award pot
- Join [C4 Discord](https://discord.gg/code4rena) to register
- Submit findings [using the C4 form](https://code4rena.com/contests/2022-03-timeswap-contest/submit)
- [Read our guidelines for more details](https://docs.code4rena.com/roles/wardens)
- Starts March 4, 2022 00:00 UTC
- Ends March 6, 2022 23:59 UTC

This repo will be made public before the start of the contest. (C4 delete this line when made public)

## Contracts

| Name | LOC | External Contracts Called | Libraries |
| :--- | :---: | :---: | :---: |
| Timeswap-V1-Core/TimeswapPair.sol | 523 | 2 | 11 |
| Timeswap-V1-Core/TimeswapFactory.sol | 76 | 1 | 0 |
| Timeswap-V1-Convenience/TimeswapConvenience.sol | 625 | 0 | 8 |
| Timeswap-V1-Convenience/Liquidity.sol | 63 | 0 | 2 |
| Timeswap-V1-Convenience/BondPrincipal.sol | 72 | 0 | 2 |
| Timeswap-V1-Convenience/BondInterest.sol | 72 | 0 | 2 |
| Timeswap-V1-Convenience/InsurancePrincipal.sol | 72 | 0 | 2 |
| Timeswap-V1-Convenience/InsuranceInterest .sol | 72 | 0 | 2 |
| Timeswap-V1-Convenience/CollateralizedDebt.sol | 79 | 0 | 3 |

## Describe any novel or unique curve logic or mathematical models implemented in the contracts

The protocol does not use an oracle for collateral factor calculation. Instead, it utilizes a `xyz=k` constant product algorithm to discover both interest rate and collateral factor. x and y determines interest rate, while x and z determines collateral factor. Whenever the ratio of x, y, and z are not up to market rate, then it means it is a favorable price for a lender or borrower.

## Does the token conform to the ERC-20 standard? In what specific ways does it differ?

The following token contracts in the Convenience Repository follow the token standard:
- BondPrincipal ERC20, 
- BondInterest ERC20,
- InsurancePrincipal ERC20, 
- InsuranceInterest ERC20, 
- Liquidity ERC20, and 
- Collateralized Debt ERC721

The key difference they have is that they don’t store total supply in the contract, instead the respective claims (bond tokens and insurance tokens), dues, and liquidity balanceOf of those ERC20 and ERC721 contracts are the total supply.

[Timeswap Whitepaper](https://github.com/code-423n4/2022-03-timeswap/files/8180278/Timeswap.Whitepaper.pdf)

[Timeswap V1 Core Product Specification](https://drive.google.com/file/d/1SQ_Hbv_wQVXEcFlDytAFMA03Rbi5dTLu/view?usp=sharing)

[Timeswap V1 Convenience Product Specification](https://drive.google.com/file/d/1fRgY1PABhmEA34BfxxoqM73dsXkHwSCu/view?usp=sharing)

[Timeswap Gitbook Documentation](https://timeswap.gitbook.io/timeswap/)

[Code Walkthrough](https://youtu.be/AEizNC_u_yQ)

