sequenceDiagram
    participant You
    participant Browser
    participant Server

    You->>Browser: Type note and hit Save
    Browser->>Server: POST /new_note
    Server->>Server: Save that note
    Server-->>Browser: Hey, go to /notes
    Browser->>Server: GET /notes
    Server-->>Browser: Here's the page
    Browser->>Server: GET /main.css
    Server-->>Browser: Here's the styling
    Browser->>Server: GET /main.js  
    Server-->>Browser: Here's the code
    Browser->>Server: GET /data.json
    Server-->>Browser: Here's all notes
    Browser->>Browser: Show updated list
    