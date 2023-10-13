<img src="assets/logo_128x128.png" align="right" />

# Nefarius' vīcĭus updater agent

[![Build status](https://ci.appveyor.com/api/projects/status/6n8p9r0koqqt1q6m?svg=true)](https://ci.appveyor.com/project/nefarius/vicius) <!-- ![GitHub all releases](https://img.shields.io/github/downloads/nefarius/vicius/total) -->

Nefarius' [nŏvīcĭus](https://latinitium.com/latin-dictionaries/?t=lsn31290) universal software updater agent.

## About

---

*Very* work in progress, do not use 🔥 Star ⭐ it instead to show interest 🤟

---

vīcĭus is a self-contained C++20 executable acting as a software update agent. It can be deployed alongside your product and will take care of periodically checking for newer versions online and notifying the user of pending updates. Its goal is to require the least amount of configuration to get it up and running while providing enough flexibility to be customized for various environments, if desired. It doesn't require any prerequisites being present on the target system and should be able to run on any recent Windows version.

## Features

- No backend application server required  
  All you need on the server-side to get going is a web host supporting delivering static JSON files and you're done. [GitHub Pages](https://pages.github.com/) would be a sufficient free hosting solution where you can upload to and deliver the updater configuration from.
- Self-contained  
  No need to worry if .NET or other runtimes are present on the target machines, everything it needs is delivered in a single Win32 executable.
- (Almost) zero configuration  
  The bare minimum configuration can be provided by simply compiling in the server URL by adjusting the `CustomizeMe.h` header file. This does not mean you need to maintain one build for every product you wanna support; you will get **multi-tenancy out of the box** by simply naming the resulting executable after the following scheme: `manufacturer_product_Updater.exe`, e.g. `nefarius_HidHide_Updater.exe` will build the server path as `https://example.org/api/nefarius/HidHide/updates.json` (or however it is defined in `CustomizeMe.h`) automatically!
- Self-updater  
  Sometimes just the updater process needs an update (e.g. security patches), not the entire product it is watching over. It can update itself if the server-provided instance version is higher than the locally running one.

## TODOs

Non-exhaustive list of things open or in-progress...

- [ ] Finalize REST API design
- [ ] Finalize local updater config JSON format
- [ ] Add self-updater logic
  - With [libPeConv](https://github.com/hasherezade/libpeconv) maybe? Would be cool if we can avoid writing a temporary EXE somewhere
- [ ] [Documentation](https://github.com/nefarius/docs.nefarius.at/tree/nefarius/project/vicius)
- [ ] Finalize UI design
  - [x] `WizardPage::Start`
  - [x] `WizardPage::SingleVersionSummary`
  - [ ] `WizardPage::MultipleVersionsOverview`
  - [x] `WizardPage::DownloadAndInstall`
  - [ ] ...
- [ ] Design Beta-Release support
- [ ] Specify supported Command Line Arguments
- [ ] Make app icon customizable
- [ ] Add "Light" theme
- [ ] Add embedded images support for Markdown widget
- [x] Implement Product Version detection
  - [x] `RegistryValue`
  - [x] `FileVersion`
  - [x] `FileSize`
  - [x] `FileChecksum`
- [ ] Support closing and restarting applications before and after the main update
- [ ] Support running prerequisites installation before main update
- [ ] Support running the update [as Administrator](https://stackoverflow.com/a/4893508)
- [ ] Add some logging

## Sources & 3rd party credits

This tool benefits from these awesome projects ❤ (appearance in no special order):

- [Dear ImGui](https://github.com/ocornut/imgui)
  - [Using Icon Fonts](https://github.com/ocornut/imgui/blob/master/docs/FONTS.md#using-icon-fonts)
- [Simple and Fast Multimedia Library](https://www.sfml-dev.org/)
- [ImGui-SFML](https://github.com/SFML/imgui-sfml)
- [Argh! A minimalist argument handler](https://github.com/adishavit/argh)
- [Markdown for Dear ImGui](https://github.com/juliettef/imgui_markdown)
- [IconFontCppHeaders](https://github.com/juliettef/IconFontCppHeaders)
- [Ruda Font](https://fonts.google.com/specimen/Ruda)
- [Fork Awesome](https://forkaweso.me/Fork-Awesome/)
- [REST client for C++](https://github.com/mrtazz/restclient-cpp)
  - [libcurl](https://curl.se/libcurl/)
- [JSON for Modern C++](https://github.com/nlohmann/json)
- [Magic Enum C++](https://github.com/Neargye/magic_enum)
- [Semantic Versioning for modern C++](https://github.com/Neargye/semver)
- [WinReg](https://github.com/GiovanniDicanio/WinReg)
- [Portable C++ Hashing Library](https://github.com/stbrumme/hash-library)
