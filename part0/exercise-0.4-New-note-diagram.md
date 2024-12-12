```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>+server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    Note right of browser: Form data is sent in the request body
    server-->>-browser: 302 Found (Redirect to /notes)

    browser->>+server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>-browser: HTML document
    deactivate server

    browser->>+server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>-browser: the css file
    deactivate server

    browser->>+server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>-browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>+server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>-browser: [{ "content": "New note and others", "date": "2023-10-27" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes including the new one.
```