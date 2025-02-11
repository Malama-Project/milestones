---
title: "Technical Feasibility Study Report"
date: "February 2025"
---

# Technical Feasibility Study Report

**Project:** MALAMA Project  
**Date:** February 2025  

---

## 1. Introduction

This report outlines the **technical feasibility** of the MALAMA Project’s approach to recording carbon-sequestering activities on the Cardano blockchain. It covers the design of our **CIP-721 NFT** implementation, the integration of **Plutus datum** for on-chain logic, and ongoing **security and privacy** measures. 

We also address the current state of our **open-source** efforts and highlight next steps for a secure, public release of our codebase.

---

## 2. Technical Approach

1. **Objective**  
   - Provide **immutable, on-chain records** of biochar production and related carbon-sequestering activities.  
   - Use a **TypeScript/Node.js** environment for streamlined development, testing, and future scalability.

2. **Scope**  
   - Build a tokenization mechanism using **CIP-721** metadata, which encapsulates feedstock data, emissions, utility usage, and other batch-specific details.  
   - Reference the same batch IDs in **Plutus datum** to enable script-based validations and advanced features (e.g., automatic carbon credit issuance).

3. **Rationale for TypeScript**  
   - **Strong Typing & Modular Structure**: Eases collaborative development.  
   - **Integration with cardanocli-js**: Minimizes reliance on raw Bash scripts while maintaining access to essential Cardano CLI functions.  
   - **Frontend & API Synergy**: TypeScript-based backend can more easily communicate with future front-end dashboards or REST APIs.

---

## 3. CIP-721 Implementation

1. **Metadata Structure**  
   - Adheres to the CIP-721 standard to store custom fields for **biochar feedstock**, **reactor performance**, **emissions data**, and **utility usage**.  
   - Key fields include batch ID, start/end timestamps, and environmental metrics (e.g., CO2eq, NOx, water use).  
   - Large data fields can be offloaded to IPFS if necessary to keep **on-chain transaction sizes** manageable.

2. **Asset Naming & Policy IDs**  
   - We generate **unique asset names** by hex-encoding each batch ID and optionally prepending category prefixes (e.g., `000643b0`).  
   - This ensures we avoid naming collisions and maintain a consistent taxonomy for different kinds of tokens (e.g., raw feedstock vs. processed biochar).

3. **Minting Process**  
   - Our prototype uses **cardanocli-js** to build and sign transactions, attach CIP-721 metadata, and submit minted NFTs to testnet.  
   - Initial tests confirm that minted NFTs contain all required fields and pass CIP-721 validation checks.

**Supporting Evidence**  
- *Private Git Commits*: Demonstrations of CIP-721 metadata schemas and initial minting transactions are available in our **private repository**.  
- *Metadata Examples*: A JSON file illustrating the CIP-721 structure for a biochar batch is included as part of our feasibility study documentation.

---

## 4. Plutus Datum Integration

1. **Cross-Referencing Batch IDs**  
   - Each minted NFT includes a `batchId` in its metadata; the corresponding **Plutus datum** references the same ID to connect on-chain logic with specific batches.  
   - Potential use cases include **validating carbon credits**, automating reward distribution, or **verifying emission thresholds** at the point of NFT transfer.

2. **Script Design**  
   - The datum structure (written in TypeScript) captures essential metrics like CO2eq, NOx, PM, and the timestamp of measurement.  
   - **Plutus Scripts** can be extended to enforce that certain conditions (e.g., net emissions below a threshold) are met before tokens move or evolve.

3. **Testnet Trials**  
   - Basic tests ensure that the minted NFT’s data aligns with the on-chain datum.  
   - We have successfully run scripts that read the datum in real-time, confirming consistent references.

---

## 5. Security & Privacy

1. **Security Audits**  
   - Ongoing reviews of the smart contract code aim to mitigate risks like **improper datum handling**, **transaction size exploits**, or **unintended token duplication**.  
   - Once internal testing is complete, we will invite external auditors to review the final solution before fully open-sourcing it.

2. **Data Privacy & Off-Chain Storage**  
   - Sensitive farm data can be **hashed** or partially stored off-chain (e.g., IPFS) to minimize exposure and manage cost.  
   - Our approach balances **transparency** (public proof of carbon credits) with **landowner confidentiality**.

3. **Open-Source Transition**  
   - We plan to release the **TypeScript/Plutus code** in a publicly available repository once the security measures are thoroughly tested.  
   - In the meantime, interested parties may request a **private video walkthrough** or view printouts of commit logs to validate our ongoing progress.

---

## 6. Next Steps for Technical Development

1. **Pilot Implementation**  
   - Collaborate with volunteer landowners (Jeffrey W., Paul A., etc.) to record real-world batch data and further refine CIP-721 metadata.  
   - Collect feedback on the user interface and transaction cost implications for daily data uploads.

2. **Automation & UI Integration**  
   - Build a **dashboard** at [app.malamaproject.org](https://app.malamaproject.org) for landowners to upload data directly from mobile devices.  
   - Integrate a **one-click minting flow** that simplifies the process of generating CIP-721 tokens.

3. **Comprehensive Testing**  
   - Subject the system to **stress tests** for high volumes of metadata, ensuring fees remain manageable and that partial off-chain storage solutions work smoothly.  
   - Conduct thorough **Plutus script audits** to confirm that unintended token behavior is impossible (e.g., double-spending or unauthorized modifications).

---

## 7. Conclusion

The MALAMA Project’s technical architecture is **feasible** for securely recording carbon-sequestering data on the Cardano blockchain. By combining **CIP-721** NFT metadata standards with **Plutus datum** cross-references, we create a foundation for **transparent**, **immutable** tracking of biochar production and other sustainability metrics.

- **Key Benefits**:  
  - On-chain trust and verifiability for agricultural carbon credits.  
  - Adaptability for future expansions (e.g., aggregator dashboards, advanced yield or carbon-trading mechanisms).  
  - Strong synergy between user-facing tools (website, data dashboard) and blockchain logic.

Our **TypeScript** approach ensures maintainability, and pending **security enhancements** will pave the way for an open-source release that welcomes collaboration from the Cardano and global sustainability communities.

---

## 8. References & Supporting Evidence

- **Private Repository**: Contains the **TypeScript/Plutus** code, minting scripts, and all CIP-721 schema definitions (available for **private demonstrations** upon request).  
- **Metadata Examples**: JSON files for typical biochar batch tokens, showing real-world usage of CIP-721 fields.  
- **Testnet Transactions**: Logs of initial mints and data references verifying batch IDs and Plutus datum alignment.  
- **Website**: [https://www.malamaproject.org](https://www.malamaproject.org) for a general overview of our project and educational materials.

For questions, or to schedule a **video review** of our private GitHub repository, please contact us at [info@malamaproject.org](mailto:info@malamaproject.org).

---

**Submitted by:**  
*MALAMA Project Team*  
**Date:** February 2025  

This concludes the **Technical Feasibility Study Report**, showcasing our foundational work in CIP-721 tokenization and on-chain logic via Plutus. Future milestones will address expanded testing, pilot deployments, and an open-source release designed to foster broader community engagement.
