# SerialTerm

SerialTerm is a serial and TCP/Telnet terminal for Total Commander on Windows. Open a COM port or a saved network connection in a separate terminal window, in Lister, or directly in the Quick View panel.

It supports text and hexadecimal output, ANSI colors, selectable character encoding, timestamps, and connection history. Both 32-bit and 64-bit Total Commander are supported.

## Installation

Only the file system plugin files are supplied:

- `SerialTerm.wfx` (32-bit)
- `SerialTerm.wfx64` (64-bit)

1. Place both files and the supplied `languages` folder together in a folder where you have write permission.
2. In Total Commander, open **Configuration → Options → Plugins**.
3. Under **File system plugins (.WFX)**, choose **Configure → Add** and select `SerialTerm.wfx`.

64-bit Total Commander automatically uses `SerialTerm.wfx64`.

Open **Network Neighborhood** in Total Commander and select **SerialTerm**. You can now open terminals with **Enter**.

### Optional: enable F3 and Quick View

**Lister registration is not included and must be performed manually by the user.** To use **F3** and **Ctrl+Q**, create Lister copies of the supplied files:

1. In the same plugin folder, **copy** `SerialTerm.wfx` to `SerialTerm.wlx`.
2. **Copy** `SerialTerm.wfx64` to `SerialTerm.wlx64`. Keep the original WFX files as well.
3. Open **Configuration → Options → Plugins**.
4. Under **Lister plugins (.WLX)**, choose **Configure → Add** and select `SerialTerm.wlx`.

64-bit Total Commander automatically uses `SerialTerm.wlx64`. Keep all WFX and WLX files together so they share the same settings.

### Updating

Completely close Total Commander before replacing the supplied WFX files and updating the `languages` folder. If you enabled Lister support, recreate both WLX copies from the updated WFX files, replacing the previous copies. Then restart Total Commander. You only need to register the plugins once, provided their paths stay the same.

Already loaded plugins continue using the previous version until Total Commander is closed.

Keep `serialterm.ini` to preserve your settings and saved TCP connections.

## Getting started

The SerialTerm list contains:

| Entry | Purpose |
|---|---|
| `[ Manage connections… ]` | Manage saved TCP connections and configure terminal appearance. Press **Enter** to open it. |
| `COM7  Silicon Labs…` | An available serial port, with its device description. |
| `TCP - <name>` | A saved TCP or Telnet connection. |

The interface supports English, German, Ukrainian, and Russian. This guide uses the English labels.

### Connect to a serial device

1. Select its COM port and press **Alt+Enter** to open its properties.
2. Set the baud rate, data bits, stop bits, parity, and flow control required by your device.
3. Confirm with **OK**, then press **Enter** on the port to open the terminal.
4. Use **Connect** or **Disconnect** to control the connection.

The defaults are **115200 baud, 8 data bits, no parity, 1 stop bit**, no flow control, and DTR/RTS off.

### Add a TCP or Telnet connection

1. Open **Manage connections…**.
2. On the **Connections** tab, choose **New**.
3. Enter a name, host name or IPv4 address, and port number.
4. Choose **Raw (TCP)**, **Telnet with negotiation**, or **Telnet without negotiation (IAC filter)**.
5. Click **Save**, close the dialog, and open the new `TCP - <name>` entry.

You can edit or delete saved connections in the same dialog. **F8** on a TCP entry also deletes the saved connection. If the list does not refresh immediately, press **Ctrl+R**.

## Opening a terminal

| Key | Action |
|---|---|
| **Enter** | Open a separate terminal window. Opening another entry replaces the connection in that window. |
| **F3** | Open the terminal in Total Commander's Lister window. |
| **Ctrl+Q** | Show the terminal in the Quick View panel. Selecting another entry switches the preview and disconnects the previous connection. |
| **Alt+Enter** | Open the selected entry's properties. |

The management entry shows an empty preview when selected with F3 or Ctrl+Q. Use Enter to open its settings dialog.

### Automatic connection and reconnection

Each port or TCP connection has its own options in **Properties**:

- **Connect automatically (Enter, F3)**: connect automatically when opened with Enter or F3. Enabled by default.
- **Also connect in Quick View (Ctrl+Q)**: also connect automatically in Quick View. Disabled by default; enable this together with the first option if desired.
- **Reconnect automatically after connection loss**: reconnect after the connection is lost.

When automatic connection is disabled, click **Connect** to start the connection. Automatic reconnection waits until you do so. Clicking **Disconnect** stops automatic reconnection until you connect again.

Changes to an entry's properties apply immediately to its open separate terminal window. Reopen an existing F3 or Quick View terminal to use changed properties.

## Using the terminal

Type into the input field and press **Enter**, or click **Send**. Choose the outgoing line ending beside the input field: none, CR, LF, or CR+LF.

| Control | Purpose |
|---|---|
| **View** | Switch between Text and Hex output. |
| **Encoding** | Select UTF-8, Latin-1/CP1252, or ASCII. |
| **Rx line ending** | Select received line endings: Auto, CR+LF, LF, or CR. Auto recognizes all three forms. |
| **ANSI colors** | Enable colors supplied by the connected device. Disable for uniform text color. |
| **Autoscroll** | Follow incoming output. Scrolling up pauses it; scrolling to the bottom resumes it. |
| **Local echo** | Display sent text locally. Negotiated Telnet server echo suppresses local echo to avoid duplicates. |
| **Auto-reconnect** | Enable automatic reconnection after connection loss. |
| **Timestamps** | Show local arrival times before text lines, including retained output. |
| **Clear** | Clear the displayed output and its retained data. |

Serial settings can also be changed in the terminal toolbar. DTR and RTS switches are available unless their line is controlled by the selected hardware flow control.

The status area shows the connection state and received/sent byte counts. For serial connections, it also displays CTS, DSR, RI, and DCD signals.

### Selection and keyboard shortcuts

- Drag across output to select text; **Ctrl+C** copies the selection and **Ctrl+A** selects all output when the output area has focus.
- Right-click the output for Copy, Select all, and Clear output.
- In the input field, **Up/Down** recalls previously sent lines.
- In the output area, **Page Up/Page Down** scrolls; **Ctrl+Home/Ctrl+End** jumps to the beginning/end.
- **Ctrl+Q** toggles Quick View. If it does not respond while editing the baud rate, move the focus to the input or output area first.
- Close an F3 terminal with its window's close button; Esc does not close it.

## Fonts, colors, and hexadecimal output

Open **Manage connections…** with Enter, or select **SerialTerm** in Network Neighborhood and press **Alt+Enter** (Properties). Font and Appearance settings apply to all serial and TCP terminals, including F3 and Quick View. Click **Save** on the relevant tab; open terminals update within about one second.

On the **General** tab, choose the interface language and dialog theme: **Follow Total Commander** (default), **Light**, or **Dark**. Click **Save** to apply the theme immediately. This affects the connection manager and connection properties; terminal background and text colors remain independently configurable. Windows high contrast takes precedence.

### Font

Choose a font and a size from **6 to 72 pt**, using the arrow buttons or typing a value. The font list offers installed fonts with fixed character widths, and the preview shows your selection.

Default: **Consolas, 10 pt**.

### Appearance

- **Terminal background**: choose the terminal background color.
- **Text (ANSI colors off)**: choose the text color used when ANSI colors are disabled, and for hexadecimal output.
- **Hex: bytes per line**: choose **1–64 bytes per line**, using the arrow buttons or typing a value. Default: **24 bytes**.

Use **Choose…** to open the color picker, or enter a color as `#RRGGBB`. The defaults are a nearly black background (`#0C0C0C`) and light gray text (`#CCCCCC`).

With ANSI colors enabled, the device's explicit text and background colors take precedence. Hex output includes byte offsets, a position ruler, and an ASCII column. Changing the number of bytes per line only changes the layout; it does not change received data or counters.

## History and timestamps

In each entry's properties, enable **Keep history when the terminal closes** and choose a depth of **100–100,000 lines**. The default is **10,000 lines**.

Output, input history, and counters can be retained when a terminal closes, so reopening the same entry restores them. History lasts only for the current Total Commander session and is lost when Total Commander exits. Nothing is recorded while the connection is closed.

Without history, only a short display buffer is available and output is discarded when the terminal closes. Retained history is also limited by the amount of received data, so very long lines can reduce the available history.

History opened with Enter is separate from history opened with F3 or Quick View. A second window for an already open entry starts with its own empty history.

**Timestamps** adds `[hh:mm:ss.mmm]` before text lines and includes those timestamps when copying. Timestamp display can be toggled for retained output. Hex output does not show timestamps.

## Interface language

Keep the supplied **`languages` folder beside the WFX files**, with the supplied language files (`en.ini`, `de.ini`, `uk.ini`, `ru.ini`). The optional WLX copies use the same folder.

Choose the interface language on **Manage connections… → General**, click **Save**, then restart Total Commander to apply the language throughout the plugin. You can also edit `serialterm.ini`:

```ini
[Plugin]
Language=en
Theme=auto
```

The management entry is also translated; for example, German shows **[ Verbindungen verwalten… ]**. Reopening the plugin folder updates the panel label after a language change.

The language selector lists the translation files found in `languages` when you open the connection manager. `Language` stores the filename without `.ini`, for example `fr` for `fr.ini` or `pt-br` for `pt-BR.ini`. English is the default and the fallback for missing language files and missing translations. The interface remains usable in English even if the language files are unavailable.

To add a translation, copy `en.ini` to a new UTF-8 file, such as `languages/fr.ini`, translate the values, and set its native language name:

```ini
[Strings]
language.name="Français"
action.connect="Connecter"
manage.name="Gérer les connexions…"
```

Reopen **Manage connections… → General** to select the new language; no plugin rebuild is needed. Keep translation keys and `{0}` placeholders intact. Missing entries fall back to English. If `language.name` is missing, the selector uses the filename stem. Filenames may contain letters A–Z, digits, hyphens, and underscores (up to 63 characters before `.ini`).

For manual INI edits, close Total Commander first, then restart it. `Theme=auto|light|dark` selects the dialog theme. Connection names and received device output are not translated; the terminal's Encoding setting controls how device output is decoded.

## Where settings are stored

Settings and saved TCP connections are stored in **`serialterm.ini` beside the plugin files**. The file is created when settings are saved; the plugin folder must be writable.

To back up or transfer your configuration, copy this file. If you used an older version that stored it beside Total Commander's `wcx_ftp.ini`, copy your existing `serialterm.ini` into the plugin folder to keep those settings.

## Troubleshooting and limitations

- **Access denied when connecting:** another application or terminal window may already be using the COM port. Close that connection and try again.
- **Unreadable output:** check the serial parameters and select the character encoding and received line ending used by the device.
- **Settings do not persist:** check write permission for the plugin folder. After an update, completely restart Total Commander so it loads the new files.
- **A board resets on connection:** some USB serial drivers briefly change DTR/RTS when a port opens, even when those lines are configured off. This can reset devices with an automatic reset circuit.
- ANSI support covers colors, bold, and inverse text. Full-screen terminal applications that require cursor positioning or screen control are not supported.
- Sending is text-only. Hexadecimal input, file transfer, and automatic logging to a file are not available.
- TCP connections support IPv4. Internationalized host names are not automatically converted.
- Very long lines are wrapped after 4,096 characters. Wide characters and some emoji may not align correctly.
- Use the mouse to move between terminal controls if Tab navigation does not work in Lister or Quick View.
