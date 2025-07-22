[Networking and Multiplayer in Unreal Engine | Unreal Engine 5.5 Documentation | Epic Developer Community](https://dev.epicgames.com/documentation/en-us/unreal-engine/networking-and-multiplayer-in-unreal-engine)

true multiplayer: two or more instances of the game are running on different machines

### Peer-To-Peer
---
player’s information is sent directly to the other players’ computer

**issue**
- when there are many players, there is a great deal of data being transmitted across the network
- there is no authoritative version of the game

### Client-Server
---
a single machine is designated as the server while all other machines are designated as clients.
each client will only need to meet the bandwidth requirements for sending and receiving.

**server**
- often authoritative: the server runs a version of the game that is deemed to be the correct version.
- player send a request to the server, which then checks to make sure that that movement is appropriate → then he server moves the character and distributes that movement update information to all the clients (: replication)

**ways to implement the client-server model**
- Listen-Server: player is actually playing the game on that machine
    - one of the player’s machines acts as the server
    - playing the game, rendering graphics
- Dedicated-Server: the machine is dedicated to simulating the authoritative version on the game and replicating information down to all clients
    - a machine is a designated to be the server for the game
    - no one is actually playing the game on this machine → there’s no need to render the graphics
    - allow for the server machine to only handle simulating the authoritative version of the game and replicate data down to the client

### Unreal Engine Multiplayer
---
unreal engine uses an **authoritative client-server** model