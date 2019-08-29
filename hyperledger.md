# Notes:
1) not a cryptocurrency	,it is a blockchain
2) No mining
3) different concensus as like cryptoCurrency
>> properties like block immutability prevention of double spending are maintained
4) Operate in a  range of 1/2 a million transactions per minute
5) Distributed database-distributed b/w all the parties in the network.All participants hold same data.
6) no single point of failure.
7) Ledger stores every single operation on blockchain.
8) No Limit.dont enforce particular hardware. it works anywhere.
9) Participant visibility matters.
10) Hyper Fabric is running on Docker


# 3 Important Components:
## Fabric CA(Certificate Authority):
> Every single operation in HyperFabric must be signed cryptograhically with the certificate.Best CryptoGraphic Standard.
> 509 standards
> Different cer. for diff user
> In certificate, Information Can contain different
#### attributes
it is propagated. so the chaincode can read this data and manipulate. 
####transitData
> provide username,password to generate certificate,enforce privacy,expiry,etc..
> High quality. but user is not enforced to use this.

## Peer
> it is the place where blockchain data is stored.
> A network contains N no. of peers.
> 1 Peer can control multiple channels.
> It updates the ledger.
> It is the heart of the system.
> All the peers synchronise automatically

## Ordering Service
> It verifies the policies
> Heart of the concensus algorithm
> provide Orderer of the operation.Before commiting, Every operation must pass thru ordering service. It creates the blocks,signed and verified.
> After that it send these blocks to the peers.
> Then peers verify and commit to the ledger.
> Responsible for verification,security,policy verification.
> It is done by 
####Apache Kafka
It has distributed ordering service.If one is down,others will take care.
It manages currency,double spending and all other problems.

## Channels
> Main way for data relation
> Separate instance of hyperledger fabric
> every channel is completely inpendent.
> They never exchange data.

* channel 1 = a---b---c
* channel 2 = a---b => c cannot know the information shared in channel 2
> If c wants to join the channel2, all the parties i.e: a&b must agree to join c in that channel. Even if one party disagree,it wont allow c to join 
> Can add N no. of peers to same channel
> Can add N no. o f groups | members to same channel
> One peer can be into N no of channels

## Chaincode(golang/python/java/javascript)
> It is a program/smart contract
> It will read/write ledger data
> Operation -> the sdk sends the transaction to the peer.
> peer executes the chain code
> Only chaincode can interact with the Ledger.

> If we have 3 peers as a part of the channel, we have to install the chaincode on every single peer.
> ledger data is inside the peer.

> step3 -> install -> instantiate

### Policy
> when we instantiate ,we need to provide the policy
> Policy, before executing something ,every single peer needs to verify the transaction,or majority or atleast by one.
> Every single chain code has different policy
> we cant have a chain code without policy.

## Whole Structure:
> A peer may be part of n no. of channels
> Every channel has separate ledger
> Every channel has one or many chain codes
> each chain code has different policy

link : https://hyperledger-fabric.readthedocs.io/en/latest/endorsement-policies.html

# MSP(Membership Service Provider)
> It is a set of cryptographic materials that define organisation it self.
> Every peer need these type of certificates.
> It tells,this peer is this part of organization and so on.
> Only peers are the part of the MSP that can communicate each other.

> Channel (public certificates)