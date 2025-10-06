# <img src="../assets/logo.png"> Tutorial 4 – Profile and Strings

Now we're going to configure two other JSON files: `profile.json` and `strings.json`, both located at the root of the `public/data` folder.

## Profile

The `profile.json` file holds essential information about you — the portfolio owner.  
It includes both **static fields** (which stay the same across all languages) and **locales fields** (which can vary by language).

### ⚡ Profile Static Fields

| Property                   | Type     | Required? | Description                                                                                                                 |
|----------------------------|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------|
| `name`                     | STRING   | REQUIRED  | Your name.                                                                                                                  |
| `profilePictureUrl`        | STRING   | REQUIRED  | Path to your profile picture. The path is relative to the `public` folder (e.g. `images/pictures/pfp.png`).                 |
| `resumePdfUrl`             | STRING   | OPTIONAL  | A direct link to your resume in PDF format. If provided, a button will appear on the sidebar allowing users to download it. |
| `statusCircleVisible`      | BOOLEAN  | REQUIRED  | Indicates whether a small status circle should appear next to your profile picture.                                         |
| `statusCircleVariant`      | STRING   | REQUIRED  | Your availability status. Must be one of: `available`, `busy`, or `unavailable`.                                            |
| `statusCircleHoverMessage` | STRING   | REQUIRED  | A key referencing a localized string that appears when a user hovers over the status circle.                                |

### 🌐 Profile Locales Fields

Every `locales` object is a **nested object of objects**.  
Each root-level entry represents a language ID and contains the localized fields for that language. For example:

```json
{
    "en": {
        "field": "Field"
    },
    "es": {
        "field": "Campo"
    }
}
```

The profile locales properties are:

| Property                                 | Type          | Required?  | Description                                                                                                                                                                                                                                                                    |
|------------------------------------------|---------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `localized_name`                         | STRING        | OPTIONAL   | A version of your name translated into the selected language (e.g., your Spanish name or Chinese name).                                                                                                                                                                        |
| `localized_name_stylized`                | STRING        | OPTIONAL   | An **HTML-formatted** version of your name. You can use `[[text]]` for **bold** and `{{text}}` for highlighting with the primary theme color.                                                                                                                                  |
| `status_message_available_for_freelance` | STRING        | OPTIONAL   | The default status message for your availability. You can customize or add other messages based on your `statusCircleHoverMessage`.                                                                                                                                            |
| `roles`                                  | ARRAY[STRING] | REQUIRED   | A list of roles (e.g., `"Frontend Developer"`, `"Designer"`). If more than one is provided, the app will animate between them every 5 seconds.                                                                                                                                 |
| `name_pronunciation_ipa`                 | STRING        | OPTIONAL   | A phonetic representation of your name. If provided, it will be displayed when the pronunciation button next to your name is hovered.                                                                                                                                          |
| `name_pronunciation_audio_url`           | STRING        | OPTIONAL   | A direct link to an audio file that plays the pronunciation of your name. If provided, a play button will appear next to your name so users can hear how it's pronounced. Helpful if you're reaching an international audience or have a last name that’s often mispronounced. |

> **Note:** Required fields must be present **at least** in the default language.  
> If a field is missing in a specific language, the app will automatically fall back to the default language set in `settings.json`.

### 📌 Tip: Having a different picture for each theme

You can make your profile picture change based on the active theme using a built-in feature of this template.
Instead of using a static URL, you can set your `profilePictureUrl` like this:


```json
{
    "profilePictureUrl": "images/pictures/pfp-{theme}.png"
}
```

The `{theme}` placeholder will be dynamically replaced with the current theme ID (dark, light, etc.). Then, you need to add the corresponding image variants to your project:
- `images/pictures/pfp-dark.png`
- `images/pictures/pfp-light.png`

Also, to ensure these images are loaded in advance, it's recommended to add them to the `imagesToCache` array in your `settings.json` file:

```json
{
    "imagesToCache": [
        "images/pictures/pfp-dark.png",
        "images/pictures/pfp-light.png"
    ]
}
```

This `{theme}` placeholder works pretty much with any image URL in the project, not just the profile picture.

## Strings

The `strings.json` file contains **global strings** used across various components in your app.

If you've reset your portfolio, the `strings.json` file will already include a set of **preset strings**.  
It’s **strongly recommended** to keep all of them, as they're required by the core components of the application.

Additionally, for full multilingual support, you should provide **translations for each string in each language** you're supporting.  
This ensures your app is fully translated and provides a consistent experience across all supported languages.

## Next Steps
Ready to keep going? Check out the next tutorial or revisit the previous one if you need a refresher:

⬅️ [Previous: Titles and Colors](./TUTORIAL_03_TITLES_AND_COLORS.md)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
[Next: Categories and Sections](./TUTORIAL_05_CATEGORIES_AND_SECTIONS.md) ➡️ 