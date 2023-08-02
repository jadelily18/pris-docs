---
title: Introduction
description: Prismarine is an easy-to-use application designed for creating, managing, and exporting Minecraft resource packs.
---

# {$frontmatter.title}

{$frontmatter.description} As of now, Prismarine is very incomplete, but in the future will support things
like [Vanilla Tweaks](https://vanillatweaks.net/) and likely, combining resource packs together.

All of the written content on this site, aside from assets I do not own, is licensed under the permissive
[MIT License](https://github.com/jadelily18/pris-docs/tree/main/LICENSE).

## Install

Installation is fairly simple, but does require you to [install Rust](https://www.rust-lang.org/learn/get-started).

Once Rust is installed, since its package manager `Cargo` is installed with it, you can copy and paste the following
command into your terminal to install Prismarine:

```bash copy
cargo install prismarine
```

## Usage

Prismarine's user experience is fairly simple so far and somewhat resembles its inspiration,
[Packwiz](https://github.com/packwiz/packwiz).

### Creating a Project

Once Prismarine is installed, you can run the following command to create a new project called `My Resource Pack` in
a new directory.

```bash copy
prismarine new "My Resource Pack"
```

### Configuration

Once your project is created, you can navigate to that directory and you will find a few files and directories
created for you. We'll only cover three here but you can find information about the others
[here](/docs/getting-started/structure).

-   **[_prismarine.toml_](/docs/getting-started/structure#prismarine-toml) -** This file is your main configuration file
    for your project. It includes the name, version, description, license, and some other required and optional fields.

-   **[_.prisignore_](/docs/getting-started/structure/#prisignore) -** This controls exactly what files are included
    when you export the pack. This file uses the same format as [.gitignore](https://git-scm.com/docs/gitignore).

### Exporting

Exporting is simple! Prismarine essentially zips the `pack` directory and everything in the project directory not
included in [.prisignore](/docs/getting-started/structure/#prisignore) gets included in the final exported
.ZIP file. Writing a `pack.mcmeta` file isn't neccessary (and might result in an error), because Prismarine
automatically generates the file from the metadata in the
[prismarine.toml](/docs/getting-started/structure#prismarine-toml), including the description. Run the following
command in your project directory to export your project to a .ZIP file compatible with Minecraft:

```bash copy
prismarine export
```
