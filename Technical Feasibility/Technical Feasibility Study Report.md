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
   - **Frontend & API Synergy**: A TypeScript-based backend can more easily communicate with front-end dashboards or REST APIs in future milestones.

---

## 3. CIP-721 Implementation

1. **Metadata Structure**  
   - Adheres to the CIP-721 standard to store custom fields for **biochar feedstock**, **reactor performance**, **emissions data**, and **utility usage**.  
   - Key fields include batch ID, start/end timestamps, and environmental metrics (e.g., CO2eq, NOx, water use).  
   - Large data fields can be offloaded to IPFS if necessary to keep **on-chain transaction sizes** manageable.

2. **Asset Naming & Policy IDs**  
   - We generate **unique asset names** by hex-encoding each batch ID and optionally prepending category prefixes (e.g., `000643b0`).  
   - This ensures we avoid naming collisions and maintain a consistent taxonomy for different tokens (e.g., raw feedstock vs. processed biochar).

3. **Minting Process**  
   - Our prototype uses **cardanocli-js** to build and sign transactions, attach CIP-721 metadata, and submit minted NFTs to the testnet.  
   - Initial tests confirm that minted NFTs contain all required fields and pass CIP-721 validation checks.

**Supporting Evidence**  
- **Private Git Commits**: Demonstrations of CIP-721 metadata schemas and initial minting transactions are available in a private repository (for now).  
- **Metadata Examples**: A JSON file illustrating the CIP-721 structure for a biochar batch is included in our feasibility study documentation.

---

## 4. Plutus Datum Integration

1. **Cross-Referencing Batch IDs**  
   - Each minted NFT includes a `batchId` in its metadata; the corresponding **Plutus datum** references the same ID to connect on-chain logic with specific batches.  
   - Potential use cases include **validating carbon credits**, automating reward distribution, or **verifying emission thresholds** at the point of NFT transfer.

2. **Script Design**  
   - The datum structure (implemented in TypeScript) captures essential metrics like CO2eq, NOx, PM, and measurement timestamps.  
   - **Plutus Scripts** can be extended to ensure certain conditions (e.g., net emissions below a threshold) are met before tokens move or evolve.

3. **Testnet Trials**  
   - Basic tests confirm that minted NFT data aligns with the on-chain datum.  
   - We have successfully run scripts that read the datum in real-time, ensuring consistent references.

---

## 5. Security & Privacy

1. **Security Audits**  
   - Ongoing reviews of the smart contract code aim to mitigate risks like **improper datum handling**, **transaction-size exploits**, or **unintended token duplication**.  
   - After internal testing, external auditors will be invited to review the final solution before open-sourcing it.

2. **Data Privacy & Off-Chain Storage**  
   - Sensitive farm data can be **hashed** or partially stored off-chain (e.g., IPFS) to minimize on-chain exposure and manage costs.  
   - This approach balances **transparency** (public proof of carbon credits) with **landowner confidentiality**.

3. **Open-Source Transition**  
   - We plan to release the **TypeScript/Plutus code** in a publicly available repository once security measures are thoroughly tested.  
   - In the meantime, interested parties may request a **private video walkthrough** or review curated commit logs to validate ongoing progress.

---

## 6. Next Steps for Technical Development

1. **Pilot Implementation**  
   - Collaborate with volunteer landowners (e.g., Jeffrey W. and Paul A.) to capture real-world batch data and refine CIP-721 metadata.  
   - Gather feedback on user interface feasibility and transaction costs.

2. **Automation & UI Integration**  
   - Develop a **dashboard** at [app.malamaproject.org](https://app.malamaproject.org) for landowners to upload data directly from mobile devices.  
   - Integrate a **one-click minting flow** that streamlines CIP-721 NFT creation.

3. **Comprehensive Testing**  
   - Subject the system to **stress tests** for high-volume metadata inputs, ensuring fees and latency remain manageable.  
   - Conduct thorough **Plutus script audits** to prevent double spending, unauthorized modifications, or other unexpected token behaviors.

---

## 7. Conclusion

The MALAMA Project’s technical architecture is **feasible** for securely recording carbon-sequestering data on the Cardano blockchain. By combining **CIP-721** NFT metadata standards with **Plutus datum** cross-references, we establish a foundation for **transparent**, **immutable** biochar production tracking and future expansions—such as advanced yield or carbon-credit trading mechanisms.

- **Key Benefits**:  
  - On-chain trust and verifiability for agricultural carbon credits.  
  - Adaptability to incorporate aggregator dashboards and yield analytics.  
  - Seamless integration between user-friendly front-end tools and robust blockchain logic.

Our **TypeScript** approach ensures maintainability, and pending **security enhancements** will pave the way for an eventual open-source release, welcoming collaboration from the Cardano and global sustainability communities.

---

## 8. References & Supporting Evidence

- **Private Repository**: (Temporary) Contains TypeScript/Plutus code, minting scripts, and CIP-721 schema definitions (contact us for a video walkthrough or partial commit logs).  
- **Testnet Transactions**: Detailed logs of our initial CIP-721 mints and data references verifying batch IDs and Plutus datum alignment.  
- **Website**: [https://www.malamaproject.org](https://www.malamaproject.org) for an overview of the MALAMA Project’s user-facing materials.

For questions or to schedule a **video review** of our private GitHub repository, please contact us at [info@malamaproject.org](mailto:info@malamaproject.org).

---

**Submitted by:**  
*MALAMA Project Team*  
**Date:** February 2025  

This concludes the **Technical Feasibility Study Report**, highlighting our CIP-721 tokenization foundation and Plutus-based on-chain logic. Future milestones will feature expanded testing, pilot deployments, and our transition to a fully open-source codebase.
