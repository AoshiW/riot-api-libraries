# Public Libraries for the Riot Games API

## Table of Contents
1. [Introduction](#introduction)
2. [How It Works](#how-it-works)
2. [I Want to Include My Library!](#i-want-to-include-my-library)
3. [My Library's Information is Wrong/Outdated](#my-librarys-information-is-wrongoutdated)
4. [Troubleshooting](#troubleshooting)
5. [Future Work](#future-improvementssuggestions)

## Introduction
This repository is the home of the configuration files that power the `!libs` command for BottyMcBotFace on the Riot Games API Developer Community (https://discord.gg/riotgamesdevrel)

The aim of this repository is to provide a semi-automated, centralized way for 3rd Party Library Creators to manage the exposure of their libraries to other 3rd Party Developers.

## How It Works
### Directory Structure
The `libraries` directory contains language-specific subdirectories. Within these sub-directories are JSON files that contain library configurations. 

The filename is the name of the repository, **lowercased and with all non-alphanumeric characters removed.**. If the filename already exists (aka there's another library with the same name), simply add a number to the end of your filename (e.g. `lolfakejavalib1.json`).

#### Example
For a Java library called `LoL-Fake-Java-Lib`, it's configuration would live at `libraries/java/lolfakejavalib.json`

### File Structure
Each JSON file should consist of a single `RepoObject` JSON object with the following properties:

#### RepoObject
- `owner` [**string**] - The GitHub account that owns the repository
- `repo` [**string**] - The name of the repository
- `description` [**string**] _(Optional)_ -  A description of the library. If omitted, the repository description will be used instead
- `language` [**string**] - The programming language of the library
- `links` [**array**] - An array of `RepoLink` objects
- `metadata` [**object**] - An object containing metadata on the library.
- `tags` [**array**] - An array of strings indicating which features are supported by the library. This array can contain any tags, but only the following are official:
  - `v4` - Include if the library supports `v4` of the Riot Games API. [BottyMcBotFace](https://github.com/Querijn/BottyMcBotface) will only show libraries that have the `v4` tag in all channels that don't have other tags (see below)
  - `v5` - Include if the library supports `v5` of the Riot Games API. You should still include the `v4` tag
  - `lol` - Include if the library supports the LoL APIs. However, only libraries with the tag `v4` will show up in [#lol-dev](https://discord.com/channels/187652476080488449/379429593829867521)
  - `lcu` - Include if the library supports the LCU API. Libraries with this tag will show up in [#lcu-api](https://discord.com/channels/187652476080488449/516802588805431296)
  - `ingame` - Include if the library supports the Ingame API. Libraries with this tag will show up in [#ingame-api](https://discord.com/channels/187652476080488449/543112946402721832)
  - `replay` - Include if the library supports the Replay API
  - `tft` - Include if the library supports the TFT APIs. Libraries with this tag will show up in [#tft-dev](https://discord.com/channels/187652476080488449/595727408058073090)
  - `lor` - Include if the library supports the LoR APIs. Libraries with this tag will show up in [#lor-dev](https://discord.com/channels/187652476080488449/633905002976378881)
  - `val` - Include if the library supports the Valorant APIs. Libraries with this tag will show up in [#val-dev](https://discord.com/channels/187652476080488449/694820049063510026)
  - `rso` - Include if the library supports RSO. Libraries with this tag will show up in [#rso-dev](https://discord.com/channels/187652476080488449/946641562757107782)
  - `rate-limiting` - Include if the library natively handles rate limiting

#### RepoLink
- `name` [**string**] - The display name of the link
- `url` [**string**] - The URL of the link

#### Example
lolfakejavalib.json
```
{
    "owner": "WxWatch",
    "repo": "LoL-Fake-Java-Lib",
    "description": "This is a fake Java library for the Riot Games API",
    "language": "Java",
    "links": [
        {
            "name": "Documentation",
            "url": "https://github.com/WxWatch"
        }
    ],
    "metadata": {
        "version": "1.2.0"
    },
    "tags": [
        "v4",
        "rate-limiting"
    ]
}
```

## I Want to Include My Library!
Awesome! Simply create a Pull Request that adds a file with your library's configuration to the appropriate folder (if your language's folder isn't there, feel free to create it!). Once we verify that everything is correct, we'll merge it in and you're all set!

## My Library's Information is Wrong/Outdated
It's simple to fix! Simply create a Pull Request that updates the configuration file for your library. Once we verify that everything is correct, we'll merge it in and you're all set!

## Troubleshooting
For any specific issues / feature requests, you can create a Github Issue or reach out to WxWatch on the [Riot API Community Discord](https://discord.gg/riotgamesdevrel)

## Future Improvements/Suggestions
- ~~With the upcoming deprecation of `pre-v3` APIs, a way for libraries to be marked as `supporting v3 `.~~ Done!
- Remove the `language` property and have the updater rely on the directory name to know the language.
- A more robust way to show what APIs a library supports
- A way for libraries to show any additional features it may have (rate limiter, etc.)
- Support for libraries not hosted on Github

## Disclaimer
Riot API Libraries Repository isn’t endorsed by Riot Games and doesn’t reflect the views or opinions of Riot Games
or anyone officially involved in producing or managing League of Legends. League of Legends and Riot Games are
trademarks or registered trademarks of Riot Games, Inc. League of Legends © Riot Games, Inc.
