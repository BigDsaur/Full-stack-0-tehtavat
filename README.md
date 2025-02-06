# Full-stack-0-tehtavat



    0.4: uusi muistiinpano tehtävä


    sequenceDiagram
    participant user
    participant browser
    participant server
    
    user->>browser: Writes a note
    user->>browser: Clicks "Save"
    
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: 302 Found (Redirect to /notes)
    deactivate server
    
    Browser Refresh after redirect
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the CSS file
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server
    
    Note right of browser: The browser executes JavaScript to fetch updated notes
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Updated notes list [{ "content": "HTML is easy", "date": "2023-1-1" }, { "content": "New note", "date": "2025-2-6" }, ... ]
    deactivate server    

    Note right of browser: The browser executes the callback function that renders the updated notes



    0.5: Single Page App tehtävä


    sequenceDiagram
    participant browser
    participant server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: JavaScript file
    deactivate server
    
    JavaScript lataa SPA:n
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server
    
    JavaScript updates the page with notes without refresh



    0.6: Uusi muistiinpano tehtävä


    sequenceDiagram
    participant user
    participant browser
    participant server
    
    user->>browser: Writes a note
    user->>browser: Clicks "Save"

    JavaScript saves the note and updates page instantly

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>browser: 201 Created (Note saved)
    deactivate server

    Page doesnt need a reload because POST was created with status code 201
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Updated notes list [{ "content": "HTML is easy" }, { "content": "New note" }, ... ]
    deactivate server

    JavaScript updates the page with the new note

    


    

    
