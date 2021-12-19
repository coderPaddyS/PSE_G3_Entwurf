```mermaid
    classDiagram
        Search --> SearchView
        Search --> Datenbank
        Cursor <-- Datenbank
        CursorAdapter --> Cursor
        SearchView --> CursorAdapter
```