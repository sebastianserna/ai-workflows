# Contributing

Guidelines for adding and maintaining templates in this repository.

## Project structure

```
ai-workflows/
├── README.md            # Template catalog (main index)
├── CONTRIBUTING.md      # This file
├── LICENSE
└── templates/
    ├── coding/          # Code generation, repo setup, dev workflows
    ├── images/          # Image generation, editing, style transfer
    ├── video/           # Video generation, editing, motion
    ├── audio/           # Audio generation, music, speech, sound design
    ├── 3d/              # 3D modeling, texturing, scene generation
    ├── writing/         # Creative writing, copywriting, documentation
    └── other/           # Miscellaneous and experimental templates
```

## Adding a new template

1. Choose the appropriate category folder inside `templates/`
2. Create a subfolder with a descriptive, kebab-case name (e.g., `react-component-generator`)
3. Include at least a `README.md` with purpose, usage instructions, and examples
4. Add the template to the catalog table in the root [README.md](README.md)

### What a template may include

Each template is a self-contained folder with at minimum a `README.md`. It may also include:

- **Prompt files** (`.md`) — reusable prompts for AI tools
- **Configuration files** — settings, parameters, or presets
- **Examples** — sample inputs/outputs demonstrating expected results
- **`i18n/`** — optional translations (see below)

## Git workflow

All contributions go through pull requests. The `main` branch is protected.

### Branch naming

Use a prefix that describes the type of change:

| Prefix | Use case |
|--------|----------|
| `template/` | New template (e.g., `template/react-starter`) |
| `update/` | Improvements to an existing template |
| `i18n/` | Adding or updating translations |
| `docs/` | Changes to README, CONTRIBUTING, or other docs |
| `fix/` | Bug fixes or corrections |

### Submitting a contribution

1. Create a branch from `main`:
   ```bash
   git checkout -b template/my-new-template
   ```
2. Add or modify templates following the conventions in this guide
3. Commit using [Conventional Commits](https://www.conventionalcommits.org/) in English:
   ```bash
   git commit -m "feat: add react-starter template"
   git commit -m "docs: update catalog with new template"
   git commit -m "fix: correct prompt formatting in compass"
   ```
4. Push and open a pull request against `main`:
   ```bash
   git push -u origin template/my-new-template
   ```
5. In the PR description, include:
   - What the template does and who it's for
   - A brief example of expected usage
   - Whether i18n translations are included

### PR checklist

Before requesting review, make sure:

- [ ] Template has a `README.md` with purpose and usage instructions
- [ ] Template is listed in the root [README.md](README.md) catalog table
- [ ] Template is listed in the corresponding category README
- [ ] File and folder names use kebab-case
- [ ] All content is in English (translations go in `i18n/`)

## i18n conventions

- The default language for all templates is **English**.
- Each template may optionally include its own translations inside an `i18n/` subfolder within the template root.
- Translations are managed per-template, not globally. A template without an `i18n/` folder is English-only.

Example:

```
templates/coding/some-template/
├── README.md          # Main description (English)
├── prompt.md          # Base prompt (English)
└── i18n/
    ├── es.md          # Spanish translation
    └── pt.md          # Portuguese translation
```
