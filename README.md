# EnvKeys

A master library for creating, updating, and managing `envkeys.json` files to standardize environment variables across software development projects. Modeled after the popular [github/gitignore](https://github.com/github/gitignore) repository, EnvKeys provides templates for `envkeys.json` files organized by categories like operating systems, languages, shells, and stacks. It aims to establish a standard convention for environment variables, similar to an RFC for `.env` files, while incorporating linting and validation best practices.

## Why EnvKeys?

Inspired by the challenges outlined in the project description, EnvKeys addresses:
- **Standardization**: Drawing from existing .env conventions (e.g., [Smartmob RFC for .env](http://smartmob-rfc.readthedocs.io/en/latest/2-dotenv.html)<grok:render card_id="f78e2a" card_type="citation_card" type="render_inline_citation">
<argument name="citation_id">0</argument>
</grok:render> and [DotEnv RFC draft](https://github.com/radprogrammer/dotenv-RFC)<grok:render card_id="cadfb9" card_type="citation_card" type="render_inline_citation">
<argument name="citation_id">6</argument>
</grok:render>), we propose a JSON-based structure for better hierarchy and validation.
- **Linting and Validation**: Integrate tools like [dotenv-linter](https://dotenv-linter.github.io/)<grok:render card_id="8c7a16" card_type="citation_card" type="render_inline_citation">
<argument name="citation_id">16</argument>
</grok:render> (for checking duplicates, formatting) and [envalid](https://github.com/af/envalid)<grok:render card_id="774a9b" card_type="citation_card" type="render_inline_citation">
<argument name="citation_id">21</argument>
</grok:render> for runtime validation in Node.js.
- **Growth and Community**: Like gitignore, templates can grow with community contributions, covering more systems and software families.
- **Scripts and Tools**: Includes scripts like `check-env.sh`, `create-env.sh`, `INSTALL.sh`, and `create-project.sh` to manage `.env` files based on `envkeys.json` templates.
- **Security**: Emphasizes handling sensitive data, with warnings about not committing `.env` files (see [best practices](https://www.getfishtank.com/insights/best-practices-for-committing-env-files-to-version-control)<grok:render card_id="6073d4" card_type="citation_card" type="render_inline_citation">
<argument name="citation_id">13</argument>
</grok:render>).

## Features

- **Template-Based**: Pre-defined `envkeys.json` templates for Linux, Node.js, Bash, JavaScript, and fullstack (Node+React) development.
- **Hierarchical Structure**: `KEY-master` with metadata and child `keys` including validation rules (regex, type).
- **Linting Integration**: Planned support for .env linting using tools like dotenv-linter.
- **Conversion Tools**: Scripts to generate `.env` from `envkeys.json`.
- **Monorepo Design**: Organized directory structure for easy extension.

## Directory Structure

The project is designed as a monorepo to accommodate growth, with templates categorized similarly to gitignore (root for common, global for OS/tools, community for specialized). Each parent (e.g., OS, language) has its own template file. Here's the proposed structure:

```
EnvKeys/
├── README.md                  # Project overview and usage
├── LICENSE                    # MIT License
├── CONTRIBUTING.md            # Guidelines for contributions (TBD)
├── templates/                 # Core templates, like gitignore files
│   ├── global/                # System-wide/OS/shell templates (like gitignore's Global)
│   │   ├── linux.json         # Linux-specific env vars (e.g., USER, HOME, PATH)
│   │   └── bash.json          # Bash shell env vars (e.g., PS1, SHELL)
│   ├── languages/             # Language-specific (root/common in gitignore)
│   │   ├── node.json          # Node.js env vars (e.g., NODE_ENV, PORT)
│   │   └── js.json            # JavaScript env vars (general, overlaps with Node)
│   └── stacks/                # Framework/stack-specific (like gitignore's Community)
│       └── fullstack-node-react.json  # Fullstack env vars (e.g., REACT_APP_*, DATABASE_URL)
├── scripts/                   # Utility scripts for managing env
│   ├── check-env.sh           # Validate .env against envkeys.json
│   ├── create-env.sh          # Generate .env from envkeys.json
│   ├── INSTALL.sh             # Setup script for the project
│   └── create-project.sh      # Scaffold new project with env setup
├── docs/                      # Documentation
│   ├── rfc.md                 # Proposed RFC for envkeys.json standard
│   ├── naming-conventions.md  # Guidelines for variable naming
│   └── validation.md          # How to use linting/validation
├── examples/                  # Sample merged envkeys.json files
│   └── linux-node-fullstack.json  # Combined template for user's system
├── lint/                      # Linting configurations
│   └── dotenv-linter-config.yaml  # Config for dotenv-linter integration
└── tests/                     # Tests for scripts and validation (TBD)
```

This structure allows:
- **Extensibility**: Add new templates under categories as the project grows (e.g., add `windows.json` under global/).
- **Monorepo Benefits**: Single repo for all templates, scripts, and docs.
- **Parent Templates**: Each category (parent) has a dedicated JSON template.

## Example `envkeys.json`

See the provided artifact for a combined `envkeys.json` focused on Linux, Node, Bash, JS, and Fullstack. It incorporates common variables from research (e.g., [Linux env vars](https://www.geeksforgeeks.org/linux-unix/environment-variables-in-linux-unix/)<grok:render card_id="a3e43f" card_type="citation_card" type="render_inline_citation">
<argument name="citation_id">33</argument>
</grok:render>, [Node.js env vars](https://nodejs.org/en/learn/command-line/how-to-read-environment-variables-from-nodejs)<grok:render card_id="255757" card_type="citation_card" type="render_inline_citation">
<argument name="citation_id">25</argument>
</grok:render>, [Fullstack examples](https://medium.com/%40damarakeswar/environment-variables-in-react-and-node-js-the-complete-guide-e2f475be35cc)<grok:render card_id="da1521" card_type="citation_card" type="render_inline_citation">
<argument name="citation_id">51</argument>
</grok:render>).

## Getting Started

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/DavitTec/EnvKeys.git
   cd EnvKeys
   ```

2. **Use a Template**:
   Copy a template (e.g., `templates/global/linux.json`) to your project as `envkeys.json` and customize.

3. **Generate .env**:
   ```bash
   ./scripts/create-env.sh envkeys.json > .env
   ```

4. **Validate**:
   Use integrated linter: `dotenv-linter .env` (install via Rust cargo).

## Contributing

Welcome! Follow gitignore's model: One template per PR, provide docs/links. See CONTRIBUTING.md (TBD).

## License

MIT License - see [LICENSE](LICENSE).

## Contact

[DavitTec GitHub](https://github.com/DavitTec) | [LinkedIn](https://linkedin.com/in/davit).