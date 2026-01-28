# Example JSON Structures - REFERENCE GUIDE

**📍 Examples are now distributed throughout the mod structure!**

Instead of looking at this file, **navigate to the actual folders** where files belong:

- **Item definitions**: `Server/Item/Items/` (see EXAMPLE_* files)
- **Recipes**: `Server/Item/Recipes/` (see EXAMPLE_* files)
- **Drop tables**: `Server/Drops/Item/` (see EXAMPLE_* files)
- **Hitboxes**: `Server/Item/Block/Hitboxes/` (see EXAMPLE_* files)
- **Resource types**: `Server/Item/ResourceTypes/` (see EXAMPLE_* files)
- **Interactions**: `Server/Item/Interactions/` (see EXAMPLE_* files)

Each folder has:
1. **EXAMPLE_* files** - Copy these and modify them
2. **README.md** - Explains what goes in that folder and how to use it

---

## Items

**📍 Location**: `Server/Item/Items/` folder

Example files:
- `EXAMPLE_BasicItem.json` - Simple generic item
- `EXAMPLE_FoodItem.json` - Consumable food
- `EXAMPLE_BlockItem.json` - Placeable block
- `EXAMPLE_BlockWithInteraction.json` - Block with interaction
- `README.md` - Complete guide for items

### Basic Item
```json
{
  "TranslationProperties": {
    "Name": "server.items.BasicItem.name",
    "Description": "server.items.BasicItem.description"
  },
  "Parent": "Template_Generic",
  "Icon": "Icons/ItemsGenerated/BasicItem.png",
  "ResourceTypes": [{"Id": "Miscellaneous"}],
  "Quality": "Common",
  "Consumable": false,
  "Interactions": {},
  "BlockType": {
    "Material": "Empty",
    "DrawType": "Model",
    "CustomModel": "Resources/BasicItem.blockymodel",
    "CustomModelTexture": [
      {
        "Texture": "Resources/BasicItem_Texture.png",
        "Weight": 1
      }
    ],
    "HitboxType": "Item_Small",
    "ParticleColor": "#FFFFFF",
    "CustomModelScale": 1.0
  },
  "Scale": 1,
  "IconProperties": {
    "Scale": 1.0,
    "Rotation": [0, 0, 0],
    "Translation": [0, 0]
  }
}
```

### Food Item (Consumable)
```json
{
  "TranslationProperties": {
    "Name": "server.items.Apple.name",
    "Description": "server.items.Apple.description"
  },
  "Parent": "Template_Food",
  "Icon": "Icons/ItemsGenerated/Apple.png",
  "ResourceTypes": [{"Id": "Foods"}],
  "Quality": "Common",
  "Consumable": true,
  "Interactions": {},
  "BlockType": {
    "Material": "Empty",
    "DrawType": "Model",
    "CustomModel": "Resources/Apple.blockymodel",
    "CustomModelTexture": [
      {
        "Texture": "Resources/Apple_Texture.png",
        "Weight": 1
      }
    ],
    "HitboxType": "Item_Small",
    "ParticleColor": "#FF5555",
    "CustomModelScale": 0.8
  },
  "Scale": 1,
  "IconProperties": {
    "Scale": 0.9,
    "Rotation": [15, 45, 20],
    "Translation": [0, -2]
  }
}
```

### Block Item
```json
{
  "TranslationProperties": {
    "Name": "server.items.CustomBlock.name",
    "Description": "server.items.CustomBlock.description"
  },
  "Parent": "Template_Block",
  "Icon": "Icons/ItemsGenerated/CustomBlock.png",
  "ResourceTypes": [{"Id": "Blocks"}],
  "Quality": "Common",
  "Consumable": false,
  "Interactions": {
    "Hit": {
      "RequiredTool": "Pickaxe",
      "DropContainer": "Drops_CustomBlock"
    }
  },
  "BlockType": {
    "Material": "Stone",
    "DrawType": "Model",
    "CustomModel": "Resources/CustomBlock.blockymodel",
    "CustomModelTexture": [
      {
        "Texture": "Resources/CustomBlock_Texture.png",
        "Weight": 1
      }
    ],
    "HitboxType": "Block_Full",
    "ParticleColor": "#999999",
    "CustomModelScale": 1.0
  },
  "Scale": 1,
  "IconProperties": {
    "Scale": 1.0,
    "Rotation": [0, 45, 0],
    "Translation": [0, 0]
  }
}
```

## Recipes

### Simple Crafting Recipe
```json
{
  "RecipeName": "Recipe_SimpleItem",
  "CraftingStation": "Workbench",
  "Inputs": [
    {"ItemId": "RawMaterial", "Quantity": 2},
    {"ItemId": "Tool", "Quantity": 1}
  ],
  "Outputs": [
    {"ItemId": "CraftedItem", "Quantity": 1}
  ],
  "CraftingTime": 3.0
}
```

### Cooking Recipe
```json
{
  "RecipeName": "Recipe_CookedFood",
  "CraftingStation": "Stove",
  "Inputs": [
    {"ItemId": "RawFood", "Quantity": 1},
    {"ItemId": "Water", "Quantity": 1}
  ],
  "Outputs": [
    {"ItemId": "CookedFood", "Quantity": 1}
  ],
  "CraftingTime": 5.0
}
```

### Multi-Input Recipe
```json
{
  "RecipeName": "Recipe_ComplexItem",
  "CraftingStation": "AdvancedWorkbench",
  "Inputs": [
    {"ItemId": "Material1", "Quantity": 3},
    {"ItemId": "Material2", "Quantity": 2},
    {"ItemId": "Material3", "Quantity": 1},
    {"ItemId": "Catalyst", "Quantity": 1}
  ],
  "Outputs": [
    {"ItemId": "ComplexItem", "Quantity": 1},
    {"ItemId": "Byproduct", "Quantity": 1}
  ],
  "CraftingTime": 8.0
}
```

## Drop Tables

### Single Drop
```json
{
  "Container": {
    "Type": "Single",
    "Weight": 100.0,
    "Item": {
      "ItemId": "YourItem"
    }
  }
}
```

### Multiple Possible Drops
```json
{
  "Container": {
    "Type": "Multiple",
    "Containers": [
      {
        "Type": "Single",
        "Weight": 50.0,
        "Item": {
          "ItemId": "CommonDrop",
          "Quantity": 1
        }
      },
      {
        "Type": "Single",
        "Weight": 30.0,
        "Item": {
          "ItemId": "UncommonDrop",
          "Quantity": 1
        }
      },
      {
        "Type": "Single",
        "Weight": 20.0,
        "Item": {
          "ItemId": "RareDrop",
          "Quantity": 1
        }
      }
    ]
  }
}
```

### Variable Quantity Drop
```json
{
  "Container": {
    "Type": "Single",
    "Weight": 100.0,
    "Item": {
      "ItemId": "Seeds",
      "Quantity": {
        "Min": 2,
        "Max": 5
      }
    }
  }
}
```

## Hitboxes

### Small Item Hitbox
```json
{
  "Bounds": {
    "X": 8,
    "Y": 8,
    "Z": 8
  }
}
```

### Medium Item Hitbox
```json
{
  "Bounds": {
    "X": 12,
    "Y": 12,
    "Z": 12
  }
}
```

### Full Block Hitbox
```json
{
  "Bounds": {
    "X": 16,
    "Y": 16,
    "Z": 16
  }
}
```

### Custom Hitbox
```json
{
  "Bounds": {
    "X": 14,
    "Y": 10,
    "Z": 14
  }
}
```

## Resource Types

### Basic Resource Type
```json
{
  "Name": "YourResourceType",
  "Color": "#FFFFFF",
  "Weight": 1
}
```

### Colored Resource Type
```json
{
  "Name": "RareOre",
  "Color": "#FF00FF",
  "Weight": 3
}
```

## Translations (server.lang format)

### Basic Item Translations
```
server.items.YourItem.name=Your Item Name
server.items.YourItem.description=Description of your item.
```

### Complete Item Set Translation
```
server.items.BasicItem.name=Basic Item
server.items.BasicItem.description=A simple item for crafting.

server.items.AdvancedItem.name=Advanced Item
server.items.AdvancedItem.description=A more complex item created through advanced recipes.

server.items.RareItem.name=Rare Item
server.items.RareItem.description=An extremely rare and valuable item.
```

### Recipe Translations
```
server.recipes.Recipe_SimpleItem.name=Simple Item Recipe
server.recipes.Recipe_SimpleItem.description=Combine materials at a workbench.
```

### Effect Translations
```
server.effects.Poison.name=Poison
server.effects.Poison.description=Take damage over time.

server.effects.Regeneration.name=Regeneration
server.effects.Regeneration.description=Restore health over time.
```

## Blocks with Interactions

### Harvestable Block
```json
{
  "TranslationProperties": {
    "Name": "server.items.HarvestableBlock.name",
    "Description": "server.items.HarvestableBlock.description"
  },
  "Parent": "Template_Block",
  "Icon": "Icons/ItemsGenerated/HarvestableBlock.png",
  "ResourceTypes": [{"Id": "Blocks"}],
  "Quality": "Uncommon",
  "Consumable": false,
  "Interactions": {
    "Hit": {
      "RequiredTool": "Axe",
      "DropContainer": "Drops_HarvestableBlock",
      "BreakTime": 2.0
    }
  },
  "BlockType": {
    "Material": "Wood",
    "DrawType": "Model",
    "CustomModel": "Resources/HarvestableBlock.blockymodel",
    "CustomModelTexture": [
      {
        "Texture": "Resources/HarvestableBlock_Texture.png",
        "Weight": 1
      }
    ],
    "HitboxType": "Block_Full",
    "ParticleColor": "#8B4513",
    "CustomModelScale": 1.0
  },
  "Scale": 1,
  "IconProperties": {
    "Scale": 1.0,
    "Rotation": [0, 45, 0],
    "Translation": [0, 0]
  }
}
```

## Color Reference (Hex Codes)

Common colors for particle effects and resource types:
- Red: `#FF0000`
- Green: `#00FF00`
- Blue: `#0000FF`
- Yellow: `#FFFF00`
- Purple: `#FF00FF`
- Cyan: `#00FFFF`
- Orange: `#FFA500`
- Brown: `#8B4513`
- Gray: `#808080`
- White: `#FFFFFF`
- Black: `#000000`

## Tips for Using These Templates

1. **Copy entire JSON blocks** - It's easier to edit than build from scratch
2. **Always update these fields** at minimum:
   - Translation keys (Name, Description)
   - File paths (Icon, CustomModel, CustomModelTexture)
   - ItemIds (in recipes and drops)
   - Quality levels

3. **Validate JSON** - Use jsonlint.com if you get errors
4. **Test incrementally** - Create one item, test it, then create more
5. **Keep consistent naming** - Use same patterns throughout your mod

## Common Mistakes to Avoid

- ❌ Forgetting commas between JSON properties
- ❌ Using single quotes instead of double quotes
- ❌ Forgetting translation key definitions in server.lang
- ❌ Referencing files that don't exist
- ❌ Mixing up ItemId and file names
- ❌ Using spaces in file names
- ❌ Not matching icon file names to item IDs

Good luck with your mod configurations!
