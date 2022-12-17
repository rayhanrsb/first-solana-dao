# Rayhan's First Dao Attempt

This repo demonstrates how to create a custom DAO using the Governance library from the Solana Program Library (SPL).

It is built for simplicity, allowing anybody to create a DAO by simply submitting a name for the DAO (after having connected their wallet of course). It assumes no governance mint has been created and creates one for the DAO.

Many thanks to Mango Markets and Maximilian Schneider for putting together a [guide](https://mango-markets.notion.site/Solana-Governance-Demo-e188492717644a6e8288a7d8379263e8) that was of great help in building this repo.

Of course, many thanks to the Solana team, in particular the Realms team for putting together the spl-governance library which is the basis of this program. Reading through your code was a delight and is exemplary for any delevoper on Solana looking for inspiration on how to write great code.

The program ID of the governance program instance is EjoScY8tP3ksb8jB4j6aUWKD6bC7DkrE2yXKWJd8MvjA. It is currently deployed to devnet.

## Steps to reproduce / How I built this

### Step 1 - Clone the program and front-end repos

Clone the solana program library, build your own instance of the governance program and keep note of the program ID (you will need this later):

    git clone https://github.com/solana-labs/solana-program-library
    cd solana-program-library/governance/program
    cargo build-bpf
    solana program deploy ../../target/deploy/spl_governance.so

Clone the provided front-end (or dont - you can interact with you program with a custom built client if you prefer):

    git clone https://github.com/solana-labs/oyster.git

The package you are looking for in the oyster repo is under packages/governance

In the repo root directory (the oyster directory), I ran the commands:

    yarn && yarn bootstrap && yarn build --scope @oyster/common --scope @solana/spl-governance --scope governance
    yarn start governance

That started up the front-end.

### Step 2 - Configure your front-end (if you cloned the front-end repo)

If you cloned the front-end, When you launch it you need to change the program ID in the url to the program ID of your instance of the governance program.

The url structure might be like this: http://localhost:3000/#/?rogramId=INSERT_YOUR_PROGRAM_ID_HERE.

I later configured the .env file in the oyster\packages\governance directory to use my program ID as the default governance program ID, so I don't have to pass it through the url query anymore

### Step 3 - Follow the instructions

If you cloned the front-end repo and configured it properly, you will now see a flow for creating a new DAO (in Solana, DAOs are called Realms). Go ahead and do so.

If you did not use the provided front-end, you can create your own front-end that interacts with your governance program directly. Check out the SDK [here](https://github.com/solana-labs/oyster/tree/main/packages/governance-sdk) which could help you get started.
