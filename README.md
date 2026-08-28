# SteaMidra on CrossOver

A setup guide for running **SteaMidra** through **CrossOver/Wine**


---



## 1. Download SteaMidra

Download the latest official [**SteaMidra**](https://github.com/Midrags/SFF/releases) setup from its GitHub releases page.

Run the SteaMidra installer through CrossOver and complete the installation normally.

### Important

Do not launch SteaMidra yet.
At the final screen, **uncheck**:

> **Run SteaMidra**


---

## Installing ICU 78.3

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


Rename:

```text
icuuc78.dll --> icuuc.dll
```



Copy all three files into:

```text
SteaMidra/_internal/PyQt6/Qt6/bin/
```

---

## 2. Setup CrossOver

Open the bottle's **Wine Configuration** and add:

```text
dwmapi
```

Apply the change before continuing.

Open the SteaMidra bottle in CrossOver.

Under **Graphics**, select: *Wine*

---


## 3. Run SteaMidra

In CrossOver, use **Run Command**.

Navigate to the SteaMidra installation directory and select:

```text
SteaMidra_GUI.exe
```


Before launching the executable, add this environment variable:

```text
QTWEBENGINE_CHROMIUM_FLAGS=--disable-gpu-compositing
```
After SteaMidra launches run **AutoLC**

## Replace `dwmapi.dll`

After SteaMidra has been closed, locate:

```text
Program Files (x86)/Steam/
```

Replace the existing:

```text
dwmapi.dll
```

with the `dwmapi.dll` from the [releases](https://github.com/AirUser-max/SteaMidra_MacOS/releases/tag/dwmapi.dll) 


---

## 4. Final Launch

Run:

```text
SteaMidra_GUI.exe
```


Use the same environment variable from earlier:

```text
QTWEBENGINE_CHROMIUM_FLAGS=--disable-gpu-compositing
```

