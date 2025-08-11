# Upgrade

PowerShell can be upgraded from within PowerShell using the winget command-line tool, which is a package manager for Windows. Here's how to do it:

1. Open PowerShell as administrator. This is necessary to install the updated version of PowerShell.

Search for the PowerShell package using winget. Execute the following command:

>	winget search Microsoft.PowerShell

This command will display available PowerShell packages, including the latest version.

2. Install the latest version of PowerShell. If an update is available, use the following command to install it:

>	winget install --id Microsoft.PowerShell --source winget --exact --silent --scope machine

This command will download and install the newest version of PowerShell.

3. Alternatively, you can use the Install-Module command to update PowerShellGet, which is a module that helps manage other PowerShell modules.

>	Install-Module PowerShellGet -Force

After this initial switch, you'll be able to use Update-Module PowerShellGet to update PowerShellGet in the future.

>[!NOTE]
It's worth noting that PowerShell doesn't auto-update by default. You need to manually trigger the update process using the methods described above.
>
Additionally, you can enable Microsoft Update for PowerShell. This allows you to get the latest PowerShell 7 updates through the traditional Microsoft Update management flow. 

# Edit PowerShell Apparence

This guide walks you through editing the `settings.json` file to customize the appearance of PowerShell 7 in Windows Terminal.

  

---

  

## 📌 Prerequisites

  

- Windows Terminal installed (from Microsoft Store or GitHub)

- PowerShell 7 installed

- Basic familiarity with JSON editing

- A text editor (VS Code recommended)

  

---

  

## 🔍 Step-by-Step Guide


### 1. **Open Windows Terminal Settings as JSON**

  

1. Launch **Windows Terminal**.

2. Click the dropdown arrow next to the tab bar.

3. Select **"Settings"** — this opens the GUI settings page.

4. At the bottom left, click **"Open JSON file"**.

  

Alternatively, open the file directly:

> 	C:\Users\<YourUsername>\AppData\Local\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe\LocalState\settings.json

  

---

  

### 2. **Locate the PowerShell 7 Profile**

  

Search for the section that looks like this in **settings.json under **"profiles" -> "list":

  

```json

{

  "guid": "{your-guid}",

  "name": "PowerShell 7",

  "commandline": "pwsh.exe",

  "hidden": false

}

```

  

---

  

### 3. **Edit Appearance Settings**

  

Add or modify the following keys inside the PowerShell 7 profile object:

  

```json

{

  "name": "PowerShell 7",

  "source": "Windows.Terminal.PowershellCore",

  "colorScheme": "One Half Dark",

  "fontFace": "Cascadia Code PL",

  "fontSize": 12,

  "acrylicOpacity": 0.85,

  "useAcrylic": true,

  "backgroundImage": "C:/Path/To/Image.png",

  "backgroundImageOpacity": 0.2,

  "backgroundImageStretchMode": "fill"

}

```

  

> 💡 **Note:** Update the image path and appearance settings to your preference.

  

---

  

### 4. **Customize or Add Color Schemes**

  

Scroll to the `"schemes"` section or add a new one:

  

```json

"schemes": [

        {

            "name": "MyCustomDark",

            "background": "#0C0C0C",

            "foreground": "#FFFFFF",

            "selectionBackground": "#FFFFFF",

            "cursorColor": "#FFFFFF",

  

            /* colors */

  

            "black": "#1E1E1E",

            "brightBlack": "#5C6370",

  

            "white": "#ABB2BF",

            "brightWhite": "#FFFFFF",

  

            "blue": "#61AFEF",

            "brightBlue": "#61AFEF",

  

            "cyan": "#56B6C2",

            "brightCyan": "#56B6C2",

  

            "green": "#98C379",

            "brightGreen": "#98C379",

  

            "purple": "#C678DD",

            "brightPurple": "#C678DD",

  

            "red": "#E06C75",

            "brightRed": "#BE5046",

  

            "yellow": "#E5C07B",

            "brightYellow": "#D19A66"

        }

    ],


```

  

Then reference it by name in the profile:

  

```json

"colorScheme": "MyCustomDark"

```



---

  

### 5. **Save and Restart**

  

- Save the `settings.json` file.

- Restart Windows Terminal to see your changes in effect.

  

---

  

## ✅ Tips

  

- Fonts like **Fira Code**, **Cascadia Code PL**, or **JetBrains Mono** support programming ligatures and enhance the look.

- You can use `"padding"` to control spacing, e.g., `"padding": "12, 8, 12, 8"`.

- Use `"cursorShape": "filledBox"` to change the cursor type.

  

---

  

## 🧪 Troubleshooting

  

- 🛑 JSON parse error? Make sure all commas and brackets are correctly placed.

- ⚠️ Appearance not applying? Ensure you’re editing the correct profile (`"name": "PowerShell 7"`).

- ⚠️ Make sure to add the line which references the scheme by name to all profiles (see step 4)

  

---

  

## 📚 References

  

- [Windows Terminal Docs](https://learn.microsoft.com/en-us/windows/terminal/)

- [PowerShell 7](https://github.com/PowerShell/PowerShell)

  

---

  

Happy customizing! 🎨

---
# Profiles
## Dark+ 
```json
{
  "name": "Dark+",
  "background": "#1E1E1E",
  "foreground": "#D4D4D4",
  "black": "#000000",
  "red": "#CD3131",
  "green": "#0DBC79",
  "yellow": "#E5E510",
  "blue": "#2472C8",
  "purple": "#BC3FBC",
  "cyan": "#11A8CD",
  "white": "#E5E5E5",
  "brightBlack": "#666666",
  "brightRed": "#F14C4C",
  "brightGreen": "#23D18B",
  "brightYellow": "#F5F543",
  "brightBlue": "#3B8EEA",
  "brightPurple": "#D670D6",
  "brightCyan": "#29B8DB",
  "brightWhite": "#E5E5E5"
}

```
## My Theme - blue
```json
        {

            "background": "#2D7D9A",

            "black": "#000000",

            "blue": "#bfc6d4",

            "brightBlack": "#725f0a",

            "brightBlue": "#a8c5e6",

            "brightCyan": "#29B8DB",

            "brightGreen": "#11ff00",

            "brightPurple": "#D670D6",

            "brightRed": "#F14C4C",

            "brightWhite": "#ac4a4a",

            "brightYellow": "#F5F543",

            "cursorColor": "#000000",

            "cyan": "#6bdfff",

            "foreground": "#000000",

            "green": "#0DBC79",

            "name": "My Theme - blue",

            "purple": "#BC3FBC",

            "red": "#ff7d7d",

            "selectionBackground": "#72cf7b",

            "white": "#E5E5E5",

            "yellow": "#E5E510"

        },
```
## Palenight
```json
        {

            "background": "#292D3E",
            "foreground": "#A6ACCD",
            "black":      "#000000",
            "red":        "#F07178",
            "green":      "#C3E88D",
            "yellow":     "#FFCB6B",
            "blue":       "#82AAFF",
            "purple":     "#C792EA",
            "cyan":       "#89DDFF",
            "white":      "#D0D0D0",
            "brightBlack":  "#434758",
            "brightRed":    "#FF8B92",
            "brightGreen":  "#DDFFA7",
            "brightYellow": "#FFE585",
            "brightBlue":   "#9CC4FF",
            "brightPurple": "#E1ACFF",
            "brightCyan":   "#A3F7FF",
            "name": "Palenight",
            "brightWhite":  "#FFFFFF"

        },

```
## Tokyo Storm Gogh
```json
        {
            "background": "#24283B",
            "foreground": "#C0CAF5",
            "black":      "#1D202F",
            "red":        "#F7768E",
            "green":      "#9ECE6A",
            "yellow":     "#E0AF68",
            "blue":       "#7AA2F7",
            "purple":     "#BB9AF7",
            "cyan":       "#7DCFFF",
            "white":      "#A9B1D6",
            "brightBlack":  "#414868",
            "brightRed":    "#F7768E",
            "brightGreen":  "#9ECE6A",
            "brightYellow": "#E0AF68",
            "brightBlue":   "#7AA2F7",
            "brightPurple": "#BB9AF7",
            "brightCyan":   "#7DCFFF",
            "brightWhite":  "#C0CAF5",
            "name": "Tokyo Storm Gogh"
        }

```

## Dracula
```json
{
  "name": "Dracula",
  "cursorColor": "#F8F8F2",
  "selectionBackground": "#44475A",
  "background": "#282A36",
  "foreground": "#F8F8F2",
  "black": "#21222C",
  "blue": "#BD93F9",
  "cyan": "#8BE9FD",
  "green": "#50FA7B",
  "purple": "#FF79C6",
  "red": "#FF5555",
  "white": "#F8F8F2",
  "yellow": "#F1FA8C",
  "brightBlack": "#6272A4",
  "brightBlue": "#D6ACFF",
  "brightCyan": "#A4FFFF",
  "brightGreen": "#69FF94",
  "brightPurple": "#FF92DF",
  "brightRed": "#FF6E6E",
  "brightWhite": "#FFFFFF",
  "brightYellow": "#FFFFA5"
}

```