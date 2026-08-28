# UI Element Catalog

Catalog of discovered, relevant UI elements. Populated/updated by `VisualQAAgent`. Do not invent elements before they exist in the frontend.

| Element ID | Page | Component | Type | Label | Selector/Identifier | Purpose | Expected Action | Expected Result | Related Feature | Related API | Validation | Error Behavior | Loading Behavior | Accessibility | Responsive Behavior | Test Status | Last Tested | Known Issues |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CHAT-INPUT-001 | Chat | MessageInput | textarea | Message input | `data-testid="chat-input"` | Compose a message | Type text | Text appears, send enabled | FEAT-003 | POST /chat | Non-empty, max length | Inline validation message | n/a | `aria-label="Message"` | Full width on mobile | Pending | | |
| CHAT-SEND-001 | Chat | MessageInput | button | Send | `data-testid="chat-send"` | Submit the message | Click / Enter | Message sent, appended to history | FEAT-003 | POST /chat | Disabled when input empty/loading | Disabled + tooltip on error | Spinner while awaiting response | `aria-label="Send message"` | Touch target ≥44px | Pending | | |
| CHAT-RETRY-001 | Chat | MessageList | button | Retry | `data-testid="chat-retry"` | Retry a failed message | Click | Re-sends last failed message | FEAT-003 | POST /chat | Only shown on error state | Shows error toast on repeat failure | Spinner while retrying | `aria-label="Retry sending message"` | n/a | Pending | | |
| UPLOAD-FILE-001 | Upload | UploadPanel | file input | Choose file | `data-testid="upload-file-input"` | Select a document to upload | Click / file picker | File selected, name shown | FEAT-002 | POST /upload-document | Type/size checked client-side | Inline error for invalid file | n/a | `aria-label="Choose document"` | n/a | Pending | | |
| UPLOAD-SUBMIT-001 | Upload | UploadPanel | button | Upload | `data-testid="upload-submit"` | Submit the selected document | Click | Upload begins, progress shown | FEAT-002 | POST /upload-document | Disabled until a file is selected | Error banner on failure | Progress indicator | `aria-label="Upload document"` | n/a | Pending | | |
| NAV-HOME-001 | Global | NavBar | link | Home | `data-testid="nav-home"` | Navigate to home/landing | Click | Navigates to `/` | n/a | n/a | n/a | n/a | n/a | Keyboard-focusable link | Collapses to menu on mobile | Pending | | |
| NAV-CHAT-001 | Global | NavBar | link | Chat | `data-testid="nav-chat"` | Navigate to chat page | Click | Navigates to `/chat` | FEAT-003 | n/a | n/a | n/a | n/a | Keyboard-focusable link | Collapses to menu on mobile | Pending | | |

*(Additional rows are added by VisualQAAgent as real UI elements are discovered/built.)*
