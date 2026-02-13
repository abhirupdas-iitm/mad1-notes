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

## Lecture 4

### Software Architecture
##### Description: - Introduction to design patterns in software architecture, with focus on Model-View-Controller (MVC) and related patterns used in web-based client-server applications.

#### Common Software Architecture Patterns
- MVC (Model-View-Controller)
- MVA (Model-View-Adapter)
- MVP (Model-View-Presenter)
- HMVC (Hierarchical MVC)
- MVVM (Model-View-ViewModel)
- ...
#### What is a Design Pattern?
- A general, reusable solution to a commonly occurring problem within a given context in software design.
- Experienced designers observe recurring "patterns" in code.
- Reusing these patterns can make design and development faster.
- Patterns guide the design and thought process.

#### Model-View-Controller (MVC)

##### Model:
- Core data to be stored for the application.
- Typically involves databases.
- Responsible for indexing and preparing data for easy searching and manipulation.
- Example (Email app): Stores emails on server, indexed and ready to manipulate.

##### View:
- User-facing side of the application.
- Interfaces for finding and manipulating information.
- Responsible for display only.
- Example (Email app): Display list of emails; read individual emails.

##### Controller:
- Contains the "business logic" of the application.
- Decides how data should be manipulated.
- Handles user actions.
- Example (Email app): Sort emails, delete, archive.

#### MVC Interaction Flow
- User uses **controller**
- Controller manipulates **model**
- Model updates **view**
- User sees the updated view

#### Origins of MVC
- Not a new concept.
- Originated in the Smalltalk language (1979).

#### Other Design Patterns
- Model-View-Adapter (MVA)
- Model-View-Presenter (MVP)
- Model-View-ViewModel (MVVM)
- Hierarchical MVC (HMVC)
- Presentation-Abstraction-Control (PAC)
- ...

- Each pattern has its own use cases, but the fundamentals are similar.
#### Focus of This Course

- Platform:
  - Web-based
- Architecture:
  - Client-server
- Software architecture:
  - Model-View-Controller (MVC)

- Goal: Build web-based applications with a central server.
- Use hypertext markup to control and manipulate display.
#### Example Scenario: User Wants to Check Email

- User interacts with the View (email interface).
- Action is sent to the Controller.
- Controller requests required data from the Model.
- Model retrieves emails from storage (server/database).
- View is updated and displays the list of emails to the user.
### Notes to be taken for `Activity Question 4`

1. The model does not control user interaction and the controller executes the business logic of an application. (Question: 1)
2. In the M-V-C architecture, the developer can create multiple views of a model. (Question: 4)
---

## Lecture 5

### Why the "Web"
##### Description: - Understanding why the web is chosen as the platform for this course, along with its historical evolution and underlying networking principles.

#### Why Web as a Platform

- Platform of choice for this course
- Generic platform:
  - Works across operating systems
  - Works across hardware architectures
  - Cross-platform by design
- Built on sound underlying principles
- Worth understanding:
  - Constraints: what can and cannot be done easily
  - Costs: storage, network, device sizing, datacenter infrastructure

#### Historical Background

##### Telephone Networks (~1890+)
- Circuit-switched networks
  - Allow A to talk to B through a complex switching network
- Physical wires tied up for the entire duration of a call
- Resources occupied even if no data (voice) is being transmitted
##### Packet-Switched Networks (~1960s)
- Wires occupied only when data is sent
- More efficient resource usage
- Designed for data instead of continuous voice transmission
##### ARPANet (1969)
- Node-to-node network
- Mostly university-driven
- Early foundation of modern internet concepts
##### Other Early Networks
- IBM SNA
- Digital DECNet
- Xerox Ethernet
- Each had its own design and protocol mechanisms

#### Protocols and Internetworking

##### Protocol
- Defines how to format packets
- How to place them on the wire
- Headers, checksums, and interpretation rules
- Initially, each network had its own protocol

##### "Inter" Network Concept
- How to communicate between different network protocols?
- Idea: introduce a common "inter-network" protocol

##### IP – Internet Protocol (1983)
- Defines packet headers, packet types, and interpretation
- Can operate over different underlying networks:
  - Ethernet
  - DECNet
  - PPP
  - SLIP

##### TCP – Transmission Control Protocol (1983)
- Establishes reliable communication
  - Retries
  - Error control
- Automatically scales and adjusts to network limits

#### Where Are We Now?
##### Original Web (Early Web)
- Static pages
- Complicated executable interfaces
- Limited styling capabilities
- Browser compatibility issues

##### Web 2.0 (~2004+)
- Dynamic pages generated on the fly
- HTTP used as a general transport mechanism
  - Supports binary data and serialized objects
- Client-side computation and rendering
- Platform-agnostic environment (acts like an operating system layer)

**Key Idea:**
The web evolved from circuit-switched communication systems to packet-switched, protocol-driven networks that enabled scalable, cross-platform communication. With TCP/IP and Web 2.0, the web became a powerful, dynamic, platform-independent system capable of supporting modern applications.

### Notes to be taken for `Activity Question 5`

1. UDP can result in data loss. (Question: 2)
2. A set of rules that defines how the data packets are formed and placed on wires is called `Protocol`. (Question: 6)
3. Internet protocol does not necessarily establish a reliable communication. (Question: 7)
4. Limited connectivity was not a limitation of the original web. (Question: 8)
5. The internet is a network of networks. (Question: 11)
6.  TCP gives priority to the reliability of data delivered. (Question: 12)
---
