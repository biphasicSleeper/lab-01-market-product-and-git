## Product Choice
The name of the product is Telegram. The website is: [telegram.org](https://web.telegram.org). It is a website and an app for chatting with people.
## Main components
![Telegram Component Diagram](./diagrams/out/telegram/component-diagram/Component%20Diagram.svg)
![Telegram Component Diagram Code](./diagrams/src/telegram/component-diagram.puml)
The Mobile App displays the chats of the user on the phone. 
Desktop App does the same thing, but as a desktop app.
Web Client does the the same as well, but is accessible through the browser instead.
Notification and Update Service is responsible for sending users notifications, be it on the mobile or on desktop, and is responsible for updating the app as well.
Media and File Service are responsible for the transfer of media between users.
## Data flow
![Telegram Sequence Diagram](./diagrams/out/telegram/sequence-diagram/Sequence%20Diagram.svg)
![Telegram Sequence Diagram Code](./diagrams/src/telegram/sequence-diagram.puml)
Media Upload is responsible for tackling the exchange of media in between users. First, the image is chosen and sent, and then it gets saved in parts until all the parts get saved to the server. 
## Deployment
![Telegram Deployment Diagram](./diagrams/out/telegram/deployment-diagram/Deployment%20Diagram.svg)
![Telegram Deployment Diagram Code](./diagrams/src/telegram/deployment-diagram.puml) There are User Devices and a Third-Party Server, which are connected to Telegram's Global Infrastructure. The latter consists of the Edge/Construction Layer, the Compute Cluster, the In-Memory Cluster, Storage Cluster, and an Event Cluster.
## Assumptions
- I assumed the notifications are sent through the same system, be it on mobile or desktop.
- I also assumed the Third party Server is not a part of Telegram's Global Infrastructure.
## Open questions
- How can people send voice messages?
- How do pictures which are invisible at first get computed?
