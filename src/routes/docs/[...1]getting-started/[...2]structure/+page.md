---
title: File Structure
description: Prismarine's file structure.
---

# {$frontmatter.title}

Prismarine uses a simple project file structure:

```text
my-project/
├─ pack/
│  ├─ minecraft/
│  ├─ ..a_mod/
├─ source/
│  ├─ ..source_file.aseprite
│  ├─ ..source_file.psd
├─ .prisignore
├─ prismarine.toml
├─ README.md
├─ LICENSE
```

## `pack`

This is the directory that will be zipped, including all of its children. You can include
everything normally, except for the `pack.mcmeta` file, as this will be auto-generated on
export.

## `source`

This directory should include any project files you use to create any assets that go in
the `pack` directory. For example, Photoshop files, Aseprite files, GIMP files, etc.

## `.prisignore`

This file lists all the files and directories you don't want to be included in the final
export. It uses the same format as [.gitignore](https://git-scm.com/docs/gitignore).

## `prismarine.toml`

This is the configuration file for your project. It includes the following:

-   `name` - Project name. This will be used to name the file when exporting.
-   `mc_description` - Description of the project. This will be used in the `pack.mcmeta`
    file, so you can add formatting as well.
-   `pack_version` - Project version. This will be used to name the file when exporting.
-   `minecraft_version` - The targetted Minecraft version. This will be used to infer
    the `pack_format` for the `pack.mcmeta` file.
-   `license` - The name or SPDX identifier of the license your pack is under. Defaults
    to ARR (All Rights Reserved).
