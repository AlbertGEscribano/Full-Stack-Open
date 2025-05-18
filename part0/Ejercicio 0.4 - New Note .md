Ejercicio 0.4 - Nuevo Diagrama de Nota

Crea un diagrama similar que describa la situación en la que el usuario crea una nueva nota en la página https://studies.cs.helsinki.fi/exampleapp/notes escribiendo algo en el campo de texto y haciendo clic en el botón Save.


    sequenceDiagram
        participant Client
        participant Server

        note over Client: Client add new note: "Hi, I'm sending new one"
        Client->>Server: HTTP POST https://studies.cs.helsinki.fi/exampleapp/new_note

        note over Server: Server saves a new note and responds with an HTTP 302 status code. <br/>This URL redirection request redirects the browser to the URL <br/> https://studies.cs.helsinki.fi/exampleapp/notes, which is found in <br/>the header of the HTTP request.

        Server-->>Client: Redirection to https://studies.cs.helsinki.fi/exampleapp/notes
        
        note over Client: Post method reloads browser, generating a new server call

        Client->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/notes
        Server-->>Client: HTML-Code
        Client->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.css
        Server-->>Client: main.css
        Client->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.js
        Server-->>Client: main.js

        note over Client: Browser starts executing js-code that request JSON data from server

        Client->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/data.json
        Server-->>Client: [{ content: "Hi, I'm sending new one", date: "2025-05-18T11:49:04.582Z" }, ...]

        note over Client: Browser executes the event handler that renders notes to display

![](https://github.com/AlbertGEscribano/Full-Stack-Open/blob/720d147e426c5807fbd658c8a7c815dae9086b47/part0/Ejercicio%200.4%20-%20New%20Note%20.md)