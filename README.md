**On June 25, 2026, an HTB update added translation directly through their website, making this script USEFUL ONLY if your language is available via Google Translate but not on HTB.**


# HTB Academy - Google Translate Fix

**A Tampermonkey script to translate Hack The Box Academy without breaking the layout.**

## 🛑 The Problem

Trying to learn something else at the same time as a language is a idiotic way to take in a ton of information without retaining any of it. 
 **In cybersecurity,  English is essential , but you need to learn these two fields separately.**

Translating HTB Academy modules using the built-in Google Translate tool often turns the learning experience into a nightmare. The translation engine (AI) poorly handles the HTML code tags (`<code>`) used by HTB to highlight technical terms (e.g., `Web API`, `HTTP methods`). 

As a result, the translator panics when encountering these tags. It chops up sentences incorrectly and breaks the blue frames. **Worst of all, to try and make sense of the paragraphs it just broke, Google Translate actively adds non-existent words (like "APIproxy" or "web framework") that were never in the original text. This attempt to force grammatical sense completely ruins the technical accuracy and makes the text confusing to read.**

## 💡 How it works (The Solution)

Instead of trying to block the translation, this script uses a "stealth" approach to trick the Google Translate algorithm while strictly maintaining the site's original aesthetics:

1.  **Stealth Transformation (`<code>` to `<span>`):** The script dynamically converts all small keyword frames into fluid text elements. Google Translate can then read and translate the entire sentence in a **perfectly logical and grammatical way**, without generating ghost words or gibberish.
2.  **Preserving the HTB Design:** The visual rendering is fully preserved. The script retrieves and locks the original CSS: the text stays in the characteristic HTB blue, the background remains dark gray, and a "monospace" font is forced to maintain the "code" look.
3.  **Anti-Bug Cleanup:** It targets and removes the hidden directional attributes (`dir="ltr"`) within HTB's keywords, which are the main reason Google randomly splits sentences.
4.  **Dynamic Support (Vue.js / Nuxt):** The script monitors the page in the background. When you switch from one section to another in a module (without reloading the page), the optimization is instantly and automatically applied to the new content.

## 📸 Preview (Before / After)

### Without the script (Google Translate Bug):
<img width="1438" height="763" alt="image" src="https://github.com/user-attachments/assets/846310ad-328d-4faf-a8c4-c6fdd69d5b0a" />

### With the script (Smooth and clean translation):
<img width="1439" height="709" alt="image" src="https://github.com/user-attachments/assets/01f9df66-a90d-4e6c-bb18-e4e365287d53" />

**Requirement:** Active permission to execute user scripts : https://www.tampermonkey.net/faq.php?q=Q209#Q209
