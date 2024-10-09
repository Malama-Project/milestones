# Malama Project Milestone 1 Outputs:

**1. Project Blueprint Detailing Blockchain Architecture and Integration Strategy**:
  We have defined the initial blockchain architecture and integration strategy for The Malama Project. 
  We have organized our project into four main pillars:
  1a. Fully operational stake pool. All wallet creation, tx, and minting are performed using the stake pool. 
  2b. MongoDB. We use MongoDB for off-chain storage, and asset management before they go on-chain.
  3c. A react/ts frontend to allow user input.
  4c. Fastify Server. We use the Fastify server to facilitate communication between the stake pool, front-end, and MongoDB.

**2. UI/UX Design Prototypes for the Platform**:
  Carbon Sequestration Methods Information:
  The UI will include clear information on current carbon sequestration methods accessible through the user's profile via a dashboard. Currently: 

  A.IMO Creation 
    
  B.Biochar Application 
    
  Information related to carbon-increasing efforts is saved in the MongoDB until approved for credit creation/and minted by a board vote.
  We are starting with IMO(indigenous Micro-organism creation) and applying biochar. 
  Other methods will be added as approved by the project.     
   
**2b. Easy Signup for Farmers**
  When Farmers create an account with our app:
  1b. An address is automatically created and stored in the User's MongoDB account.
  2b. A savecard is created to track/identify users. This is in the CIP68 format to allow users to record sequestration efforts and to reference each credit to an address/farm. 
  3b. The reference NFT from the savecard will be sent to a Plutus contract which will store and validate all efforts for that user. 
  4b. Wallet creation and Savecard are made automatically, so not to discourage new users with the burden of Understanding WEB3 before they can use the app. Farmers should have a low barrier of entry to participate.  
**2c. Display Carbon Efforts On-Chain**:
  1c. All sequestration efforts will be automatically sent to the wallet created during farmer registration. 
  2c. Users will be able to see all credits created or (sensors readings if present)
  -an example of sensor data being actively recorded on-chain can be found here: **https://nana-frontend.vercel.app/dagwell-test**

 **Please access UI.UX screenshots at https://github.com/Malama-Project/milestones/tree/main/UI.UX**

**3. Documentation on the Process for Minting Tokens Based on Farmers' Sequestration Efforts**:
  Farmers to mint tokens (NFTs) for their carbon sequestration efforts.
  a.This process starts with the farmer creating a sequestration project. 
  b.The farmer can select his land on an interactive map.
  c.Once land is selected, farmers can start sequestration efforts.(Currently Biochar application, and IMO creation)
  d.When a farmer starts a sequestration effort, a draft is created in our MongoDB
  e. The sequestration effort goes to our board to verify the effort is valid. (Location, pictures, and biochar test results)
  f.Once approved, a reference NFT is created and stored in a smart contract, allowing the userNFT to become the credit. 
  g. Once the credit leaves the user's wallet, it is marked as retired. 

  


