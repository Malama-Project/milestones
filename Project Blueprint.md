# **Malama Project Milestone 1: Detailed Project Blueprint**

## **1. System Architecture Overview**

The Malama Project integrates four core components, each responsible for different functions to achieve seamless carbon sequestration efforts and tokenization. Detailed explanation of each part of the architecture.

### **1.1 KINA Stake Pool Relay Nodes(Either of 3 For Redundancy)**

The KINA Stake Pool Relay Node is the backbone of the Cardano-based blockchain interactions. It performs:

- **Wallet Creation:** Automatically generates user wallets for tracking sequestration credits.
- **Transaction Execution:** Processes all transactions related to carbon credits.
- **Minting:** Facilitates the minting of NFTs representing carbon credits based on farmers' efforts.

### **1.2 MongoDB for Off-Chain Storage**

MongoDB serves as our **off-chain database** to manage user data, sequestration efforts, and carbon credit information before the data is minted on the blockchain. MongoDB is utilized to:

- **Asset Management:** Temporarily store the details of sequestration efforts (e.g., images, location, biochar data) until approved for on-chain minting.
- **User Profiles:** Store user information, allowing easy access to history and real-time updates.
- **Stores live sensor data from soil (if available). 
- **Uses stored sensor data to create data points for soil(if Available). 
### **1.3 React/TypeScript Frontend**

The **React/TypeScript-based frontend** is designed to allow seamless user interaction, providing a simple interface for landowners to register and manage their sequestration efforts. It includes:
 
- **User Dashboard:** Displays farmer progress and sequestration methods.
- **Interactive Map:** Allows farmers to select their land and track sequestration activities on a geospatial interface.
- **Submission Portal:** Easy submission of biochar and IMO efforts for approval and tokenization.
- **On-Chain Asset Viewer:** Displays user's wallet with minted sensor readings and sequestration efforts. 
### **1.4 Fastify Server**

The **Fastify server** acts as a middleware, ensuring the communication between the front-end interface, MongoDB, and the stake pool. Its role includes:

- **API Endpoints:** Manages all incoming requests from the frontend (wallet creation, submission of sequestration efforts, etc.)
- **Data Transmission:** Sends and retrieves data to/from MongoDB and manages on-chain transactions through the KINA Stake Pool.

---

## **2. System Architecture Diagram**

We’ve created a detailed architecture diagram to visually represent how each component interacts with one another. This includes:

- **Front-End (React)** → **API (Fastify)** → **Database (MongoDB)** → **Blockchain (kINA Relay Node)**

### **Diagram Link:**
https://miro.com/app/board/uXjVLTv6Crs=/?share_link_id=932311592987

---

## **3. Data Processing Workflow**

### **3.1 Sequestration Data Collection**

When a farmer initiates a sequestration effort (e.g., biochar or IMO application), the data is collected and stored off-chain in MongoDB before being verified. The workflow includes:

- **Data Input:** Farmers provide evidence (e.g., pictures, location data) of the biochar application or IMO creation.
- **Temporary Storage:** MongoDB stores the effort details, including timestamp, land coordinates, and user ID.
- **Validation Queue:** Once submitted, the effort is queued for review by the board for on-chain validation.

### **3.2 Sequestration Effort Approval and Token Minting**

Once a farmer’s efforts have been approved, the process to mint carbon credit tokens (NFTs) begins:

1. **Validation by Board:** Location data, biochar tests, and other evidence are reviewed.
2. **Token Creation:** A reference NFT is generated for the approved sequestration effort.
3. **On-Chain Update:** The NFT is stored in the credit smart contract and tied to the farmer’s wallet.

---

## **4. Performance and Scalability Considerations**

We have designed the system to scale as adoption grows:

### **4.1 Performance Optimizations**

- **Efficient Database Management:** MongoDB handles large datasets of farmer submissions and sequestration data with scalability in mind, ensuring the system can accommodate high volumes of input.
- **Transaction Batch Processing:** Stake pool operations are optimized for batch transactions, allowing multiple minting operations to occur simultaneously, reducing network load.

### **4.2 Scalability Considerations**

- **Geographic Expansion:** The architecture supports the addition of multiple regions with varying sequestration methods. As new methods (e.g., reforestation, soil regeneration) are approved, these will be incorporated into the system.
- **User Growth:** The project is positioned to onboard hundreds of users without disrupting system performance by using a low-barrier entry system (wallet creation and onboarding via the front end).
- **Financial Solutions:** In the future we plan to use the node for small farms to process Transactions and to use Cardano as a Community Block Chain Credit Union. 

---

## **5. Updated System Documentation and Process for Minting Tokens**

### **5.1 Steps for Minting**

1. **Sequestration Project Creation:** Farmers select land and initiate biochar or IMO creation efforts.
2. **Submission to Board:** Data (photos, test results) is submitted and reviewed by the board.
3. **Approval:** Once validated, a reference NFT is minted and stored in a smart contract.
4. **Credit Creation:** Each verified carbon sequestration effort results in a minted credit, which can be transferred, sold, or retired.

---

