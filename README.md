# hhdmac

Homecoming Hero Designer for Mac

# Download & Install

Prepare your Mac environment. Get Homecoming Hero Designer running locally on your own Mac before trying to distribute it to others.

```
curl -o ${HOME}/Downloads/hhdsetup.exe https://imaginarydevelopment.github.io/imaginary-hero-designer/publish/setup.exe
# Set Wine variables
export WINEPREFIX=${HOME}/.wine32
export WINEARCH="win32"
# Install Brew. Skip this step if you already have Brew.
usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
# Set up Wine prerequisites
brew install wine winetricks
winetricks dotnet472
# Install Homecoming Hero Designer
wine ~/Downloads/hhdsetup.exe
```

This should install & launch Homecoming Hero Designer successfully. If it does not launch, the rest of these instructions will not work.

# Bottle

Find the path to Hero Designer.exe.

```
find ~/.wine32 -name "Hero Designer.exe" | tail -1 | sed 's/Hero Designer.exe//' | pbcopy
```

Open WineBottler.  Set the following options:

1. Prefix template: new prefix (default)
2. Program Installation: 
  1. Click "select file"
  2. Press command-shift-g, then command-v in the dialog box.
  3. Click "go".
  4. Click "Hero Designer.exe"
  5. Set "Installation Mode" to "copy file (Program) and all files in the folder to the App Bundle"
  6. Set System Version Info to xp
  7. Include Mono (dotnet472 fails installation without it)
  8. Include Gecko (dotnet472 fails without it)
  9. Select Remove Users
  10. Select Remove Installers
3. Program Execution: Leave at defaults
4. Winetricks: dotnet472
5. App Bundle:
  1. Self-contained: click the "Include Wine.app" check mark
  2. Copyright @ Homecoming Servers
  3. Identifier: homecoming.hero.designer
  4. Category Type: Games
  5. Codesign Identity: blank
6. Silent Install: Selected. Makes bottling this app much faster & more reliable, as dotnet472 requires multiple reboots from .Net 4.5 to 4.6 to 4.7.2.


