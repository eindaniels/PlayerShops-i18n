# PlayerShops – Translations (i18n)

Language files for [PlayerShops](https://github.com/eindaniels/PlayerShops), a PaperMC shop plugin using Display Entities and Vault.

This repository contains all translations of the plugin. Anyone can add a new language or improve an existing one.

> [!NOTE]
> Translations are community-friendly: small fixes like typos or better phrasing are just as welcome as whole new languages.

> [!IMPORTANT]
> `en_US/messages.yml` is the reference file. New keys are always added there first.

## Repository structure

Every language has its own folder named after its locale (`language_COUNTRY`), containing a `messages.yml`:

```
.
├── en_US/
│   └── messages.yml
├── de_DE/
│   └── messages.yml
└── README.md
```

## Using a language file

1. Download the `messages.yml` of the language you want (e.g. from the `de_DE` folder).
2. Put it into the plugin's language folder on your server (`plugins/PlayerShops/`).
3. Run `/ps reload`.

## Contributing a translation

### Add a new language

1. Fork this repository.
2. Copy the `en_US` folder and rename it to your locale, e.g. `fr_FR`, `es_ES`, `pt_BR`.
3. Open `messages.yml` in your new folder and translate **only the values**, never the keys.
4. Open a pull request.

### Improve an existing translation

Edit the language's `messages.yml`, fix the wording and open a pull request.

> [!TIP]
> You can edit files directly on GitHub with the pencil icon. GitHub creates the fork and the pull request for you.

## Rules for translations

### Keys stay untouched

> [!CAUTION]
> Never translate or rename keys. The plugin looks messages up by key, so a changed key means a missing message in-game.

```yaml
# correct
mainCommand.usage: "Verwendung: /ps <reload|version|info>"

# wrong – the key was translated
Hauptbefehl.Verwendung: "..."
```

### Keep MiniMessage tags

Messages use [MiniMessage](https://docs.advntr.dev/minimessage/format.html). Keep all tags exactly as they are, including colors, hover and click events. Only translate the visible text.

```yaml
# English
<#ff1717>Warning! This will permanently delete all items in this storage. <hover:show_text:"/forcedeleteshop confirm"><click:run_command:/forcedeleteshop confirm>[Click to confirm]

# German – tags unchanged, text translated
<#ff1717>Achtung! Dadurch werden alle Items in diesem Lager unwiderruflich gelöscht. <hover:show_text:"/forcedeleteshop confirm"><click:run_command:/forcedeleteshop confirm>[Zum Bestätigen klicken]
```

> [!WARNING]
> Command names inside `run_command` must never be translated. A translated command does nothing when the player clicks it.

### Keep placeholders

Placeholders like `{0}`, `{1}`, … are replaced by the plugin at runtime. Keep all of them and their count. You may change their **position** in the sentence if your language needs it.

### Version colors

The `versioning.*` keys define the colors of the release channels and are not meant to be translated:

| Key | Color |
|-----|-------|
| `versioning.alpha`  | `#E5484D` |
| `versioning.beta`   | `#F5A524` |
| `versioning.rc`     | `#3E8EF7` |
| `versioning.stable` | `#30A46C` |

### Style

- Use a consistent form of address (e.g. "du" in German) across the whole file.
- Keep messages short and clear, especially warnings.
- Use the same terms for the same things (e.g. always "Lager" for storage).
- Save the file as **UTF-8** without BOM.

## Testing your translation

1. Put your file on a test server.
2. Select your language and run `/ps reload`.
3. Check the messages in-game, especially those with colors, hover texts and click events.
4. Look into the console for YAML or MiniMessage errors.

> [!TIP]
> Validate your file with a YAML linter before testing. Most errors are missing quotes or wrong indentation.

## Pull request checklist

- [ ] Based on the current `en_US/messages.yml` (all keys present)
- [ ] No keys changed or removed
- [ ] All MiniMessage tags and placeholders kept
- [ ] `messages.yml` is valid YAML, saved as UTF-8 and located in a correctly named locale folder
- [ ] Tested in-game (or at least checked for syntax errors)

## Reporting problems

Found a wrong or missing translation? [Open an issue](../../issues) and mention the language and the key.

> [!NOTE]
> For bugs in the plugin itself, please use the [PlayerShops repository](https://github.com/eindaniels/PlayerShops/issues).
