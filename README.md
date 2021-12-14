# Specification for a General Purpose Event Tickets Open Internet Service


## Impetus

There are a great number of potential uses for a general purpose ticket NFT service, which would allow creators to monetize and control access to online meetup events, public NFT sale events, early access to a new dApp, and so on.

## Primary Components

**Standard NFT Interface:** Should implement the implied NFT standard of the IC, making sure to include the ability to burn, and perhaps the ability to perform allowances.    

**Minting:** Users must be able to mint tickets, with parameters:
- number of tickets: Nat
- name: Text
- description: Text
- branding: Asset (aviate/assets.mo)
- date start: opt Time
- date end: opt Time
- date start label: opt Text
- date end label: opt Text
- etc...

**Ticket Display:** The ticket display should be a simple SVG graphic that has an attractively simple design, injected with the metadata of each token. Standard views should be adhered to (ext token identifier, token index, thumbnail view.)    

**Payments:** Users should be charged to mint tickets, and payouts should be regularly made based on a distribution that all developers agree upon.    

## Limitation of Scope

There are tempting functions to add to this canister, but I think they should be resisted. For example, logic for the initial allocation of tickets, or the initial sale of tickets, or the use of a ticket by a holder, etc. Instead, these would be valuable later additions, or services of their own.

## Ticket Lifecycle Example:

**Minting:** A batch of tickets would be minted by a creator, who would specify the metadata and display information that they require for their purpose. The ticket canister stores the metadata and mints the run of ticket NFTs to the desired address.    

**Burning:** The general use case of a ticket is to spend that ticket in order to gain access to some event, dApp feature, etc. This is achieved by allowing a dApp to take control the users ticket NFT and burning that NFT. This is done by transferring the NFT to the blackhole principal.    

**Expiration:** A ticket may be given an expiration date. In those cases, we should indicate with a bright colour that the ticket has expired, and expired tickets should perhaps be evicted from memory after some time.   

## Scaling to an arbitrary number of tickets

How do we keep the service running as more and more tickets are minted? 

## CAP integration

Provenance and transaction history would be very good to have.

## DAB integration

Plus creating PRs into other wallets, so that we are automatically discovered.

## Use Case #1: NFT Pre Sale

- A creator pays for and mints a run of tickets
- Tickets are sent to the creator's address
- Creator manually sends those tickets to holders who will be able to access the pre sale
- Ticket holder presents ticket during pre sale
- Pre sale canister requests allowance on the ticket
- Pre sale canister burns the ticket
- Pre sale canister creates a token capturing the user's access to the pre sale
- Pre sale canister can indicate whatever metadata on this token at burn time, such as an allocation to purchase one NFT from the sale
- Pre sale frontend application may now provide access to restricted views
- Token can be used to control access to pre sale, allowing the user to complete a purchase for one NFT

## Use Case (Common) - Events Ticket

- Event host create an event with ticket specifications: name, count, picture ...
- Users register the event by paying with cryptocurrency (e.g ICP...) and get a ticket which is minted NFT
- (online event) Users login the event system, and host will verify the ticket base on the principal
- (offline event) Users print the ticket and bring it to the event, host scan the ticket for verification(so might need to generate a QR code on ticket for this scenario?)

## Milestones

- Completed V1 of the specification with consensus from collaborators.
- Build an alpha version of the canister.
- Use the alpha canister in a real world event (Saga legends pre sale in January or February.)
- Release a beta version
    - Implement learnings from first real world use
    - Develop a landing page
    - Create some developer documentation
