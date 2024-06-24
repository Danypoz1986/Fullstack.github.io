# Creating a New Note in Single Page App Sequence Diagram

```mermaid
sequenceDiagram
    participant browser
    participant server
    
    Note right of browser: Käyttäjä kirjoittaa tekstikenttään muistiinpanon ja painaa "tallenna" nappia
    
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa (with note data)
    activate server
    Note right of server: Palvelin vastaanottaa uuden muistiinpanon tiedot ja tallentaa ne
    server-->>browser: 201 Created (JSON with the new note)
    deactivate server
    
    Note right of browser: The browser updates the note list dynamically without reloading the page
    browser->>browser: Update the notes list with the new note

