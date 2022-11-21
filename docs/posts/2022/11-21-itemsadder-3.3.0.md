---
template: giscus.html

title: What is new in ItemsAdder v3.3.0?
description: "A quick overview over the changes made in ItemsAdder v3.3.0"

tags:
  - minecraft
  - resource-packs
  - itemsadder
---

[^1]: Generated using https://tree.nathanfriend.io

!!! note "Important"
    This blog post will only cover the main differences between ItemsAdder v3.3.0 and its previous versions.  
    Creating items has remained the same with the only difference being the [new folder structure](#structure).
    
    To learn how to create custom items, blocks, etc. read my previous post about ItemsAdder:
    
    [Understand and create custom ItemsAdder Items](../10-29-itemsadder){ .md-button }

## Structure

ItemsAdder has a main folder called `contents` that contains all the configuration files and assets for the custom items, blocks, models, furnitures, etc.  
The structure may look confusing at first, but at closer inspection is it a lot easier to understand and use.

Let's show a quick example using the `_iainternal` folder as an example[^1]:  
```
contents/
└── _iainternal/
    ├── configs/
    │   ├── dictionaries/
    │   │   ├── de.yml
    │   │   ├── en.yml
    │   │   ├── es.yml
    │   │   ├── fr.yml
    │   │   ├── it.yml
    │   │   ├── pt.yml
    │   │   ├── tr.yml
    │   │   └── zh_cn.yml
    │   ├── lang_overwrite/
    │   │   ├── dyed.yml
    │   │   └── merchant.yml
    │   ├── guis.yml
    │   └── icons.yml
    └── resourcepack/
        ├── _iainternal/
        │   └── (ommited for simplicity)
        └── pack.mcmeta # This is only part of _iainternal
```
As you can see is the folder containing two main folders: `configs` and `resourcepack`

`configs` is the equivalent to the previous `items_packs` folder, meaning it contains the YAML files to define your custom items, blocks, etc. to add.  
`resourcepack` is equal to the previous `resource_pack` folder, meaning it's the main place containing your assets. The structure is the same as the usual `assets/namespace/...` one, which means that `resourcepack/example/texture/` is equal to `assets/example/texture/` in a resource pack.

## How to migrate

While ItemsAdder v3.3.0 supports the old folder structure is it still recommended to convert your old content to the new one.  
One thing you need to keep in mind is, that ItemsAdder no longer creates generated model files, meaning you can/should delete any `auto_generated/` folder to save space.

Migrating is relatively easy:

- Copy any YAML files and folders located at `ItemsAdder/data/items_packs/namespace/` to `ItemsAdder/contents/namespace/configs/` (Replace `namespace` with the respective namespace used).
- Copy any asset files and folders located at `ItemsAdder/data/resource_pack/assets/namespace/` to `ItemsAdder/contents/namespace/resourcepack/namespace/` (Replace `namespace` with the respective namespace used).
- Rename `data` to any name (i.e. `data-old`) to prevent ItemsAdder from using the old folders.
- Remove any `auto_generated` folders to save disk-space.

!!! warning "Important!"
    `z_iainternal` was renamed to `_iainternal` so make sure to rename that folder to avoid duplicate files being generated.  
    Also, update any use of `z_iainternal` in the YAML files, including `ia_gui.yml` in the ItemsAdder folder.

Once you completed these steps should you be able to just `/iazip` everything to get the new resource pack. The new location of the resource pack is at `ItemsAdder/output/generated.zip`  
ItemsAdder will report any issues during the Zip file creation, so keep an eye out for those.

## Common issues

Here is a list of common issues and how you could solve them.

### Image not found for font_image 'namespace:image'. assets/namespace/textures/path/image.png { #image-not-found }

This error may happen if ItemsAdder is unable to find a font image defined in one of the YAML configurations (or in one of its own files such as `ia_gui.yml`).  
Usually this happens if you renamed a folder, but didn't update any files mentioning the font image with the old namespace. So, to fix it, check any files that may use the old namespace and update them.

### Invalid character in folders/name of file: /contents/namespace/resourcepack/namespace/textures/path/image.png { #invalid-character }

This error is given whenever invalid characters are used in a file or folder path.  
Common invalid characters are:

- Uppercase letters (i.e. `textures/someFolder/image.png`)
- Spaces (i.e. `textures/path/invalid image name.png`)
- Non alphanummeric characters (à, é, è, etc.)

To fix this, simply remove or replace invalid characters with accepted ones (alphanummeric characters (a-z, 0-9), hyphens (-) and underscores (\_)).  
Remember to also check any YAML or model files that may use the path and/or file names and correct those too.

### File compression skipped: duplicate entry: assets/path/file.json { #file-compression-skipped }

This error means that a file with the exact same name and exact same location already exists in the provided folder and that ItemsAdder skipped any attempts at compressing (minifying) it.  
This usually only happens with Minecraft files.

If you're sure that these files are only from ItemsAdder (Have been generated by it on older versions) can you safely delete them. Otherwise, leave them in to avoid any issues.

--8<-- "footnotes.md"
