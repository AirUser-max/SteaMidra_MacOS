# SteaMidra on CrossOver

A setup guide for running **SteaMidra** through **CrossOver/Wine**, including the required DLL overrides, ICU libraries, graphics configuration, and optional support for downloading native macOS game builds.


---



## 1. Download SteaMidra

Download the latest official **SteaMidra** setup from its GitHub releases page.


## 2. Add the `dwmapi` DLL Override

Open **CrossOver** and select the bottle where SteaMidra will be installed.

Open the bottle's **Wine Configuration** and add:

```text
dwmapi
```

Apply the change before continuing.

---

## 3. Install SteaMidra

Run the SteaMidra installer through CrossOver and complete the installation normally.

### Important

At the final screen, **uncheck**:

> Run SteaMidra

Do not launch SteaMidra yet.

---

# Installing ICU 78.3

SteaMidra requires the ICU 78.3 runtime libraries.

Official ICU 78.3 release:

**https://github.com/unicode-org/icu/releases/tag/release-78.3**

Download:

```text
icu4c-78.3-Win64-MSVC2022.zip
```

Extract the ZIP somewhere convenient.

From the extracted files, locate:

```text
icuuc78.dll
icuin78.dll
icudt78.dll
```

Create a temporary folder and copy those three files into it.

Rename:

```text
icuuc78.dll --> icuuc.dll
```



Copy all three files into:

```text
SteaMidra/_internal/PyQt6/Qt6/bin/
```

---

# Configure CrossOver Graphics

Open the SteaMidra bottle in CrossOver.

Under **Graphics**, select:

```text
Wine
```

---

# Launch SteaMidra

## 1. Run `SteaMidra_GUI.exe`

In CrossOver, use **Run Command**.

Navigate to the SteaMidra installation directory and select:

```text
SteaMidra_GUI.exe
```

---

## 2. Add the Qt WebEngine environment variable

Before launching the executable, add this environment variable:

```text
QTWEBENGINE_CHROMIUM_FLAGS=--disable-gpu-compositing
```


---

# Run AutoLC

Once SteaMidra starts:

1. Run **AutoLC**.
2. Wait for AutoLC to finish.
3. **Completely exit SteaMidra.**


---

# Restore `dwmapi.dll`

After SteaMidra has been closed, locate:

```text
Program Files (x86)/Steam/
```

Replace the existing:

```text
dwmapi.dll
```

with the `dwmapi.dll` from the releases section 


---

# Final Launch

Run:

```text
SteaMidra_GUI.exe
```


Use the same environment variable from earlier:

```text
QTWEBENGINE_CHROMIUM_FLAGS=--disable-gpu-compositing
```

SteaMidra should now launch using the completed configuration.

