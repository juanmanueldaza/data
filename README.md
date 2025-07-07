# data
A repository of data to serve my projects.

> **📁 Part of the daza.ar Ecosystem**: This repository is part of the [daza.ar-env](https://github.com/juanmanueldaza/daza.ar-env) development environment. For local development setup, unified workflow, and cross-site documentation, see the [main repository](https://github.com/juanmanueldaza/daza.ar-env).

---

## Data Schema

### start.json
- `title`: string — Page title
- `meta`: object — Metadata for SEO and social sharing
  - `charset`, `viewport`, `description`, `og`, `twitter`: standard meta tags
- `header`: object — Profile image, name, and role
- `sections`: object
  - `about`: { title, content[] }
  - `funProjects`: { title, projects[] }
    - Each project: { name, description, github, website, preview }
  - `whatDrivesMe`: { title, content }
  - `socials`: { title, links[] }
    - Each link: { platform, url, icon }

### md/
- Markdown files (e.g., `cv.md`, `one-pager.md`) for use in other sites.

---

## Update Process
- Edit JSON or Markdown files directly via PR or commit.
- Validate JSON syntax before pushing.
- For new schema fields, update this README and consuming sites.

---

## Security & API Notes
- If serving via API, ensure CORS headers are set appropriately.
- Rate limit API endpoints to prevent abuse.
- Validate and sanitize any user input if write access is exposed (currently read-only).
- Use access controls for any sensitive or private data (none present by default).

---

## 🏗️ Ecosystem

This data repository is part of the **daza.ar ecosystem**:

- **🛠️ Development Environment**: [daza.ar-env](https://github.com/juanmanueldaza/daza.ar-env) - Unified development setup for all sites
- **📋 Contributing**: Follow the branch workflow in [daza.ar-env/CONTRIBUTING.md](https://github.com/juanmanueldaza/daza.ar-env/blob/main/CONTRIBUTING.md)
- **🎯 Issues & Features**: Use the [feature_improvement.md](https://github.com/juanmanueldaza/daza.ar-env/blob/main/.github/ISSUE_TEMPLATE/feature_improvement.md) template
- **🏗️ Architecture**: See [deployment documentation](https://github.com/juanmanueldaza/daza.ar-env/blob/main/docs/DEPLOYMENT.md) for the full ecosystem architecture

### Sites Using This Data
- **📄 CV Site**: [cv.daza.ar](https://cv.daza.ar) - Imports markdown content from this repository
- **📋 Onepager**: [onepager.daza.ar](https://onepager.daza.ar) - Imports markdown content from this repository
- **🏠 Start Page**: [start.daza.ar](https://start.daza.ar) - Uses start.json configuration
- **📝 Mdsite**: [mdsite.daza.ar](https://mdsite.daza.ar) - Markdown processing utilities
- **🧭 Navbar**: [navbar.daza.ar](https://navbar.daza.ar) - Navigation component
- **🖼️ Wallpapers**: [wallpapers.daza.ar](https://wallpapers.daza.ar) - Wallpaper collection

## License
MIT
