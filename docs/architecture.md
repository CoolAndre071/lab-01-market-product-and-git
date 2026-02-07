## Product Choice

* **Product:** Telegram
* **Website:** <https://telegram.org>
* **Description:** Cloud-based messenger for phones and desktopes, that focuses on speed and security.
  
## Main components

![Component Diagram](./diagrams/out/telegram/component-diagram/Component%20Diagram.svg)

[Link to PlantUML Code](./diagrams/src/telegram/component-diagram.puml)

**Components description:**

1. **Mobile/Desktop Client:** The user-facing application, that handles encrypting, local storaging etc.
2. **MTProto Proxy/Load Balancer:** The entry point for all client connections; it manages the encrypted connection and routes requests to the appropriate backend services.
3. **Auth Service:** Handles user registration, login verification via SMS codes, and session management.
4. **Message Database:** A distributed database that handles everything user need to connect to cloud-chat-services.
5. **Media Storage / CDN:** A distributed file storage system responsible for uploading, storing, and delivering images, videos, and documents efficiently.

## Data flow

![Sequence Diagram](./diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)

[Link to PlantUML Code](./diagrams/src/telegram/sequence-diagram.puml)

**Flow description:**

* **Selected Group:** Sending a Text Message.
* **Description:** The user types a message in the Client App. The Client encrypts the payload using MTProto and sends it to the Server. The Server authenticates the session, saves the message to the Message Database.

## Deployment

![Deployment Diagram](./diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)

[Link to PlantUML Code](./diagrams/src/telegram/deployment-diagram.puml)

**Description:**
The client applications are deployed on phones, desktopes, etc. There are many Data Centers across the globe, which gives user low-latency messenger by connecting users to closest data centers.

## Assumptions

1. I assume the notification service relies on Google and Apple services, that gives opportunity to "wake up" device while it is in background mode.
2. I assume that cloud-chats uses server-side encryption, where keys are stored on server, while secret-chats contain keys only on both devices using end-to-end encryption.

## Open questions

1. How implemented global search, that can search across multiple databases across the world?
2. What is used in spam-filtering system?
