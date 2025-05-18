Ejercicio 0.6 - Nueva nota en diagrama de aplicación de una sola página

Crea un diagrama que represente la situación en la que el usuario crea una nueva nota utilizando la versión de una sola página de la aplicación.

    sequenceDiagram
        participant Client
        participant Server

        note over Client: Client executes a handler function when the user clicks the <br/> "Save" button. A new note is created and added to the list.<br/> Then, the complete list is reloaded and sent to the server.

        Client->>Server: HTTP POST /exampleapp/new_note_spa
        
        note over Server: POST petition to new_notes_spa <br/> direction contains the new note.
        
        Server-->>Client: Status Code 201 Created <br/>{content: "Hi, I'm sending a new one on SPA ", date: "2025-05-18T16:17:16.209Z"}

        note over Client: The page does not reload, and the user stays on the same view. <br/> This behavior is typical in a SPA (Single Page Application).

![](part0\assets\new note SPA.png)