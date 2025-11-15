## 0.4

```mermaid

sequenceDiagram
    participant Browser
    participant Server
    
    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note 
    activate Server
    Server-->>Browser: Location: https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate Server
    Server-->>Browser: HTML document
    deactivate Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    Server-->>Browser: the css file

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    Server-->>Browser: JavaScript file

    Note right of Browser: browser starts execuring JS code and fetches new notes

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: JSON (including the new note)
    deactivate Server

    Note right of Browser: browser executes the callback function to render new notes
```



## 0.5

```mermaid
sequenceDiagram
    participant Browser
    participant Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate Server
    Server-->>Browser: HTML document (root + empty notes container)
    deactivate Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate Server
    Server-->>Browser: CSS file
    deactivate Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate Server
    Server-->>Browser: JavaScript (SPA app bundle)
    deactivate Server

    Note right of Browser: JS initializes the SPA: fetch references, register event handlers

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: JSON of notes
    deactivate Server

    Note right of Browser: Javascript updates in-memory state and renders notes to the DOM

```





## 0.6



```mermaid
sequenceDiagram
    participant Browser
    participant Server

    Note right of Browser: User creates a new note
    Note right of Browser: JS execute event.preventDefault
    Note right of Browser: event handler creates new note, notes.push(note)
    Note right of Browser: re-renders notes list in the DOM

    Browser->>Server: POST Content-Type: application/json, body: {"content":"...", "date":"..."}
    activate Server
    Note right of Server: Server appends new note to storage
    Server-->>Browser: 201 Created
    deactivate Server

    

```

























































































