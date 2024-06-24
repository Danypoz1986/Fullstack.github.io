# New Note Sequence Diagram

```mermaid
sequenceDiagram
    participant browser
    participant server
    
    Note right of browser: Käyttäjä kirjoittaa tekstikenttään muistiinpanon ja painaa "tallenna" nappia
    
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note (with note data)
    activate server
    Note right of server: Palvelin vastaanottaa uuden muistiinpanon tiedot ja tallentaa ne
    server-->>browser: HTTP 302 Redirect to /notes
    deactivate server
    
    Note right of browser: Selaimen ohjataan takaisin /notes-sivulle
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server
    
    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Updated JSON data with the new note
    deactivate server
    
    Note right of browser: The browser executes the callback function that renders the updated list of notes

