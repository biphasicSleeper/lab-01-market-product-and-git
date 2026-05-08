## Product Choice
The name of the product is Telegram. The website is: [telegram.org](https://web.telegram.org). It is a cloud-based messaging platform that allows users to communicate through text messages, voice messages, video calls, group chats, and media sharing. It is available both as a website and as downloadable applications for mobile devices and desktop computers. One of Telegram’s main strengths is its ability to synchronize messages and files across multiple devices in real time. This means that a user can begin a conversation on a smartphone and continue it later on a desktop or in a browser without losing any data. Telegram is also known for its speed, scalability, and emphasis on privacy and security.
## Main components
![Telegram Component Diagram](./diagrams/out/telegram/component-diagram/Component%20Diagram.svg)
![Telegram Component Diagram Code](./diagrams/src/telegram/component-diagram.puml)
- The Mobile App displays the chats of the user on the phone. It allows users to send text messages, images, videos, stickers, voice messages, and files. The mobile application also handles notifications and background synchronization with Telegram’s servers.
- Desktop App does the same thing, but as a desktop app. Users can communicate, manage files, and participate in group conversations through a desktop environment.
- Web Client does the the same as well, but is accessible through the browser instead. This component is especially useful for users working on shared or restricted devices because communication can happen entirely through a web browser.
- Notification and Update Service is responsible for delivering notifications to users on both desktop and mobile devices. It informs users when they receive messages, calls, or updates. In addition, it manages application updates and ensures clients remain synchronized with the latest features and security patches.
- Media and File Service manages the upload, download, storage, and transfer of files and media between users. This includes photos, videos, documents, stickers, and voice recordings. Since Telegram supports large file transfers, this component is essential for maintaining fast and reliable media delivery.
## Data flow
![Telegram Sequence Diagram](./diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)
![Telegram Sequence Diagram Code](./diagrams/src/telegram/sequence-diagram.puml)
Media Upload is responsible for tackling the exchange of media in between users. The process begins when a user selects an image or another media file to send. The client application then divides the file into smaller parts before transferring it to Telegram’s servers. Splitting the file into chunks improves reliability because interrupted uploads can resume without restarting the entire transfer.

Once each chunk reaches the server, it is temporarily stored and verified. After all chunks have been received successfully, the server reconstructs the complete file and stores it in Telegram’s storage infrastructure. The media is then linked to the chat and becomes available for download by the receiving user. This process ensures efficient media handling while supporting large-scale communication.
## Deployment
![Telegram Deployment Diagram](./diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)
![Telegram Deployment Diagram Code](./diagrams/src/telegram/deployment-diagram.puml) There are User Devices and a Third-Party Server, which are connected to The deployment diagram illustrates how Telegram is distributed across multiple systems and infrastructure layers. Users interact with Telegram through User Devices, such as smartphones, tablets, desktops, and web browsers. These devices connect to Telegram’s Global Infrastructure, which is designed to handle communication requests efficiently and reliably.
The infrastructure contains several layers:
-The Edge/Connection Layer manages incoming user connections and routes requests to the correct services.
-The Compute Cluster processes application logic, authentication, and message handling.
-The In-Memory Cluster stores temporary and frequently accessed data for faster performance.
-The Storage Cluster keeps persistent data such as chats, files, and media.
-The Event Cluster handles asynchronous events, notifications, and background processing tasks.
The deployment also includes a Third-Party Server, which is shown as separate from Telegram’s internal infrastructure. This server may provide external integrations, APIs, or additional services connected to the platform.
## Assumptions
- I assumed the notifications are sent through the same system, be it on mobile or desktop.
- I also assumed the Third party Server is not a part of Telegram's Global Infrastructure.
## Open questions
- How are voice messages recorded, compressed, stored, and transmitted efficiently between users?
- How are “view-once” or initially blurred images processed and protected before being revealed to the recipient?
