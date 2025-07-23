# Testing Multiplayer
---
### 01. Testing In-Editor

![[Pasted image 20250723100721.png]]
Unreal engine has built in multiplayer testing capabilities.

**Net mode**
- Play Standalone: a standalone game will be started
- Play As Listen Server: the editor will act as both a Server and a Client
- Player as Client (Dedicated Server): the editor will act as a Client. A server will be started for you behind the scenes to connect to

### 02. LAN Connection

LAN(Local Area Network)

# Online Subsystem
---
### 01. IP Address

Local IP Address (Internal IP Address): the address assigned to your computer by your local network router

Public IP (External IP): your router has a public IP address that the rest of the internet connects to

### 02. Online Subsystem

In order to connect to another machine without knowing its IP, we need an intermediate step, whether it’s out ow dedicated server or a server hosted by a professional service like steam.

Unreal Engine has its own functions that we can use to connect to a service and depending on which service our game is configured to use Unreal Engine will handle all of the platform specific details under the hood when a program or game engine allows us to just interact with a single code base handling all the cross-platform ability under the hood

**Online Subsystem**
- Unreal Engines’ own code base for managing the connection to online services
- provides s with an abstraction layer, so we don;t need to learn the code bases for each service we wish to use for out games
- Contains functions that we can use to connect to services, have them host our game sessions and connect us to other players

# Online Session
---
### 01. Online Subsystem

Online Subsystem
- Access functionality online services

Interface
- Friends Interface
- Achievements Interface
- Sessions Interface

Platform Services
- Friends
- Achievements
- Sessions
- Etc.

### 02. Session Interface

Session Interface
- creating, managing and destroying game sessions
- searching for sessions
- matchmaking

Session
- an instance of the game running on the server
- advertised (players can join), or private (invite only)

**Lifetime of a Session**
Create Session → wait for players to join → register players → start session → play → end session → unregister players → update session or destroy session

**Session interface function**
CreateSession(), FindSession(), JoinSession(), StartSession(), DestroySession()

### 03. Our Game Plan

![[Pasted image 20250723100756.png]]

# Configure for Stream
---
### Configure the Project for Steam

[Online Subsystem Steam Interface in Unreal Engine | Unreal Engine 5.4 Documentation | Epic Developer Community](https://dev.epicgames.com/documentation/en-us/unreal-engine/online-subsystem-steam-interface-in-unreal-engine?application_version=5.4)

### Access the Online Subsystem

smart pointer: The **Unreal Smart Pointer Library** is a custom implementation of C++11 smart pointers designed to ease the burden of memory allocation and tracking. This implementation includes the industry standard **Shared Pointers**, **Weak Pointers**, and **Unique Pointers**. It also adds **Shared References** which act like non-nullable Shared Pointers. These classes cannot be used with the `UObject` system because Unreal Objects use a separate memory-tracking system that is better-tuned for game code.

ctrl + shift + B
: 비주얼 스튜디오에서 컴파일
(언리얼 엔진에서 라이브 코딩은 꺼 놓는 게 좋은 듯?)

t shared pointer smart pointer wrapper
```jsx
TSharedPtr<class IOnlineSession, ESPMode::ThreadSafe> OnlineSessionInterface;
```
This approach is used to prevent potential issues that can arise with multithreading.

ERROR: unable to delete hot-reload files
1. **Delete the `Saved`, `Intermediate`, and `Binaries` folders** within your project's directory.
2. **Generate your Visual Studio project files.**
3. **Open the newly generated project file** in Visual Studio.
4. **Rebuild the modules** within your project.

![[Pasted image 20250723100854.png]]
![[Pasted image 20250723100905.png]]

To connect to the Steam online subsystem, make sure the Steam desktop app is running and you're logged in.
→ build한 프로젝트를 실행해야 연결된 걸 확인할 수 있음

# Creating a Session
---
### 01. Delegate and Callback
- an object that holds a reference to a function
- unreal engine delegates are capable of having functions bound to them, then broadcasting a signal that each bound function will receive and execute in response to the broadcast