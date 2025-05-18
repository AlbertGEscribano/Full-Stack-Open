0.5 - Diagrama de aplicación de una sola página

Crea un diagrama que describa la situación en la que el usuario accede a la versión de aplicación de una sola página de la aplicación de notas en https://studies.cs.helsinki.fi/exampleapp/spa.

    sequenceDiagram
        participant Client
        participant Server

        Client->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/sp
        Server-->>Client: HTML-code
        Client->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.css
        Server-->>Client: main-css-code
        Client->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/spa.js
        Server-->>Client: spa.js

        note over Client: Browser starts executing js-code <br/> that request JSON data from server

        Client->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/data.json
        Server-->>Client: [{content: "Hi, I'm sending a new one on SPA ", date: "2025-05-18T16:04:07.475Z"}]

        note over Client: Browser executes the event handler <br/> that renders notes to display

![](part0\assets\SPA.png)