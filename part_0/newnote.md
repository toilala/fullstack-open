sequenceDiagram
    participant User
    participant Browser
    participant Server

    Note left of User: User types note content<br/>and clicks Save button

    User->>Browser: Click Save button
    activate Browser
    
    Browser->>Browser: JavaScript event handler executes
    Note right of Browser: Form data is collected<br/>and POST request prepared
    
    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate Server
    Note left of Server: Server processes new note<br/>and adds it to data.json
    
    Server-->>Browser: HTTP 302 Redirect to /notes
    deactivate Server
    
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate Server
    Server-->>Browser: HTML document
    deactivate Server
    
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate Server
    Server-->>Browser: CSS file
    deactivate Server
    
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate Server
    Server-->>Browser: JavaScript file
    deactivate Server
    
    Note right of Browser: Browser executes JS code
    
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: Updated JSON with new note<br/>[{content: "new note", date: "..."}, ...]
    deactivate Server
    
    Note right of Browser: Browser executes callback<br/>and re-renders notes list<br/>(including the new note)
    
    deactivate Browser