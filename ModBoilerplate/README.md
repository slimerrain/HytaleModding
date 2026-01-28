# Hytale Mod Boilerplate

This is a complete boilerplate/template for creating Hytale mods. It includes the full directory structure and example files showing you what needs to be created for each type of content.

## Quick Start

1. Copy this entire folder as a new mod folder
2. Update `manifest.json` with your mod's information
3. Replace "YourItem" references with your actual item names
4. Add your custom assets (models, textures, icons)
5. Flesh out the JSON files with your specific configuration

## Directory Structure Overview

```
ModBoilerplate/
├── manifest.json                 # Mod metadata (REQUIRED - update this first!)
├── Common/                       # Client-side assets
│   ├── Blocks/                   # Block definitions
│   ├── BlockTextures/            # Block texture files
│   ├── Icons/
│   │   └── ItemsGenerated/       # Auto-generated item icons (PNG)
│   ├── Items/                    # Item visual definitions
│   └── Resources/                # 3D models (.blockymodel) and textures
└── Server/                       # Server-side configuration
    ├── Drops/                    # Item drop tables
    ├── Entity/
    │   ├── Effects/              # Status effects
    │   └── Stats/                # Entity stats/attributes
    ├── Item/
    │   ├── Block/
    │   │   └── Hitboxes/         # Block collision hitboxes
    │   ├── Interactions/         # Block interaction definitions
    │   ├── Items/                # Item definitions (MAIN - see details below)
    │   ├── Recipes/              # Crafting/cooking recipes
    │   └── ResourceTypes/        # Resource type definitions
    └── Languages/
        └── en-US/
            └── server.lang       # English translations
```

## File Structure Details

### 1. `manifest.json` (REQUIRED)

**Location:** Root folder

This file defines your mod's metadata and is **required**. Update these fields:

```json
{
  "Group": "YourGroupName",           // Your name/organization
  "Name": "Your Mod Name",             // Display name of the mod
  "Version": "1.0.0",                  // Version number
  "Description": "What it does...",    // Brief description
  "Authors": [
    {
      "Name": "Your Name",
      "Email": "your@email.com",
      "Url": ""
    }
  ],
  "Website": "",                       // Optional: Your website
  "ServerVersion": "",                 // Leave empty for compatibility
  "Dependencies": {},                  // Mods this requires
  "OptionalDependencies": {},          // Optional mod dependencies
  "LoadBefore": {},                    // Mods to load after this one
  "DisabledByDefault": false,          // Start enabled/disabled
  "IncludesAssetPack": true,           // true if you have Common/ assets
  "SubPlugins": []                     // Advanced: leave as []
}
```

### 2. Common Assets (Client-Side)

These files define how items appear and are rendered in the game.

#### **Common/Resources/** (Models and Textures)
- **`.blockymodel` files**: 3D model files for items/blocks (binary format - create in Hytale's Block Editor)
- **`.png` files**: Texture files for models (standard PNG images)

#### **Common/Icons/ItemsGenerated/** (Item Icons)
- Item icons displayed in inventory/UI (PNG files)
- Usually auto-generated or created from 2D artwork
- Named to match your item IDs (e.g., `YourItem.png`)

#### **Common/Blocks/** 
- Block definition files (if creating custom blocks)
- JSON files describing block visual properties

#### **Common/BlockTextures/**
- Texture definitions for blocks
- Maps textures to block faces

#### **Common/Items/**
- Visual item definitions
- References to models and textures

### 3. Server Configuration (Game Logic)

#### **Server/Item/Items/** (MOST IMPORTANT)

Item definition files that configure how items work. Example structure:

```json
{
  "TranslationProperties": {
    "Name": "server.items.YourItem.name",      // Translation key for name
    "Description": "server.items.YourItem.description"  // Translation key
  },
  "Parent": "Template_Generic",                 // Base item type to inherit from
  "Icon": "Icons/ItemsGenerated/YourItem.png", // Icon path
  "ResourceTypes": [{"Id": "YourResourceType"}],// Resource categories
  "Quality": "Common",                          // Rarity (Common, Uncommon, Rare, etc.)
  "Consumable": false,                          // Can it be consumed/eaten?
  "Interactions": {},                           // Block interactions
  "BlockType": {                                // How it renders
    "Material": "Empty",
    "DrawType": "Model",
    "CustomModel": "Resources/YourItem.blockymodel",
    "CustomModelTexture": [
      {
        "Texture": "Resources/YourItem_Texture.png",
        "Weight": 1
      }
    ],
    "HitboxType": "Item_Small",                 // Collision size
    "ParticleColor": "#FFFFFF",                 // Particle effect color
    "CustomModelScale": 1.0                     // Model size multiplier
  },
  "Scale": 1,
  "IconProperties": {
    "Scale": 1.0,
    "Rotation": [0, 0, 0],                      // X, Y, Z rotation
    "Translation": [0, 0]                       // X, Y offset
  }
}
```

**Common Parent Types:**
- `Template_Generic`: Basic item
- `Template_Food`: Consumable food items
- `Template_Tool`: Tools and equipment
- `Template_Block`: Placeable blocks
- `Template_Armor`: Wearable armor

#### **Server/Item/Recipes/** (Crafting Recipes)
JSON files defining recipes for items. Example:

```json
{
  "RecipeName": "YourRecipe",
  "CraftingStation": "WorkbenchId",
  "Inputs": [
    {"ItemId": "ItemA", "Quantity": 2},
    {"ItemId": "ItemB", "Quantity": 1}
  ],
  "Outputs": [
    {"ItemId": "YourItem", "Quantity": 1}
  ],
  "CraftingTime": 5.0
}
```

#### **Server/Item/ResourceTypes/**
Define resource categories items belong to. Example:

```json
{
  "Name": "YourResourceType",
  "Color": "#FFFFFF",
  "Weight": 1
}
```

#### **Server/Item/Block/Hitboxes/**
Define collision boxes for blocks. Example:

```json
{
  "Bounds": {
    "X": 16,
    "Y": 16,
    "Z": 16
  }
}
```

#### **Server/Drops/Item/**
Define what items drop when blocks are broken. Example:

```json
{
  "Container": {
    "Type": "Single",
    "Weight": 100.0,
    "Item": {
      "ItemId": "YourItemId"
    }
  }
}
```

**Drop Types:**
- `Single`: One item option
- `Multiple`: Multiple possible outcomes (weight-based)
- `Range`: Variable quantity drops

#### **Server/Languages/en-US/server.lang**
Translation file for item names and descriptions:

```
server.items.YourItem.name=Your Item Name
server.items.YourItem.description=A detailed description of the item.
server.effects.ExampleEffect.name=Effect Name
```

#### **Server/Entity/Effects/**
Define status effects/buffs that can affect entities. JSON configuration files.

#### **Server/Entity/Stats/**
Define entity attributes and statistics. JSON configuration files.

#### **Server/Item/Interactions/**
Define how blocks respond to player interaction. JSON configuration files.

## Creating Your Mod: Step-by-Step

### Step 1: Update metadata
```
1. Edit manifest.json with your mod name, version, and author info
```

### Step 2: Add your items
```
1. Create JSON files in Server/Item/Items/ for each item
2. Define item properties (parent type, icon, model, etc.)
3. Add corresponding translation keys to server.lang
```

### Step 3: Create visual assets
```
1. Add .blockymodel files to Common/Resources/
2. Add texture .png files to Common/Resources/
3. Add item icons to Common/Icons/ItemsGenerated/
```

### Step 4: Define drops/interactions
```
1. Create drop files in Server/Drops/ to define what blocks drop
2. Create interaction files in Server/Item/Interactions/ for block behaviors
```

### Step 5: Add recipes (if applicable)
```
1. Create recipe JSON files in Server/Item/Recipes/
2. Reference workbench IDs and input/output items
```

## Asset Creation Notes

### Creating Models
- Use Hytale's Block Editor to create `.blockymodel` files
- Save models to `Common/Resources/`
- Export at appropriate scale (typically 1 unit = 1 pixel)

### Creating Textures
- 16x16, 32x32, or 64x64 PNG files recommended
- Save to `Common/Resources/`
- Use transparent backgrounds (PNG with alpha channel)
- Colors should match Hytale's 16-bit color palette for consistency

### Creating Icons
- 64x64 PNG icons for inventory display
- Save to `Common/Icons/ItemsGenerated/`
- Name matching your item ID for auto-detection

## Translation System

Use translation keys in your JSON files (e.g., `server.items.YourItem.name`), then define the actual text in `server.lang`:

```
server.items.YourItem.name=Display Name Here
server.items.YourItem.description=Description text here.
```

This allows easy multi-language support by creating additional language files:
- `Server/Languages/fr-FR/server.lang` (French)
- `Server/Languages/de-DE/server.lang` (German)
- etc.

## Testing Your Mod

1. Copy the mod folder to your Hytale mods directory:
   - Windows: `C:\Users\<YourUsername>\AppData\Roaming\Hytale\UserData\Mods\`
   - Mac: `~/Library/Application Support/Hytale/UserData/Mods/`
   - Linux: `~/.local/share/Hytale/UserData/Mods/`

2. Launch Hytale and enable your mod in the mod menu

3. Check the game log for any errors:
   - Usually located in the Hytale config folder

## Common Issues & Solutions

### "Mod fails to load"
- Check `manifest.json` for syntax errors (valid JSON required)
- Ensure `IncludesAssetPack` is set to `true` if you have Common/ assets
- Check for missing translation keys in server.lang

### "Items don't appear"
- Verify item JSON files are in `Server/Item/Items/`
- Check translation keys match entries in server.lang
- Ensure icon file exists at the specified path
- Verify icon filename matches (case-sensitive on some systems)

### "Models don't render"
- Check that .blockymodel files exist at the specified path
- Verify texture PNG files exist
- Ensure model scale is appropriate (0.5-2.0 usually works)

### "Drops don't work"
- Create drop files matching your block IDs
- Ensure drop files reference correct ItemIds
- Check Container Type is valid (Single, Multiple, Range)

## Advanced Configuration

### Item Parent Types (Template Inheritance)
Items inherit properties from parent templates. Common ones:
- `Template_Generic` - Basic item with no special properties
- `Template_Food` - Consumable food, has hunger/saturation values
- `Template_Tool` - Tools with durability and special properties
- `Template_Block` - Placeable blocks with physics
- `Template_Armor` - Wearable armor with defense values
- `Template_Weapon` - Combat weapons with damage stats

Inherit properties by setting `"Parent": "TemplateNameHere"`

### Custom Block Types
For blocks, you can customize:
- `DrawType`: "Model", "Sprite", "Liquid", etc.
- `Material`: Block physics (Empty, Stone, Wood, etc.)
- `HitboxType`: Collision size (Item_Small, Item_Medium, Block_Full, etc.)
- `ParticleColor`: Hex color for particles when broken

## Where to Get Help

- Hytale modding documentation: Check the official Hytale forums
- Example mods: Study the BrewsSteeps and LeafJuice mods in this workspace
- Game logs: Check for detailed error messages in the game's log files

## Tips for Success

1. **Start small**: Create one item first, test it, then expand
2. **Use consistent naming**: Follow the `Category_ItemName` pattern
3. **Keep translation keys organized**: Use dot notation (e.g., `server.items.category.name`)
4. **Test frequently**: Load your mod after each major change
5. **Reference examples**: Study existing mods for structure patterns
6. **Use proper JSON**: Validate JSON files with a JSON validator if you get errors

## Example Mod Progression

```
Version 1.0:
- 1 custom item
- 1 crafting recipe
- Basic translations

Version 1.1:
- 2-3 more items
- Interaction systems
- Custom workbench

Version 2.0:
- Full item set
- Complete crafting chains
- Custom blocks and effects
```

Good luck with your mod! Happy modding! 🎮
