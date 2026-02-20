# Changelog

All notable changes to AxiomIDE are documented in this file.

## [1.2.1] - 2026-02-19

### Added
- Extension activity-bar contribution support improvements:
  - Extension-contributed activity entries now appear reliably in the far-left sidebar.
  - Contributed activity items open dedicated dockable tool windows.
  - Added icon loading pipeline for contributed activity icons with safe fallback glyph rendering.
- Version Control productivity upgrades:
  - Staged/unstaged/untracked/conflict file tree with per-file actions (`Stage`, `Unstage`, `Discard`, `Open Diff`).
  - Inline diff preview pane that updates live when selecting a file in the changes tree.
  - Commit Composer panel with:
    - Required commit message validation.
    - `Amend` and `Sign-off` toggles.
    - `Commit Staged` and `Commit + Push` actions.
    - Collapsible `Show/Hide` behavior for more vertical workspace.
- Git status decorations in explorer and editor tabs:
  - File-level status badges/colors in project tree.
  - Open-tab status badges/icons with dirty-state integration.
- Floating Version Control window workflow:
  - Large undocked VCS window for full-screen style review/commit work.
  - `Dock Back` action in floating header.
  - Stable dock/undock behavior for left-side tool windows.
- JavaScript language support
  - NodeJS project creation
  - TypeScript language support using `typescript-language-server`

### Changed
- Extensions panel marketplace layout reworked for usability:
  - Replaced cramped marketplace column layout with split-pane based sizing.
  - Increased visible space for marketplace result list and package details/docs.
  - Improved default divider sizing so marketplace content is readable on open.
- Version Control panel layout reworked for usability:
  - Changes tree promoted as primary area.
  - Repo section made collapsible (`Show Repos` / `Hide Repos`).
  - Commit composer and summary sections rebalanced to avoid cramped rendering.
- VCS summary refresh behavior improved:
  - Preserves manual scroll position during live auto-refresh.
  - Stops forced scroll jumps while reviewing output/history.
- IntelliSense trigger behavior tuned for responsiveness:
  - Auto-complete now only opens in meaningful contexts (member access or identifier prefix length >= 2).
  - Removed noisy auto-trigger patterns that opened suggestions unexpectedly.
  - Reduced completion request churn via trigger filtering and debounce adjustments.

### Fixed
- Marketplace VSIX installation now handles HTTP redirects (`301`, `302`, `303`, `307`, `308`) instead of failing on redirect responses.
- Fixed extension activity fallback icon rendering by adding missing glyph icon implementation used by rail buttons.
- Fixed multiple Version Control UI overlap/collapse issues in constrained layouts and floating mode.
- Fixed stale/incorrect VCS status visuals by clearing/repainting status maps in no-project/no-repo/refresh-failure states.
- Reduced autocomplete lag caused by over-eager silent completion triggering.

## [1.1.0] - 2026-02-18

### Added
- C# semantic highlighting pipeline powered by LSP semantic tokens:
  - Full, range, and delta token request support.
  - Token legend-aware coloring with modifier-sensitive styling.
  - Editor viewport-aware refresh and debounced updates while typing.
- Semantic highlighting controls:
  - `View -> Toggle Semantic Highlighting`.
  - Command Palette action: `View: Toggle Semantic Highlighting`.
- C# quick-fix workflow:
  - `Ctrl+.` invokes LSP code actions popup with keyboard and mouse apply.
  - Workspace edit execution with resource operation support (`CreateFile`, `RenameFile`, `DeleteFile`).
- Run/build preflight save pipeline:
  - Save-all dirty editors before Run, Build, startup actions, and run configuration execution.
  - Clear run cancellation messaging when save fails.

### Changed
- Improved completion UX and relevance:
  - Better ranking and stale-request suppression.
  - Completion resolve support for richer details/documentation.
  - Auto-import metadata surfaced in completion docs and rows.
- Improved semantic rendering style to use subtle tint overlays instead of heavy fills.
- Persisted semantic highlighting preference in workspace layout and applied it on layout load for open C# editors.

### Fixed
- Prevented repeated LSP shutdown noise during restart by hardening stop lifecycle behavior.
- Fixed semantic highlight cleanup when editors close or language services are detached.
- Ensured `.cs`/`.Designer.cs` edits are flushed to disk before execution paths that build/run project code.

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
