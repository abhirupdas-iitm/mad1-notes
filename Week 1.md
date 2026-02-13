## Lecture 1

### Types of Apps
##### Description: Obtaining an overall idea about 'apps' in general and a broad classification of various kinds of applications

#### Web Apps
- **The Platform**
- Works across OS, device → create common base
- Heavily network dependent
  - Workarounds for offline processing
- **Main focus of this course**

#### Mobile Apps
- Targeted at mobile platforms: phones/tablets
- **Constraints**
  - Limited screen space, audio, camera
  - Memory/processing (touch, audio, camera)
  - Power
- **Frameworks**
  - Cross-platform
- **Network! oriented**
  - Usually network oriented

#### Desktop Apps
- Usually standalone
  - Editors/Word processors
  - Web browser
  - Mail
- Often work offline
  - Local data storage
  - Possible network connection
- **Software Dev Kits (SDK)**
  - Custom frameworks
  - OS specific

### Notes to be taken for `Activity Question 1`

1. For a web application to function smoothly, the client and the server should reside in different machines. (Question: 3)
2. SDKs integrate with other parts of the machine such that the user doesn’t have to carry out any integration manually. (Question: 4)
3. Cocoa Touch is an Apple specific SDK. (Question: 5)
---

## Lecture 2

### Components of an App
##### Description: - Understanding the various components that are integral to implementing an app like storage, computation and presentation and discussing various platforms, like desktop, mobile, web and embedded, on which applications are built and used

#### Components:
1. Storage
2. Computation
3. Presentation

#### Platforms
- Desktop
- Mobile
- Web-based
- Embedded

#### Platform features
- **Desktop**
  - Keyboard, mouse, video
  - Desktop paradigm – folders, files, documents
- **Mobile**
  - Touchscreen
  - Voice, tilt, camera interfaces
  - Small self-contained apps
- **Web-based**
  - Datacenter storage – persistent
  - Cloud: access anywhere, multi-device
- **Embedded**
  - Single function, limited scope

#### Components
- Storage
- Computation
- Presentation

#### Example: email client
- **Storage**
  - Where are the emails stored?
  - How are they stored on the server? File formats etc.
- **Compute**
  - Indexing of emails
  - Searching
- **Presentation**
  - Display list of mails
  - Rendering/display of individual mails

**Key ideas:**  
Different app platforms (desktop, mobile, web, embedded) have their own typical inputs, storage locations, and usage patterns, which affects how you design and deploy applications. Components like storage, computation, and presentation can be split across client and server; the email client example shows how data is stored, processed (index/search), and finally presented to the user.

### Notes to be taken for `Activity Question 2`

1. Electronic Calculator is an embedded application. (Question: 3)
2. Storage is used to manipulate the data based on request. (Question: 4)
---
## Lecture 3

### Client-Server and Peer-to-Peer Architecture

##### Description: - Understanding different system architectures used to build applications, mainly Client-Server and Distributed (Peer-to-Peer) models, and how clients, servers, and networks interact.

#### Types of Architectures
- Client-Server
- Distributed (Peer-to-Peer)
#### Client-Server Architecture

##### Server:
- Stores data
- Provides data on demand
- May perform computations

##### Clients:
- End users
- Request data
- Handle user interaction and display

##### Network:
- Connects client to server
- Can be local
- Acts as a data pipe (no alterations to data)

#### Client-Server Model

- Explicit differentiation between clients and servers
- Explicit server(s)
- Explicit client(s)

##### Local Systems:
- Both client and server can be on the same machine (local network / communication)
- Conceptually still a networked system

##### Machine Clients:
- Example: Software / antivirus updaters
- May not require direct user interaction

##### Variants:
- Multiple servers
- Single queue
- Multiple queues
- Load balancing frontends

##### Examples:
- Email
- Databases
- WhatsApp / messaging
- Web browsing
#### Distributed (Peer-to-Peer) Model

- All peers are considered "equivalent"
  - Some peers may be more equal than others (practically)
- No strict separation like client and server

##### Error Tolerance:
- Masters / introducers
- Election / re-selection of masters on failure

##### Shared Information:
- Data and responsibilities distributed among peers

##### Examples:
- BitTorrent
- Blockchain-based systems
- IPFS, Tahoe (distributed file systems)

**Key Ideas:**
Client-Server architecture clearly separates roles: clients request and display, servers store and compute, and the network connects them. In Distributed (Peer-to-Peer) systems, nodes act as equals, share responsibilities, and improve fault tolerance through distributed control and master re-election mechanisms.
### Notes to be taken for `Activity Question 3`

1. In general, it can suffer from the failure of a certain number of nodes. (Question: 1)
2. Peer-to-Peer is naturally more fault tolerant. (Question: 4)
3. For a client-server model to function smoothly, the client and the server have to be on different machines. (Question: 5)
---
