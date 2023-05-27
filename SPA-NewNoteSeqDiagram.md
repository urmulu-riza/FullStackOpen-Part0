Title Submitting a note in the modern SPA notes application
URL https://studies.cs.helsinki.fi/exampleapp/spa

```mermaid
sequenceDiagram
    Actor r as Riza (Me, The User!)
    participant b as Browser
    participant s as Server

    r->>b: Click Submit
    rect rgb(191, 223, 255)
    b->>b: Create a new note
    b->>b: Add the note to the notes list
    b->>b: Rerender the note list on the page and clear the note input
    end


    rect rgb(200, 150, 255)
    b->>s: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate s

    Note right of b: the new note is sent as JSON data containing both the content of the note (content) and the timestamp (date).
    Note right of b: The Content-Type header of the request tells the server that the included data is represented in JSON format.
    s-->>b: Status code 201 (The request has been fulfilled and has resulted in one or more new resources being created.)
    Note right of b: the server does not ask for a redirect, the browser stays on the same page, and it sends no further HTTP requests.
    deactivate s
    end
```
