# Botanical ChatGPT

A CSS-only browser extension that gives ChatGPT a warm botanical theme inspired
by sunlit ivory interiors, deep green leaves, fresh lime accents, and muted gold.

The extension contains:

- No JavaScript
- No popup or background process
- No analytics or network requests
- No remote images, fonts, or other dependencies
- One Manifest V3 file and one CSS file

It applies only to `chatgpt.com` and the legacy `chat.openai.com` address.

## Install in Chrome

1. Keep this folder somewhere permanent on your computer. If you received the
   ZIP package, unzip it first.
2. Open Chrome and enter `chrome://extensions` in the address bar.
3. Turn on **Developer mode** in the upper-right corner.
4. Select **Load unpacked**.
5. Select this folder, the one containing `manifest.json`.
6. Open or refresh [ChatGPT](https://chatgpt.com).

Chrome creates a generic extension icon because this theme does not need a
toolbar button. To turn the theme off, use the toggle beside **Botanical
ChatGPT** on `chrome://extensions`.

## Use on another computer

Copy `botanical-chatgpt-extension.zip` to the other computer, unzip it, and
repeat the Chrome installation steps above. Chrome does not sync extensions
that were loaded in Developer mode, so each computer needs to load its own
unpacked copy.

After changing the CSS, return to `chrome://extensions`, select the reload icon
on the extension card, and refresh ChatGPT.

## Install in Safari

Safari cannot load the raw extension folder directly. Apple requires Safari Web
Extensions to be wrapped in a small macOS app, but the same manifest and CSS can
be converted without adding JavaScript.

Requirements:

- A Mac with a current version of macOS
- Xcode installed from the Mac App Store

From Terminal on the Mac, run:

```sh
xcrun safari-web-extension-converter "/path/to/botanical-chatgpt" \
  --project-location "/path/to/safari-build" \
  --app-name "Botanical ChatGPT" \
  --bundle-identifier "com.yourname.botanical-chatgpt"
```

Then:

1. Open the generated Xcode project in `safari-build`.
2. Select the app target. Under **Signing & Capabilities**, choose your Apple
   development team if Xcode asks for one.
3. Select **My Mac** as the run destination and press **Run**.
4. Open the generated **Botanical ChatGPT** app once.
5. In Safari, open **Safari > Settings > Extensions**.
6. Enable **Botanical ChatGPT** and allow access to `chatgpt.com`.
7. Open or refresh ChatGPT.

The Safari app wrapper is required by Safari; the web extension inside it
remains CSS-only. Distributing it broadly to other people through Safari
requires Apple's normal app signing and distribution process.

Apple's reference:
[Packaging a web extension for Safari](https://developer.apple.com/documentation/safariservices/packaging-a-web-extension-for-safari)

## Customize the colors

Open `styles/botanical-chatgpt.css`. The editable palette is at the top:

```css
--botanical-canvas: #f3eedc;
--botanical-surface: #fbf8eb;
--botanical-leaf: #17613f;
--botanical-leaf-deep: #113d31;
--botanical-leaf-bright: #218343;
--botanical-lime: #91b52b;
--botanical-gold: #d6a83b;
```

Change those values, reload the extension, and refresh ChatGPT.

## Troubleshooting

**The theme is not visible**

- Confirm the extension is enabled.
- Confirm the address starts with `https://chatgpt.com/`.
- Reload the extension and then refresh the ChatGPT tab.
- If ChatGPT was already open during installation, close and reopen that tab.

**Part of ChatGPT uses its original colors**

ChatGPT's interface changes over time. This theme primarily uses ChatGPT's
theme variables and stable semantic attributes to reduce breakage. If a new
interface element is missed, update `styles/botanical-chatgpt.css`.

**Chrome reports a manifest error**

Make sure you selected the extracted folder that directly contains
`manifest.json`, not the ZIP file or a parent folder.

## Privacy and permissions

The manifest declares only a CSS content script for ChatGPT URLs. It does not
request browser API permissions and cannot read, store, or transmit chats.
