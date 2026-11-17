# Changelog

What is new in each Tinycast Lite release. The update window shows the section of the version it
offers.

## 1.2.0

### Changes

- **An app's shortcut now cycles its windows instead of hiding it.** Pressed while the app is already in front, it brings forward the app's next window, going through all of them in turn; with a single window it does nothing. Minimized windows are skipped, and cycling needs the Accessibility permission.
- **Updates now come from [olegy/apps-dist](https://github.com/olegy/apps-dist), a public repository of builds.** Copies of 1.1.0 and older still look in the old place and never see this release: install it once by hand from a `tinycast-<version>` release there, and updates work as before from then on.
- **App shortcuts restore as a row of their own, Applications, with Merge.** Merge keeps this Mac's app shortcuts and adds the backup's; Restore replaces them. In both, a shortcut for an app this Mac does not have is left out, so it no longer takes the chord from an app here that uses the same one.

## 1.1.0

### Changes

- **A backup is now your whole setup in one encrypted file.** Export no longer has anything to tick: it always saves everything, now including installed extensions with their data, custom Quick Actions and scripts, every shortcut, all AI settings with connections and MCP servers, and the API keys, tokens and sign-ins kept in the Keychain. Because of those, an export asks for a password of at least eight characters and writes an encrypted `.tinycastenc` file; without the password it cannot be opened, and Tinycast does not keep it. AI chats are not included. An extension that contains symbolic links is left out and named after the export. The Export Backup and Import Backup commands now open Settings → Backup.
- **Restore from a backup, section by section.** In Settings → Backup choose a `.tinycastenc` file and enter its password to see what it holds in eleven rows: General Settings, Launcher Learning, Shell Commands, Quicklinks, Apple Shortcuts, Leader Key Groups, Clipboard History, File Search, AI, Quick Actions and Extensions. Untick what should stay as it is. Restore makes a section exactly what the backup holds, its switch and settings included; Merge, offered where a section is a list of your own items, only adds the backup's items to yours and updates the ones both have, while the section's switch and settings stay as they are here, and so does each item's own on/off, so something turned off on this Mac stays off. If a restored shortcut is already used by something else here, the restored one keeps it. Snippets folders, File Search scopes and extension search paths that do not exist on this Mac are left out. Import asks once, writes the sections and relaunches.
- **Leader Key and Status Icons sit under Launcher in Settings**, after Fallbacks, instead of under Features.
- **Built-in actions have a Settings pane of their own.** Settings → Built-in Actions holds Enable Built-in Actions and Tinycast's own commands that no other pane lists, such as Define Word, Open Camera, Check for Updates and Quit. Your own scripts are now called Shell Commands, in the launcher and in Settings → Shell Commands, which holds only them and is laid out like Quicklinks: the switch, then Create Shell Command and Search Shell Commands, then your commands with Add Shell Command below.
- **Settings → AI, Extensions and Quick Actions lose the heading above their switch**, which only repeated the pane's name.
- **Confetti moved from System Actions to Built-in Actions.** A shortcut, alias or favorite set on it before has to be set again.

### Removed

- **Tinycast now speaks English, German and Russian only.** Spanish, French, Japanese, Korean, Portuguese and Simplified Chinese are gone from the interface and from emoji search keywords; a Mac set to one of them shows Tinycast in English.
- **Import Quicklinks and Export Quicklinks** are gone, both the launcher commands and the rows in Settings → Quicklinks. Quicklinks travel in a backup with everything else.
- **Older `.tinycast` backups can no longer be imported.** The unencrypted format and its three import categories are gone; export again from a copy that still has the setup.
- **Sync settings file** is gone: Settings → Backup no longer mirrors preferences into `~/.config/tinycast/settings.json`, and Tinycast neither reads nor writes that file. It carried preferences and built-in shortcuts but no custom commands, quicklinks or Quick Actions, so it could not be relied on to move a setup between Macs; a backup is the one way to do that. An existing file stays on disk and can be deleted.

## 1.0.0

Tinycast Lite now has its own version numbers, starting here, instead of the version of the Tinycast it was based on plus a Lite revision. A copy older than 1.0.0 does not see this release: install it once by hand, and updates work as before from then on.

### New

- **Leader Key.** A new mode runs a launcher entry by typing its alias, with no search and no ↵. Bind a shortcut to the Leader Key command in Settings → Leader Key, press it, then press a key: an entry with a one-character alias runs at once. For two-key sequences add a group there, a key and a name: group t gathers the entries whose alias is t plus one more character, so the shortcut, then t, then c runs the entry aliased tc. Rows are listed by key, arrows select, ↵ or a click runs the row, Backspace goes up a level, and Escape returns to the first level and then closes. An entry hidden from root search, by its launcher checkbox, by Show in root search on a quicklink or custom command, or by a pane's Show in launcher switch, still runs here and keeps its alias field editable, so a sequence does not need a row in root search. A key that needs ⌥ to type, such as one a remapper produces, works too. Aliases keep working in root search as before, and groups never appear there.
- **Script Actions.** A Quick Action can now be a small piece of JavaScript instead of a prompt: it gets the text as `text` and what it returns replaces it, on this Mac, with no model and no network. Add one in Settings → Quick Actions → Script Actions, which starts with seven examples (quotes, brackets, Markdown code, sentence case, whitespace, em dashes) left out of the launcher until you tick them. A script replaces the selection at once, with no screen; with nothing selected it transforms the clipboard and pastes the result at the cursor. A script that runs longer than two seconds is stopped.
- **Run a Quick Action with or without a preview.** Each list in Settings → Quick Actions has a Default action: Run puts the result straight back, Run with Preview opens the Quick Action screen first. Scripts start on Run, AI actions on Run with Preview. ↵ and the action's shortcut use the default, ⌘↵ runs it the other way, and ⌘K lists both. Summarize always previews.
- **Test a Quick Action.** ⌘T on a Quick Action in the launcher, or the ▶ button beside it in Settings, opens it on an empty text: type something, press ↵ and see what comes back, without touching a selection or the clipboard.

- **Hide pasted entries (experimental).** Turn it on in Settings → Clipboard and an entry you paste from Clipboard History, or with Paste Sequentially, leaves the main list instead of jumping to its top, so what is left is what you have not pasted yet. Paste and Keep Window Open (⌥↵) does the same and moves on to the next entry, so repeating it pastes a run. With the search field empty, → shows the Pasted list and ← brings back the main list; search still finds everything, and copying a pasted entry brings it back. Paste Sequentially then skips what was already pasted. An entry you paste with ⌘V in another app moves to Pasted as well: Tinycast only notices the keystroke, never reads or changes it, and needs the Accessibility permission it already uses for pasting.

- **Quick Actions on a Clipboard History entry.** Press Tab on a text entry in Clipboard History to pick a Quick Action for it: the action opens at once with that text, with no selection or clipboard read. Backspace or Esc goes back a step, and pasting or copying the result counts the entry as pasted.

### Changes

- **Quick Actions settings list AI actions and scripts apart.** Script Actions come first, AI Actions (the built-in four and your own prompts) below, each with its own Add button.
- **An ellipsis marks a Quick Action that opens its screen.** In the launcher an action whose ↵ runs with a preview ends in “…”, as Fix Grammar… does out of the box; one that puts its result straight back does not.
- **Clipboard History keeps one entry per copy.** Copy a text or a file that is already in the recent history and its entry moves back to the top instead of a second one appearing; with Hide pasted entries on, that also brings it back from Pasted. Spaces and line breaks around a text do not count as a difference, a pinned entry stays where it is, and images are not compared. Duplicates you already have stay until they age out.
- **About shows the license alone.** The line at the bottom reads Released under AGPL-3.0; credits are in the repository.
- **A new app icon.** Tinycast Lite has its own icon in the Dock, About and the update window: an orange bolt on a blue plate. The menu bar icon is unchanged.
- **A shortcut opens its screen with nothing behind it.** Press a command's shortcut while the palette shows another screen and the new screen replaces it instead of stacking on top: Escape closes the palette and the header shows no back arrow. The same goes for a link and for an entry run from Leader Key. A screen opened from a row in root search still goes back to the search.
- **The launcher shortcut only shows and hides the palette.** On any screen it now hides the palette instead of first jumping to the root search; use Escape or Backspace to go back. Hidden from a screen other than the root search, the palette brings that screen back if you reopen it within Pop to Root Search, as after clicking away.
- **Tab only opens Quick AI.** From the launcher, Tab still asks Quick AI what you typed; it no longer moves on from Quick AI to Clipboard History or from Clipboard History back to the launcher. Use Escape or Backspace to go back.

### Removed

- **Import Raycast Scripts** is gone from Settings → Commands, with the import of Raycast script command folders behind it. Commands imported earlier stay as they are.

### Fixes

- **Clipboard History has one Paste.** Text was always pasted as plain text, so Paste as Plain Text and the Default action setting are gone: ↵ pastes and ⌘↵ copies. A file entry keeps the second way as Paste Path (⌃⌘↵), which pastes its path instead of the file.
- **A Quick Action no longer takes the current line for a selection.** In Obsidian, VS Code and other editors that copy the whole line when nothing is selected, the action now opens on the clipboard, as everywhere else. With the palette open, the selection in Electron apps is now read directly, without a copy.
- **A Quick Action opens from the launcher without the palette blinking.** The palette used to hide while the selected text was fetched from apps that only give it up through a copy, such as Electron apps, and with nothing selected it stayed away for over a second while the app beeped. It now stays in place, skips the copy when the app's Copy command is disabled, and waits far less when nothing comes back.
- **⌘K opens Actions on the Quick Action screen**, while you edit the text, while it runs and after it finishes or fails; closing the menu puts the caret back in the text.

## 0.12.8-lite.5

### New

- **Status Icons.** Small emoji at the right of the launcher's search field show a state that changes on its own, so its menu-bar item can go. The first one is DNS: 🔒 while every DNS server is local (for example dnscrypt-proxy on 127.0.0.1), 🌐 while one is your provider's, 🤷 when there is none; hover shows the addresses, and a click can run one of your Custom Commands. Turn it on in Settings → Status Icons.
- **Custom Commands can offer options.** Turn on **Lists options** and the command, run without `$1`, prints its choices; the palette lists them on its own screen, and the one you pick runs the command again with it as `$1`. The first line above `---` becomes the search field's prompt, an optional second line shows at the left of the bottom bar, and each option can be dimmed, preselected, given a subtitle and an icon, or keep the palette open and refresh the list after it runs. One `eject` or `vmount` script now replaces a command per volume.

### Changes

- **Shorter bottom-bar labels.** The bottom bar names the action with a verb alone where the selected row already says what it acts on: Copy, Open, Run, Save, Create, Activate, Uninstall. The ⌘K menu keeps the full names.
- **Snippets show Paste in the bottom bar.** A one-line snippet now shows Paste ⌘↵ beside Copy, so it is clear that it can be pasted.
- **Quick AI ⇥ moved to the bottom bar**, next to the other actions, instead of sitting at the right of the search field.
- **The back chevron shows only when there is a screen to go back to.** A screen opened straight by its hotkey no longer shows it, since Escape there closes the palette.
- **A leaner Clipboard History.** The details under the preview drop the Information header and the Source and Words rows, and the bottom bar shows how many entries are listed. The history no longer records which app each entry was copied from, and the record already kept is erased on first launch.
- **Snippets show how many are listed** at the left of the bottom bar, as Clipboard History does.

### Removed

- **Window Management** is gone: window commands, custom sizes, window layouts, rooms and Space switching, with their shortcuts, deeplinks and settings pane. Switch Windows stays.

## 0.12.8-lite.4

### Removed

- **Calendar** is gone completely: the meeting card on the empty palette, Join Next Meeting, My Schedule, Create Event, Copy Meeting Link, Open in Calendar, meeting details, meetings in launcher search, auto join and the camera preview before a meeting, the calendar menu-bar item, the Calendar settings pane and the Calendars row in Permissions. Tinycast no longer asks for calendar access. Its leftover settings, shortcuts and the `calendar` section in `settings.json` are cleaned up on first launch; My Schedule leaves the compact bar.
- **Raycast themes** are gone: the Light theme and Dark theme pickers, Browse Themes, importing `raycast://theme` links, the theme background slider and the Theme command. Appearance is just System, Light or Dark, in Tinycast's own colors, and the expanded palette is plain glass again with no tinted backdrop. Saved themes and the Theme command are cleaned up on first launch.

### Changes

- **Escape always walks back.** The Escape Key Behavior setting is gone: Escape clears the search, then steps back screen by screen, and on the root search closes the palette so it opens fresh next time. The launcher hotkey takes you home: on any other screen it jumps straight to the root search, and on the root search it closes the palette, which opens fresh next time. Only clicking away keeps your place, and the next summon brings that screen back until Pop to Root Search expires. ⌘Esc no longer jumps to the root search, so Tinycast stops claiming that shortcut and no longer needs Accessibility for it.
- **The expanded palette has hard edges.** A thin line now separates the search bar and the bottom bar from the list, and rows stop at those lines instead of fading out beneath the bars. The search text is smaller, starts without the magnifying glass and sits centred in the search bar. The bottom bar is lower, leaving more room for the list. The bottom buttons lose their capsule: Open and Actions sit bare, split by a short line that hides while you hover either one. This applies to every screen in the palette.
- **Interface Size has two steps.** Default keeps the original layout and proportions with slightly larger text, and Large adds 4% to the layout with larger text still. The old smallest size is gone: it now opens at Default, and the old Large and Larger choices keep their text size.

### Fixes

- **Clipboard History keeps the keyboard after a click on the preview.** After clicking the text in the preview, Escape and the other keys go back to the search and the list instead of beeping; ⌘C still copies the selected text.
- **Clipboard History's preview no longer touches the line above it.** Text, images and files start level with the list beside them.

## 0.12.8-lite.3

### New

- **Snippets** are back, rebuilt around your own Markdown files. Add one or more folders in Settings → Snippets, then Search Snippets finds a file by its name, `keywords` and subfolder names, and previews it with highlighted code. ↵ copies it; ⌘↵ pastes a one-line snippet straight into the app you were in. Create, edit, move between folders and delete from the palette; editing changes only what you edited, so other frontmatter stays as it was. External changes show up on their own.

### Changes

- **The round menu button** at the bottom left of the palette is gone. Settings stays on ⌘, and Quit in the menu-bar icon; **Changelog** moves to Settings → About, next to GitHub, and opens this repository's releases.
- **The ⌘K Actions menu** has the same corner radius as the palette.
- **Code blocks** in Snippets, AI Chat and Quick Actions have smaller corners and no longer wrap: a long line scrolls sideways.

## 0.12.8-lite.2

### Removed

- **Dictation** is gone, along with its settings, the microphone button in AI Chat and the
  microphone permission.
- **Hyper Key** is gone.
- **Raycast import** is gone.
- **Notes** are gone completely.
- **Snippets** are gone completely: keyword expansion, the Snippets pane and its commands, snippet shortcuts and links, the backup category and *Save as Snippet* in Clipboard History. Quicklinks keep every placeholder they had. Their leftover settings, and the `snippets` and `notes` sections in `settings.json`, are cleaned up on first launch.
- Commands cleanup.

### Settings

- **About** is cleaned up.

### Fixes

- **Form fields keep their focus.** A text field in a launcher form no longer reports losing focus
  each time the form redraws while you type in it.

### From upstream Tinycast 0.12.8

Everything from upstream up to 0.12.8 that applies to Lite. Its update signing, update pill,
Notes, Dictation and Hyper Key changes are left out.

- **Compact mode is the default**: a glass search capsule with up to four shortcut buttons, chosen
  in Settings → General → Compact Shortcuts and reachable with the arrow keys. *Show favorites in
  compact mode* is gone.
- **Deeplinks for built-in commands.** Every row that takes a hotkey also runs by
  `tinycast://<kind>/<id>`; ⇧⌘C copies a row's link. Links can carry input, open Settings tabs and
  saved chats, and ask once before acting outside Tinycast.
- **Files and folders as favorites** in the launcher.
- **Show animations** in General settings turns the interface's motion off.
- Opening Tinycast from Finder or Spotlight shows the launcher, and a finished update says so.
- **Window management:** move-to-edge commands, fullscreen windows move between displays, and new
  display-move options.
- **Calculator:** natural-language dates, times in other zones, compound rates and split bills.
- **AI:** custom request headers for API connections, an *Expand thinking* setting, OpenAI MCP tool
  calls fixed, OpenCode uses Tinycast's MCP servers, and Apple Intelligence chats send no instructions.
- **Clipboard history** records HTML-only and RTF-only copies.
- **Extensions:** web OAuth keeps its state through the redirect page, sign-in finishes when
  cancelled, missing preferences can be set directly, and more Node APIs work (`os.networkInterfaces`,
  AES-GCM, `SharedArrayBuffer`, process and file owners).
- Fixes: Volume Up/Down on devices with an off-grid level, the running dot after an app quits,
  calendar events open in the default calendar app, translation language pairs, onboarding language,
  a waiting shell command's prompt, the Toggle System Appearance message, a text area crash, and a
  batch of lifecycle and data-safety bugs.

## 0.12.1-lite.1

First Tinycast Lite release, based on [Tinycast 0.12.1](https://github.com/abue-ammar/tinycast/releases/tag/v0.12.1).
Tinycast Lite is a separate app with its own settings and permissions, and it updates itself from this repository's releases.

Most of the changes below come from [Tinycast Space](https://github.com/sermelipharo/tinycast-space), collected from several community forks.

### Launcher and search

- **Alias + Space opens an entry.** Type an exact alias and press Space: a command with arguments
  jumps to its first field, an extension command with optional arguments opens so the rest of what
  you type goes into its own search bar (`brew` → Search Homebrew), and anything else runs. A
  backslash before the Space types a plain space instead.
- **Alias + Tab** does the same as alias + Space. Tab on anything else works as before.
- **Change Alias and Change Shortcut in ⌘K.** Every launcher entry, extension commands included, can
  be given an alias or a shortcut in place, without opening Settings.
- **⌘1–⌘9 run search results.** With a query typed, ⌘N runs the Nth row as Return would; holding ⌘
  shows the numbers.
- **The palette shortcut hides the palette on any screen**, and the next press brings back the
  screen you left.
- **Typo-tolerant search.** When a query of four letters or more matches nothing, Tinycast tries
  again allowing a typo or two. Queries that already match rank exactly as before.
- **Copy Deeplink.** Every entry's ⌘K menu copies a `tinycast://` link that runs it from anywhere —
  a script, another launcher, a note.
- **Show Info in Finder.** ⌘I on an application, or *Show Info in Finder* in its ⌘K menu, opens
  Finder's Get Info window.
- **Escape pops to root.** With "Navigate back or close window", Escape (or the back chevron) on a
  screen with no step back closes the palette and returns to the root search, so a screen opened by
  its own shortcut no longer comes back on every summon.

### Quick Actions

- **Quick Actions open on a palette screen** instead of a floating panel. The text — the selection,
  else the clipboard — is shown on top and can be edited; Return runs the action and the reply
  streams below. Return then pastes the reply into the app you came from, ⌘Return copies it, ⌘E edits
  the text again, and Escape stops a running reply.
- The model, effort or language can be changed per run in the screen's header.

### Appearance

- **Raycast themes.** Settings → General → Appearance has a light and a dark theme slot, filled from
  the ray.so catalog or from imported themes, with a live preview of the theme under the pointer. The
  *Theme* command switches themes from the palette, previewing each as you move through the list.
  `raycast://theme` links — from ray.so, the clipboard or an extension — ask whether to use or just
  add the theme. *Theme background* sets how strongly the palette shows the theme's gradient.
- **Hyper glyph for another app's Hyper key.** With Hyper Key set to None, *Show ✦ for another app's
  Hyper key* still shows Karabiner- or Hyperkey-style chords as ✦.
- **Window corners match macOS windows.** The palette, Notes, dialogs and settings editors are rounded
  like a regular window instead of twice as much.
- **Confetti**, as a system action and as `raycast://confetti`.

### Raycast extensions

- **⌘Return runs an action panel's second action**, as in Raycast; the ⌘K panel labels the first two.
- **Selectable Detail markdown.** All text in an extension's Detail view can be selected and copied;
  code blocks get a frame with their language and a Copy button.
- Deeplinks pass `context` to the command they open; forms focus their `autoFocus` field; icons with a
  `@dark` variant use it on a dark background; ↑/↓ through long extension lists is faster.
- More extensions work:
  - **Google sign-in** for clients without a secret (2FA Code Finder's Gmail sign-in and others).
  - **Google Translate** and other extensions that bundle undici.
  - **OAuth sign-in through raycast.com/redirect** no longer ends in "Application error".
  - Extensions built on `got`, and those that run command-line tools: a missing tool reports a normal
    "not found" error, and tools are looked up on the extension's own `PATH`.

### Clipboard and snippets

- *Images Only* in Clipboard History includes copied image files, and *Files Only* leaves them out.
- *Save as Snippet* (⌘S) in Clipboard History turns a text entry into a new snippet.
- Search Snippets: *Copy to Clipboard* (⌘Return) fills in a snippet and copies it; *Show in Finder*
  moves to ⌘F.

### Fixes

- A quicklink that starts with a placeholder, such as `{clipboard}`, opens instead of failing.
- Open Trash opens the Trash instead of the home folder.
