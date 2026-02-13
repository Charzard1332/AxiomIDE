# Changelog

All notable changes to AxiomIDE are documented in this file.

## [1.0.0] - 2026-02-13

### Added
- Initial AxiomIDE release with custom desktop shell, top chrome, side rails, status chips, and tool window system.
- Startup flow with animated splash screen and project wizard-first launch experience.
- Project Wizard with:
  - Java and C# project creation.
  - Multiple templates (console, library, Swing, WinForms).
  - Framework selection and runtime checks.
  - Optional Git init, README, .gitignore, and test scaffolding.
  - Recent projects, quick search, and command-style launch actions.
- Project scaffolding engine for Java and .NET layouts, including WinForms starter files and test project generation.
- Project model detection for Gradle/C# projects and source roots.
- Full file explorer with hidden-folder filtering and project watcher refresh.
- Multi-tab code editing experience using RSyntaxTextArea.
- Integrated terminal panel and command execution from within the IDE.
- Run/build workflow:
  - Java compile/run flow.
  - C# dotnet build/run flow.
  - Run configuration management (create/select/remove/activate).
- LSP integration via LSP4J (startup, reconnect, diagnostics, completion, signature help, save/open/change notifications).
- Diagnostics UI pipeline:
  - Problems output.
  - Inline highlights and gutter indicators.
  - Hover/click diagnostic navigation.
- Completion/signature UX, fallback C# completion path, and debounce handling.
- Command palette and advanced navigation:
  - Global command palette.
  - Go to file.
  - Project-wide symbol index and filtering.
- WinForms Designer with:
  - Toolbox, hierarchy, property editing, event handler mapping.
  - Grid/snap, alignment/distribution tools, duplication, undo/redo, keyboard shortcuts.
  - Designer/source code synchronization and save pipeline.
- Persistent workspace metadata (layout/recent/opened state) under `.axiomide` project storage.
- FlatLaf-based visual theme customization and startup UI theming.

### Changed
- Standardized build setup to Java 21 toolchain and UTF-8 defaults.
- Unified startup to launch wizard/splash before opening the main IDE frame.

### Dependencies
- FlatLaf `3.6`
- RSyntaxTextArea `3.4.0`
- Eclipse LSP4J `0.23.1`

### Notes
- This is the first stable major release of AxiomIDE.
- Focus of v1 is foundation quality: editor workflow, project creation, language services, and desktop design tooling.
