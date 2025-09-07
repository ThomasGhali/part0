# Exercise 0.4 Solution

```mermaid
sequenceDiagram
    actor U as User
    participant B as Browser
    participant S as Server

    U->>B: Clicks "Save" button
    B->>+S: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    S-->>-B: 302 Found
    note right of B: Redirect Location /exampleapp/notes
    
    B->>+S: GET https://studies.cs.helsinki.fi/exampleapp/notes
    S-->>-B: HTML document

    B->>+S: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    S-->>-B: The CSS file

    B->>+S: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    S-->>-B: The JavaScript file
    Note right of B: Browser executes JS code that fetches JSON from the server

    B->>+S: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    S-->>-B: [{"content": "note demo","date": "..."}, ...]
    Note right of B: The browser executes the callback function that renders the notes

    B-->>U: Display the updated notes
```