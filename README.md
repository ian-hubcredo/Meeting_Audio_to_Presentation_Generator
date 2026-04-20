# Fireflies to Gemini to Gamma

## Overview

This automation **turns meeting recordings into professional presentations automatically**. It uploads audio to Fireflies.ai for transcription, structures the meeting notes (summary, key topics, action items, transcript highlights), and sends them to Gamma.app to generate a polished presentation deck. The result is a ready-to-share PPTX file created from your meeting content without any manual work.

## How It Works

```
Webhook (audio URL) -> Fireflies Upload -> Structure Meeting Data -> Gamma Create Presentation -> Poll Until Complete
```

### Workflow Diagram

```mermaid
flowchart TD
    A["Webhook\nAudio URL + title"] --> B["Fireflies API\nUpload audio"]
    B --> C["Structure Data\nFormat meeting notes"]
    C --> D["Gamma API\nCreate presentation"]
    D --> E["Extract Generation ID"]
    E --> F["Wait"]
    F --> G["Check Status"]
    G --> H{"Complete?"}
    H -- "No" --> F
    H -- "Yes" --> I["Presentation Ready\nPPTX + Gamma URL"]

    style A fill:#1B3A4B,color:#fff
    style B fill:#2C5F7C,color:#fff
    style C fill:#3D5A80,color:#fff
    style D fill:#4A6D7C,color:#fff
    style I fill:#274C36,color:#fff
```

## Integrations

- **Fireflies.ai** - Meeting audio transcription and analysis
- **Gamma.app** - AI-powered presentation generation

## Setup

1. Import `Fireflies_Gemini_Gamma.json` into your n8n instance.
2. Update the Fireflies API key and Gamma API credentials.
3. Activate the workflow and send a POST with audio URL and meeting title.
