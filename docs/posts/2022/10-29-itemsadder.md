---
template: giscus.html

title: Understand and create custom ItemsAdder Items
description: "A detailed guide on understanding how to create custom items for the plugin ItemsAdder."

date: '29.10.2022'

tags:
  - minecraft
  - resource-packs
  - itemsadder
---

[^1]: https://itemsadder.devs.beer/
[^2]:
    Custom blocks are bound to certain limits. As an example will `REAL_NOTE` blocks not allow transparent textures or open sides that would expose a covered block face, as MC won't render those usually covered, resulting in an X-Ray effect.  
    `REAL_TRANSPARENT` is a workaround for this case.
[^3]: https://blockbench.net

[ia_block_types]: https://itemsadder.devs.beer/plugin-usage/adding-content/item-properties/blocks#type

In this blog post will I try my very best to teach you how to understand the general structure of ItemsAdder and how you can add your own custom Items (Either only with textures or with custom models).

I want to mention that I will only cover the very basics of how to make items and blocks. I will **not** cover how to add custom durability, effects, sounds, etc. Refer to the ItemsAdder Wiki[^1] for more info.

## General Structure

First things first, what is the general structure of ItemsAdder?  
All important stuff is handled inside `/plugins/ItemsAdder/`. When opening that folder is it first overwhelming given the amount of folders and files present. For our purposes will only the `data/` folder be of importance to us, so you can discard the other folders and files for now.

When opening the folder you will find two folders in it: `items_packs/` and `resource_pack`

### `items_packs`

This folder contains all the YAML files used to create custom items, blocks, furniture and similar. It's the main place for configuration that doesn't require altering of Model files.

The general structure of this folder is as follows:

```
items_packs/
 |
 |- :namespace # This can be any name
 |   |
 |   |- some_file.yml
 |   |- folder/ # additional folders are allowed
 |       |
 |       |- other_file.yml
 |
 |- z_iainternal/
     |
     |- ... # Internal stuff used by ItemsAdder itself
```

The structure is fairly simple, as its only purpose is to hold the configuration files and nothing more.

### `resource_pack`

This folder contains all the necessary files to create a valid resource pack to use, including the final `pack.zip` file when using `/iazip`.  
You'll notice that this folder has a `assets/` folder.

Looking into said folder may reveal a structure similar to this one:

```
resource_pack/
 |
 |- assets/
 |   |
 |   |- minecraft/
 |   |   |
 |   |   |- ... # This contains Minecraft-related files
 |   |
 |   |- z_iainternal/
 |       |
 |       |- ... # Internal stuff used by ItemsAdder itself
 |
 |- index.html
 |- pack.mcmeta
```

If you ever worked with a resource pack before should the structure of `resource_pack` look familiar to you, especially with the `pack.mcmeta` present.  
This is because this folder is the final resource pack structure inside the Zip file, meaning that the structure in it mimics Minecraft's main structure.

## Creating a basic Item (2D Item) { #creating-an-item }

Let's quickly create a new item. It should just be a normal item with a special texture and no real feature.

It's a good idea to first create the necessary folders for the textures and files to use.  
In my example will I use the name `myitem` as the namespace to use. This means that the folder structures may look like this:

```
data/
 |
 |- items_packs/
 |   |
 |   |- myitem/
 |
 |- resource_pack/
     |
     |- assets/
         |
         |- myitem/
```

As you can see do we create new folders called `myitem` inside `items_packs` and `resource_pack/assets/`.  
The reason why `resource_pack` has it inside the `assets` folder is, that MC is always checking `assets/:namespace/` for textures, models and similar when any given path is prefixed with a namespace (i.e. `myitem:some/path`).

The next step I usually do is to first add the assets. In our case would it just be a PNG file of the item.  
In this example am I calling it `dummy.png`.

Since it is a texture will we need to add a `textures` folder inside the `assets/myitem/` directory, as MC checks `assets/:namespace/textures/` for any texture file. For better organisation will I also add an extra `item/` folder to it.  
This means, that the new structure is like this:

```
data/
 |
 |- items_packs/
 |   |
 |   |- myitem/
 |
 |- resource_pack/
     |
     |- assets/
         |
         |- myitem/
             |
             |- textures/
                 |
                 |- item/
                     |
                     |- dummy.png
```

!!! tip "Pro-tips"
    
    - Keep file and folder names lowercased. Minecraft doesn't like uppercased names that much.
    - You can always use extra folders inside the textures folder to further organize your files. Just make sure to also adjust any texture paths used.

Now with this completed is the next step to actually tell ItemsAdder to add it as a new item.  
To do this, I create a new YAML file inside `items_packs/myitem/`. Any name for the file works, but it should be kept lowercase and not contain any spaces or weird characters.

To keep it simple will I name it `dummy.yml` and fill it with the following:

```yaml title="dummy.yml"
info:
  namespace: myitem # (1)
items:
  dummy: # (2)
    display_name: "Dummy Item" # (3)
    resource:
      material: PAPER # (4)
      generate: true # (5)
      textures: # (6)
      - 'item/dummy.png'
```

1.  This is used as the custom namespace for ItemsAdder commands such as `/iaget` but also other things
2.  This can be any name. Just make sure it's lowercased. It will be used as identifier for the custom item (i.e. `myitem:dummy`)
3.  The name that will be displayed when obtaining the item.
4.  The Base item that is used. ItemsAdder will assign a custom model data for the item to override the texture/model. This has to be a valid Minecraft item.
5.  `generate: true` tells ItemsAdder to auto-generate the necessary model file for this item. This should be used if you're not using a custom model.
6.  This sets the textures to use. For a normal item is only one texture needed, but blocks can have up to 6 (One for each side). The path is relative to `assets/:namespace/textures/`.

With this setup am I telling ItemsAdder to create a new entry for the item PAPER with the texture located at `assets/myitem/textures/`.  
After saving the changes can I now run `/iazip` to update the resource pack. Afterwards should I be able to get the item using `/iaget myitem:dummy`

## Creating a Block

Creating a block is for the most part the same as [creating an item](#creating-an-item) so please read that part first.

In this example am I using the same folder structure, with the difference that the PNG files for the block are inside `assets/myitem/textures/block/` and that I'm using multiple ones.

All we need to do now is add some extra stuff to it:

```yaml title="dummy_block.yml"
info:
  namespace: myitem
items:
  dummy_block:
    display_name: "Dummy Block"
    resource:
      material: PAPER # (1)
      generate: true
      textures: # (2)
      - 'block/dummy_down.png'
      - 'block/dummy_east.png'
      - 'block/dummy_north.png'
      - 'block/dummy_south.png'
      - 'block/dummy_up.png'
      - 'block/dummy_west.png'
    specific_properties:
      block: # (3)
        type: REAL_NOTE # (4)
        break_particle: ITEM # (5)
```

1.  It's recommended to use an item and not a block here, to avoid glitchy placement behaviour. The item will look like a block in the inventory.
2.  In this example am I setting individual textures for each side of the block. The order is actually important and the names should tell it. If each side has the same texture will you only need one texture to be set here.
3.  This tells ItemsAdder that this item should be placable like an actual block. This will also change the texture displayed in the Inventory to that of a full block.
4.  The `type` defines what Vanilla block should be used. Recommended is to use `REAL_NOTE`. What types are available can be found in the [Wiki][ia_block_types]
5.  Sets the particle to use for when the block is broken. `ITEM` tells ItemsAdder to use the textures set for the item.

This is already enough to create a custom block to use. All that is left is to update the resource pack (`/iazip`) and obtaining the item (`/iaget myitem:dummy_block`)

## Custom models (i.e. for furniture) { #custom-models }

There are cases where you want to create your own models for an item or a block[^2].  
Let's say we want to use a custom model for our `dummy` item.

In order to do this will we first need to create the actual Model file to use. A recommended software to use for this is Blockbench[^3] as it allows a relatively easy creation of MC block/item models.

To not make this guide too long will I skip the entire model creation process.  
Just assume we still have the same Texture file in the same directory (`assets/myitem/textures/dummy.png`) and that we create a JSON model file which may look something similar to this:

```jsonc title="dumy_model.json"
{
  "credit": "Made with Blockbench",
  "textures": {
    "0": "myitem:item/dummy",
    "particle": "myitem:item/dummy"
  },
  "elements": [
    {
      // Here would be all the element parts of our model
    }
  ]
}
```

!!! warning "Important"
    Model files follow the same structure with textures as MC does, meaning that you need to prefix the texture path with your namespace (in my case `myitem:`) and also provide a path relative to `assets/:namespace/textures/`.  
    Additionally do you **not** have to append a `.png` extension to the paths. MC automatically assumes PNG files being used.
    
    Blockbench should deal with those things by itself, as long as you're using a proper folder structure for the textures.

We would put this file into a new folder called `models`. To add more structure am I adding an extra folder called `item`, so the current structure would look similar to this:

```
data/
 |
 |- items_packs/
 |   |
 |   |- myitem/
 |       |
 |       |- dummy_item.yml
 |       |- dummy_block.yml
 |
 |- resource_pack/
     |
     |- assets/
         |
         |- myitem/
             |
             |- models/ # Newly added folder
             |   |
             |   |- item/
             |       |
             |       |- dummy_model.json
             |
             |- textures/
                 |
                 |- item/
                 |   |
                 |   |- dummy.png
                 |
                 |- block/
                     |
                     |- dummy_down.png
                     |- dummy_east.png
                     |- dummy_north.png
                     |- dummy_south.png
                     |- dummy_up.png
                     |- dummy_west.png
```

Since we just edit an existing item can we open the `dummy_item.yml` file and adjust a few things:

```yaml title="dummy_item.yml"
info:
  namespace: myitem
items:
  dummy:
    display_name: "Dummy Item"
    resource:
      material: PAPER
      generate: false
      model_path: "item/dummy_model"
```

What you may have noticed is, that `generate` is set to `false`. This is important since we want to use our own model file and keeping this option set to true would cause ItemsAdder to still auto-generate and use its own mode file.  
Additionally have I removed the `textures` option and instead added the `model_path` one. This is due to the model file containing all the texture settings to use, so we don't have to provide them here again.

If you've done everything correctly can you now run `/iazip` and the item should use the actual model you set (You may require to clear the cache tho).

--8<-- "footnotes.md"
