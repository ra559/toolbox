# Toolbox

A centralized dashboard for discovering, searching, and launching a collection of lightweight web-based tools and applications.

Toolbox provides a single starting point for accessing utilities developed for everyday productivity, development, Linux administration, email troubleshooting, and other technical tasks.

Built with HTML5, CSS3, and vanilla JavaScript, the application dynamically loads its tool catalog from a JSON configuration file.

## Features

### 1. Centralized Tool Directory

Display all registered applications in a responsive card-based interface.

Each tool entry includes:

- Tool identifier.
- Application name.
- Description.
- Version number.
- Direct link to launch the application.

The dashboard automatically generates cards from the tool catalog.

### 2. Dynamic JSON Catalog

Applications are registered in `tools.json`.

This separates application data from the presentation and rendering logic.

Example:

```json
{
  "tools": [
    {
      "id": "001",
      "name": "Email Toolbox",
      "description": "A collection of browser-based email utilities.",
      "version": "1.0.0",
      "url": "https://example.com/email-toolbox/"
    }
  ]
}
```

To add another application, add a new object to the `tools` array.

No changes to the dashboard's rendering code are necessary.

### 3. Search Functionality

Find applications using the built-in search field.

Search matches against:

- Application name.
- Description.
- Tool identifier.
- Version number.

Results update dynamically as the user types.

If no applications match the search, an appropriate empty-state message is displayed.

### 4. Responsive Interface

The dashboard adapts to different screen sizes.

- Three-column layout on larger screens.
- Two-column layout on medium screens.
- Single-column layout on mobile devices.
- Responsive application cards.
- Flexible search interface.

### 5. Terminal-Inspired Design

The interface uses a terminal-inspired visual identity.

Features include:

- Dark background.
- Terminal-green accents.
- Monospaced JetBrains Mono typography.
- Terminal window decoration.
- Command-line-inspired headings.
- Subtle grid background.
- Interactive pointer-following glow.
- Application status indicators.

### 6. Additional Features

- Application count.
- Catalog loading status.
- Error handling when the JSON catalog cannot be loaded.
- Accessible search labeling.
- Reduced-motion support.
- Secure external links using `noopener noreferrer`.

## Technology Stack

| Technology | Purpose |
|---|---|
| HTML5 | Application structure |
| CSS3 | Layout, responsive styling, and visual effects |
| Vanilla JavaScript | Catalog loading, rendering, and searching |
| JSON | Application catalog |
| Fetch API | Loading the external JSON catalog |
| JetBrains Mono | Terminal-inspired typography |

No JavaScript frameworks, package managers, backend services, or databases are required.

## Getting Started

### Requirements

- A modern web browser.
- A local or hosted HTTP server.
- Internet connection to load JetBrains Mono from Google Fonts.

The application uses the browser Fetch API to retrieve `tools.json`. Opening `index.html` directly through the `file://` protocol may prevent the catalog from loading.

### Installation

Clone the repository:

```bash
git clone https://github.com/ra559/toolbox.git
```

Navigate into the project directory:

```bash
cd toolbox
```

### Running Locally

Use Python's built-in HTTP server:

```bash
python3 -m http.server 8000
```

Open the dashboard:

```text
http://localhost:8000
```

The application will automatically load the catalog from `tools.json`.

## Adding Applications

Adding an application requires only an update to `tools.json`.

1. Open `tools.json`.
2. Locate the `tools` array.
3. Add a new application object.
4. Provide a unique identifier, name, description, version, and URL.
5. Save the file and refresh the dashboard.

Example:

```json
{
  "id": "008",
  "name": "My New Tool",
  "description": "A description of my new application.",
  "version": "1.0.0",
  "url": "https://example.com/my-new-tool/"
}
```

The dashboard automatically generates the corresponding application card.

## Project Structure

```text
toolbox/
├── .github/
│   └── workflows/
├── index.html
├── tools.json
└── README.md
```

| File / Directory | Description |
|---|---|
| `.github/workflows/` | GitHub Actions workflows |
| `index.html` | Dashboard interface, styling, and JavaScript logic |
| `tools.json` | Application catalog |
| `README.md` | Project documentation |

## Architecture

Toolbox follows a simple data-driven architecture.

```text
              Toolbox Dashboard
                      |
                      v
               Fetch tools.json
                      |
                      v
                Parse JSON
                      |
                      v
              Store catalog data
                      |
                      v
              Render application cards
                      |
                      v
              Search and filter tools
                      |
                      v
               Launch application
```

The separation between the catalog and rendering logic makes the application easy to maintain and extend.

## Error Handling

The dashboard handles common catalog-loading problems.

- HTTP errors when retrieving `tools.json`.
- Invalid JSON responses.
- Missing or invalid `tools` arrays.
- Empty application catalogs.
- Searches that return no matching applications.

When the catalog cannot be loaded, the dashboard displays an error message instead of silently failing.

## Privacy

Toolbox does not require accounts, authentication, or a backend service.

The application retrieves its catalog and renders it locally in the browser.

Search operations are performed locally against the loaded catalog. No search queries are submitted to an external service.

## Deployment

Toolbox can be hosted as a static website.

Suitable hosting options include:

- GitHub Pages.
- Nginx.
- Apache HTTP Server.
- Any static web hosting provider.

For GitHub Pages, publish the repository using the repository's Pages configuration.

## Contributing

Contributions, bug reports, and feature suggestions are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Add or improve an application entry.
4. Verify that the JSON remains valid.
5. Test the dashboard locally.
6. Submit a pull request.

When adding applications, use unique identifiers and provide accurate descriptions and working URLs.

## License

No license file is currently present in the repository. All rights are otherwise reserved by default unless the project owner specifies a license.

---

**Repository:** https://github.com/ra559/toolbox