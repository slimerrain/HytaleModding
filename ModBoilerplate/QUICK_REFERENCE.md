# Quick Reference Guide

A fast lookup guide for common mod development tasks.

## Quick Start (5 Minutes)

1. **Copy this folder** as your new mod
2. **Edit manifest.json**:
   - Change `Group` to your name
   - Change `Name` to your mod name
   - Change `Version` to 1.0.0
3. **Create your first item**:
   - Copy `Server/Item/Items/ExampleItem.json` 
   - Rename and edit it
4. **Add a translation**:
   - Add entry to `Server/Languages/en-US/server.lang`
5. **Add an icon** (PNG file):
   - Add to `Common/Icons/ItemsGenerated/`
   - Name must match item ID

## File Checklist by Feature

### Adding Items
- [ ] Create JSON in `Server/Item/Items/ItemName.json`
- [ ] Add icon to `Common/Icons/ItemsGenerated/ItemName.png`
- [ ] Add translations to `server.lang`
- [ ] Test in game

### Adding Recipes
- [ ] Create JSON in `Server/Item/Recipes/Recipe_ItemName.json`
- [ ] Add translations to `server.lang`
- [ ] Verify input/output ItemIds exist
- [ ] Test in game

### Adding Blocks
- [ ] Create item JSON in `Server/Item/Items/BlockName.json` (with Parent: Template_Block)
- [ ] Add drop file in `Server/Drops/Item/Drops_BlockName.json`
- [ ] Add hitbox in `Server/Item/Block/Hitboxes/BlockName_Hitbox.json` (if needed)
- [ ] Add 3D model to `Common/Resources/BlockName.blockymodel`
- [ ] Add texture to `Common/Resources/BlockName_Texture.png`
- [ ] Add icon to `Common/Icons/ItemsGenerated/BlockName.png`
- [ ] Add translations to `server.lang`

### Adding 3D Models
- [ ] Create model in Hytale Block Editor
- [ ] Export as `.blockymodel` to `Common/Resources/`
- [ ] Create corresponding texture `.png` in same folder
- [ ] Reference in item JSON under `CustomModel`
- [ ] Reference texture under `CustomModelTexture`

### Adding Effects/Buffs
- [ ] Create JSON in `Server/Entity/Effects/EffectName.json`
- [ ] Add translations to `server.lang`
- [ ] Reference in items or recipes
- [ ] Test effect application

## Common JSON Patterns

### Minimum Item JSON
```json
{
  "TranslationProperties": {
    "Name": "server.items.YourItem.name",
    "Description": "server.items.YourItem.description"
  },
  "Parent": "Template_Generic",
  "Icon": "Icons/ItemsGenerated/YourItem.png",
  "Quality": "Common"
}
```

### Minimum Recipe
```json
{
  "RecipeName": "Recipe_YourItem",
  "CraftingStation": "Workbench",
  "Inputs": [{"ItemId": "Input", "Quantity": 1}],
  "Outputs": [{"ItemId": "YourItem", "Quantity": 1}],
  "CraftingTime": 1.0
}
```

### Minimum Drop
```json
{
  "Container": {
    "Type": "Single",
    "Weight": 100.0,
    "Item": {"ItemId": "YourItem"}
  }
}
```

## Translation Reference

### Template
```
server.items.ItemName.name=Display Name
server.items.ItemName.description=Item description.
```

### Categories
- `server.items.*` - Items
- `server.recipes.*` - Recipes
- `server.effects.*` - Effects
- `server.blocks.*` - Blocks
- `server.stats.*` - Statistics

## Quality Levels

```
"Quality": "Common"      # Basic items
"Quality": "Uncommon"    # Better items
"Quality": "Rare"        # Valuable items
"Quality": "Epic"        # Very valuable
"Quality": "Legendary"   # Rarest items
```

## Parent Templates

| Parent | Use For | Example |
|--------|---------|---------|
| Template_Generic | Basic items | Crafting materials, components |
| Template_Food | Consumables | Apples, bread, potions |
| Template_Tool | Tools | Pickaxes, axes, shovels |
| Template_Block | Placeable blocks | Stone, dirt, custom blocks |
| Template_Armor | Wearable armor | Helmets, chestplates, boots |
| Template_Weapon | Combat weapons | Swords, bows, hammers |

## Common Hitbox Types

| Type | Size | Use For |
|------|------|---------|
| Item_Small | 8x8x8 | Seeds, coins, small items |
| Item_Medium | 12x12x12 | Ingredients, basic items |
| Item_Large | 14x14x14 | Tools, weapons |
| Block_Full | 16x16x16 | Full-size blocks |
| Block_Half | 16x16x8 | Half-height blocks, slabs |
| Block_Custom | Custom | Custom sized blocks |

## Crafting Stations

Common workbench IDs to use in recipes:
- `Workbench` - Basic crafting table
- `Stove` - Cooking
- `Furnace` - Smelting
- `Loom` - Textile crafting
- `Anvil` - Metal working
- `Brewing_Station` - Alchemy/brewing
- `Woodworking_Bench` - Wood crafting

## Tools for Harvesting

Use in block interactions:
- `Pickaxe` - For stone/ore
- `Axe` - For wood
- `Shovel` - For dirt/sand
- `Hoe` - For farming
- `Knife` - For plants
- `Hands` - Bare hands

## Color Codes (Hex)

Quick reference for common colors:

```
#FFFFFF - White
#000000 - Black
#FF0000 - Red
#00FF00 - Green
#0000FF - Blue
#FFFF00 - Yellow
#FF00FF - Magenta
#00FFFF - Cyan
#FFA500 - Orange
#800080 - Purple
#FFC0CB - Pink
#A52A2A - Brown
#808080 - Gray
```

Use for `ParticleColor` in item JSON or resource types.

## File Naming Convention

**Pattern:** `Prefix_ItemName.json`

Examples:
- `Drops_BlockName.json` - Drop table
- `Recipe_ItemName.json` - Recipe
- `Effect_StatusName.json` - Effect
- `Stats_AttributeName.json` - Statistic
- `Hitbox_BlockName.json` - Collision box
- `Interaction_BlockName.json` - Interaction

## Testing Checklist

- [ ] All JSON files are valid (no syntax errors)
- [ ] All translation keys are defined in server.lang
- [ ] All referenced files exist (icons, models, textures)
- [ ] All ItemIds in recipes exist as items
- [ ] All ItemIds in drops exist as items
- [ ] Mod loads without errors in game log
- [ ] Items appear in creative inventory
- [ ] Recipes work at correct station
- [ ] Drops occur when blocks break

## Common Errors & Solutions

| Error | Cause | Solution |
|-------|-------|----------|
| Mod won't load | JSON syntax error | Validate JSON at jsonlint.com |
| Items not appearing | Missing translation | Check server.lang has all keys |
| Icon not showing | File doesn't exist | Verify path and filename exact |
| Recipe broken | ItemId doesn't exist | Check item name in Items/ |
| Drop broken | Wrong path format | Use forward slashes, not backslashes |
| Model not rendering | Model path wrong | Check .blockymodel exists in Resources/ |

## Directory Paths Reference

| Content | Path |
|---------|------|
| Item icons | `Common/Icons/ItemsGenerated/` |
| 3D models | `Common/Resources/` |
| Textures | `Common/Resources/` |
| Item definitions | `Server/Item/Items/` |
| Recipes | `Server/Item/Recipes/` |
| Drop tables | `Server/Drops/Item/` |
| Block hitboxes | `Server/Item/Block/Hitboxes/` |
| Block interactions | `Server/Item/Interactions/` |
| Translations | `Server/Languages/en-US/` |
| Effects | `Server/Entity/Effects/` |
| Stats | `Server/Entity/Stats/` |

## Useful Commands

### Validate JSON
Use an online JSON validator: https://jsonlint.com/

### Find All TODO Items
Search your mod folder for:
- `YourItem` - Template placeholder
- `YourGroup` - Group name placeholder
- `TODO` - Developer notes

### Create Icon from Model
If creating an icon from 3D model:
1. Render model in Block Editor
2. Adjust rotation in `IconProperties`
3. Set appropriate `Scale` (usually 0.8-1.0)
4. Take screenshot
5. Crop to square and save as PNG

## Version Numbering

Follow semantic versioning:

```
Version Format: MAJOR.MINOR.PATCH

1.0.0 = First release
1.0.1 = Bug fix
1.1.0 = New features
2.0.0 = Major overhaul
```

Examples:
- `1.0.0` - Initial release
- `1.0.1` - Small fix
- `1.1.0` - Added new items
- `1.2.0` - Added new recipes
- `2.0.0` - Complete rework

## Before Distribution

- [ ] Version number updated in manifest
- [ ] All features working without errors
- [ ] Documentation complete
- [ ] Tested with other mods
- [ ] Icon/banner image created
- [ ] Release notes written
- [ ] No console errors/warnings

---

**Stuck?** Check README.md for detailed explanations or EXAMPLES.md for code samples!
