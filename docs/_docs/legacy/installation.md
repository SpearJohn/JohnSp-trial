---
title: "Manual installation"
permalink: /docs/installation/
excerpt: "[] Instructions for manually install tools and packages."
variable:
  - platform: windows
    name: Windows
  - platform: macos
    name: macOS
  - platform: ubuntu
    name: Ubuntu
last_modified_at: 2018-8-4
---

**Notice:** This article is only for the old experiences by using the installer, and will be obsoleted soon.
we strongly recommend you to use [Azure IoT Workbench](https://aka.ms/iot-workbench) which has much better experiences on both installation and development for developing on IoT DevKit.
You can follow this [tutorial]({{"/docs/get-started" | absolute_url}}) to install [Azure IoT Workbench](https://aka.ms/iot-workbench) and start up the new journey with IoT DevKit. 
{: .notice--warning}

If you have problems on using the one-click install experience, follow these  steps to manually install tools and packages for IoT DevKit development. 

{% include switch.html content = page.variable %}

## Windows

### Step 1. Install Azure CLI 2.0 MSI

Follow the [official guide](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli#windows){:target="_blank"} to install Azure CLI 2.0 with MSI:

Download and run MSI for the Windows command line from: [https://aka.ms/InstallAzureCliWindows](https://aka.ms/InstallAzureCliWindows){:target="_blank"}

### Step 2. Install Arduino IDE

The Visual Studio Code Arduino extension relies on the Arduino IDE. Download and install the [Arduino IDE for Windows](https://www.arduino.cc/en/Main/Software){:target="_blank"}. Make sure you download the **Windows Installer** version.

### Step 3. Install Visual Studio Code

Download and install [Visual Studio Code for Windows](https://code.visualstudio.com/){:target="_blank"}. This is the primary development tool for building IoT DevKit applications.

### Step 4. Download the latest package

1. Download [Windows Installer](https://nodejs.org/en/download/){:target="_blank"} to install Node.js.

2. Download the .zip file that contains required task scripts for IoT DevKit development in VS Code.

  [<i class='fa fa-download'></i> Download](https://aka.ms/devkit/prod/installpackage/tasks/latest){: .click-download-tracker .btn .btn--success .btn--large}

  Locate the .zip and extract it to your Windows user folder (`C:\Users\{your name}\azure-board-cli`). Then launch **Command Prompt** (`cmd`) and run the following commands to configure:

  ```
  cd C:\Users\{your name}\azure-board-cli

  npm install
  ```

### Step 5. Install the VS Code extension for Arduino

You can install Azure Marketplace extensions directly in Visual Studio Code. Select the extensions icon in the left pane, search for **Arduino**, and then select **Install**:

![installation-extensions]({{"/assets/images/installation-extensions-win.png" | absolute_url}})

### Step 6. Install the IoT DevKit board package

Add the IoT DevKit board by using Board Manager in Visual Studio Code.

1. Use `Ctrl+Shift+P` to open the command palette, type **Arduino**, and then find and select **Arduino: Board Manager**.

2. Select **Additional URLs** at the lower right.
 ![installation-additional-urls]({{"/assets/images/installation-additional-urls-win.png" | absolute_url}})

3. In the `settings.json` file, add a line at the bottom of the **USER SETTINGS** pane and save.
 ```json
 "arduino.additionalUrls": "https://raw.githubusercontent.com/VSChina/azureiotdevkit_tools/master/package_azureboard_index.json"
 ```
 ![installation-settings-json]({{"/assets/images/installation-settings-json-win.png" | absolute_url}})

4. In Board Manager, search for **az3166** and install the [latest version]({{"/versions" | absolute_url }}).
 ![installation-az3166]({{"/assets/images/installation-az3166-win.png" | absolute_url}})

### Step 7. Install ST-Link drivers

[ST-Link/V2](http://www.st.com/en/development-tools/st-link-v2.html){:target="_blank"} driver is required to communicate with the IoT DevKit. 

1. Download the driver from [STMicro product page](http://www.st.com/en/embedded-software/stsw-link009.html){:target="_blank"}.

2. Extract the .zip file and double click `stlink_winusb_install.bat` to install:
 ![installation-st-link]({{"/assets/images/installation-st-link-win.png" | absolute_url}})

You now have all the necessary tools and packages installed for Windows.

## macOS

### Step 1. Install Azure CLI 2.0

Follow the [official guide](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli#macos){:target="_blank"} to install Azure CLI 2.0. We recommend install with [Homebrew](https://brew.sh/){:target="_blank"}:

1. If you don't have it already, install Homebrew by following the [Homebrew installation instructions](https://docs.brew.sh/Installation.html){:target="_blank"}.

2. If you have previously installed the CLI manually, follow the [manual uninstall](manual uninstall){:target="blank"} instructions.

3. Update your local Homebrew repositories.
  ```bash
  brew update
  ```

4. Install the `azure-cli` package.
  ```bash
  brew install azure-cli
  ```

### Step 2. Install Arduino IDE

The Visual Studio Code Arduino extension relies on the Arduino IDE.

1. Download the [Arduino IDE for macOS](https://www.arduino.cc/en/Main/Software){:target="_blank"}.

2. Extract downloaded .zip file.

3. Drag and drop `Arduino.app` into Applications folder to install.

### Step 3. Install Visual Studio Code

Download and install [Visual Studio Code for macOS](https://code.visualstudio.com/){:target="_blank"}. This is the primary development tool for building IoT DevKit applications.

### Step 4. Download the latest package

1. Install Node.js. You can use popular macOS package manager [Homebrew](https://brew.sh/){:target="_blank"} or [pre-built installer](https://nodejs.org/en/download/){:target="_blank"} to install it.

2. Download the .zip file that contains required task scripts for IoT DevKit development in VS Code.

  [<i class='fa fa-download'></i> Download](https://aka.ms/devkit/prod/installpackage/mac/latest){: .click-download-tracker .btn .btn--success .btn--large}

  Locate the .zip file and extract it. Then start the **Terminal** app and run the following commands:

  a. Move extracted folder to your macOS user folder:
  ```bash
  mv [.zip extracted folder] ~/azure-board-cli
  cd ~/azure-board-cli
  ```

  b. Install npm packages:
  ```
  npm install
  ```

### Step 5. Install the VS Code extension for Arduino

You can install Azure Marketplace extensions directly in Visual Studio Code.

1. Select the extensions icon in the left pane, search for **Arduino**, and then select **Install**:
    ![installation-extensions]({{"/assets/images/installation-extensions-mac.png" | absolute_url}})

2. Open **Preference > Settings**, add a line within the **USER SETTINGS** pane and save:
  ```json
  "arduino.path": "/Applications"
  ```

  **Note:** Make sure the Arduino path is set the right location you have installed your Arduino IDE.
  {: .notice}

### Step 6. Install the IoT DevKit board package

Add the IoT DevKit board by using Board Manager in Visual Studio Code.

1. Use `Cmd+Shift+P` to open the command palette, type **Arduino**, and then find and select **Arduino: Board Manager**.

2. Select **Additional URLs** at the lower right.
 ![installation-additional-urls]({{"/assets/images/installation-additional-urls-mac.png" | absolute_url}})

3. In the `settings.json` file, add a line within the **USER SETTINGS** pane and save:
 ```json
 "arduino.additionalUrls": "https://raw.githubusercontent.com/VSChina/azureiotdevkit_tools/master/package_azureboard_index.json"
 ```
 ![installation-settings-json]({{"/assets/images/installation-settings-json-mac.png" | absolute_url}})

4. In Board Manager, search for **az3166** and install the [latest version]({{"/versions" | absolute_url }}).
 ![installation-az3166]({{"/assets/images/installation-az3166-mac.png" | absolute_url}})

You now have all the necessary tools and packages installed for macOS.

## Ubuntu

The IoT DevKit development environment can be installed and ran on Linux such as Ubuntu with manual configurations. Here is a detailed instructions from [Noel Bundick](https://twitter.com/acanthamoeba) about it: [Using the Azure IoT DevKit with Linux](https://www.noelbundick.com/2018/01/28/Using-the-Azure-IoT-DevKit-with-Linux/).

## Next Steps

You are all set! It's time to build your first IoT application by following instructions in [Projects Catalog]({{"/docs/projects/" | absolute_url }}).
