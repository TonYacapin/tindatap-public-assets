# 📱 TindaTap Public Assets & API Configuration

This repository serves as the **serverless configuration backend** for the **TindaTap Android app**.

Instead of hardcoding external resources or publishing a new Google Play Store update whenever a web tool or tutorial changes, the app dynamically fetches JSON configuration files from this repository through GitHub's Raw CDN.

This allows new tools, tutorials, and links to be updated instantly without requiring users to install a new version of the app.

---

# 🔗 Live API Endpoints

The mobile app retrieves its configuration from the following endpoints:

| Configuration | Endpoint |
|---------------|----------|
| **Tools** | `https://raw.githubusercontent.com/TonYacapin/tindatap-public-assets/refs/heads/main/tools.json` |
| **Tutorials** | `https://raw.githubusercontent.com/TonYacapin/tindatap-public-assets/refs/heads/main/tutorials.json` |

---

# 📂 Data Schemas

## tools.json

Controls the **Tools** section inside the TindaTap app.

Each item represents a tool card displayed in the application.

### Schema

```json
[
  {
    "icon": "list-outline",
    "name": "Setup",
    "description": "Set up the TindaTap app so it is ready for your store.",
    "link": "https://tindatap.com/setup"
  },
  {
    "icon": "cash-outline",
    "name": "Presyo",
    "description": "Check the SRP of selected sari-sari store products.",
    "link": "https://tindatap.com/presyo"
  },
  {
    "icon": "barcode-outline",
    "name": "Barcode",
    "description": "Generate barcodes for products that do not have one.",
    "link": "https://tindatap.com/barcode"
  },
  {
    "icon": "pricetag-outline",
    "name": "Sell Price",
    "description": "Calculate a suggested selling price for your products.",
    "link": "https://www.tindatap.com/sellprice/"
  },
  {
    "icon": "calculator-outline",
    "name": "Coster",
    "description": "Calculate recipe costs and determine profitable selling prices.",
    "link": "https://www.tindatap.com/coster/"
  },
  {
    "icon": "create-outline",
    "name": "Signs",
    "description": "Download printable store signs such as 'Ice for Sale'.",
    "link": "https://www.tindatap.com/signs/"
  },
  {
    "icon": "star-outline",
    "name": "Rate TindaTap",
    "description": "Leave a review on Google Play.",
    "link": "https://play.google.com/store/apps/details?id=com.abakus.TindaTap"
  },
  {
    "icon": "globe-outline",
    "name": "Visit Our Facebook Page",
    "description": "Follow TindaTap for updates and announcements.",
    "link": "https://www.facebook.com/share/19GqbgXjYo/"
  }
]
```

### Fields

| Field | Type | Description |
|------|------|-------------|
| `icon` | `string` | Ionicons icon name used inside the app |
| `name` | `string` | Tool title |
| `description` | `string` | Short description shown below the title |
| `link` | `string` | URL opened when the user taps the tool |

---

## tutorials.json

Provides educational videos displayed inside the app.

### Schema

```json
[
  {
    "name": "Getting Started",
    "description": "Learn the basics of using TindaTap and setting up your store.",
    "link": "https://www.youtube.com/watch?v=example1"
  },
  {
    "name": "How to Add Products",
    "description": "Learn how to add and manage products in your inventory.",
    "link": "https://www.youtube.com/watch?v=example2"
  },
  {
    "name": "How to Use Tools",
    "description": "Discover how to use pricing tools, barcode generation, and other features.",
    "link": "https://www.youtube.com/watch?v=example3"
  }
]
```

### Fields

| Field | Type | Description |
|------|------|-------------|
| `name` | `string` | Video title |
| `description` | `string` | Short explanation shown in the app |
| `link` | `string` | YouTube or external video URL |

---

# ⚡ Updating Live App Content

Updating the app's content requires only editing the JSON files.

1. Open `tools.json` or `tutorials.json`.
2. Add, edit, or remove items while keeping the JSON valid.
3. Commit and push the changes to the `main` branch.
4. The app will automatically fetch the latest configuration the next time it starts.

No Play Store update or app recompilation is required.

---

# 🚀 Propagation Time

Changes published to GitHub Raw CDN typically become available worldwide within **1–5 minutes**.

---

# 📌 Notes

- Always ensure the JSON syntax is valid before committing.
- Icon names should use **Ionicons** identifiers supported by the app.
- Every `link` should use a complete HTTPS URL.
- The app gracefully ignores unknown fields, making the schema easy to extend in future updates.
