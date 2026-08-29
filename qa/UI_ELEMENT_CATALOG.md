# UI Element Catalog

Catalog of discovered, relevant UI elements. Populated/updated by `VisualQAAgent`. Do not invent elements before they exist in the frontend.

| Element ID | Page | Component | Type | Label | Selector/Identifier | Purpose | Expected Action | Expected Result | Related Feature | Related API | Validation | Error Behavior | Loading Behavior | Accessibility | Responsive Behavior | Test Status | Last Tested | Known Issues |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CHAT-INPUT-001 | Chat | MessageInput | input | Chat message | `role="textbox"`, `aria-label="Chat message"` | Compose a message | Type text | Text appears, send enabled | FEAT-003 | POST /chat | Non-empty, max length | Inline validation message | n/a | Accessible textbox name observed | Within viewport at 390px | Pass (targeted) | 2026-08-29 | | |
| CHAT-SEND-001 | Chat | MessageInput | button | Send | button text `Send` | Submit the message | Click / Enter | Message sent, appended to history | FEAT-003 | POST /chat | Disabled when input empty/loading | Error message remains visible after failure | `...` appears while request is in flight | Button accessible by role/name; keyboard activation observed | Within viewport at 390px | Pass | 2026-08-29 | | |
| UPLOAD-FILE-001 | Upload | UploadPanel | file input | Choose file | file chooser control | Select a document to upload | Click / file picker | File selected, name shown | FEAT-002 | POST /upload-document | Type/size checked client-side | Inline error for invalid file | n/a | Choose File control observed | Usable in mobile viewport | Pass | 2026-08-29 | | `.json` rejected with allowed-type message |
| UPLOAD-SUBMIT-001 | Upload | UploadPanel | button | Upload knowledge document | button text `Upload knowledge document` | Submit the selected document | Click | Upload begins, progress shown | FEAT-002 | POST /upload-document | Disabled until a file is selected | Error banner on failure | Upload completion status observed | Button accessible by name | Usable in mobile viewport | Pass (valid path) | 2026-08-29 | | |
| NAV-HOME-001 | Global | NavBar | link | Home | not observed | Navigate to home/landing | Click | Navigates to `/` | n/a | n/a | n/a | n/a | n/a | Not observed | Not observed | Not Run | | |
| NAV-CHAT-001 | Global | NavBar | link | Chat | not observed | Navigate to chat page | Click | Navigates to `/chat` | FEAT-003 | n/a | n/a | n/a | n/a | Not observed | Not observed | Not Run | | |

*(Additional rows are added by VisualQAAgent as real UI elements are discovered/built.)*
