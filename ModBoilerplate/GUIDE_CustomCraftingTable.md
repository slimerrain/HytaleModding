# Custom Crafting Table - Complete Example Guide

## Overview

This guide shows how to create a complete custom crafting table (workbench) that players can place and use.

## Files You Need to Create

### 1. **Item Definition** (`Server/Item/Items/MyWorkbench.json`)

Copy from: `EXAMPLE_CustomCraftingTable.json`

Key points:
- Parent must be `Template_Block`
- Must have both "Hit" (for breaking) and "Interact" (for using) interactions
- `CraftingStationId` in Interact section: `"CustomWorkbench"`
- Icon path: `Icons/ItemsGenerated/MyWorkbench.png`
- Model path: `Resources/MyWorkbench.blockymodel`

```json
{
  "TranslationProperties": {
    "Name": "server.items.MyWorkbench.name",
    "Description": "server.items.MyWorkbench.description"
  },
  "Parent": "Template_Block",
  "Icon": "Icons/ItemsGenerated/MyWorkbench.png",
  "ResourceTypes": [{"Id": "Blocks"}, {"Id": "Crafting"}],
  "Quality": "Uncommon",
  "Interactions": {
    "Hit": {
      "RequiredTool": "Pickaxe",
      "DropContainer": "Drops_MyWorkbench",
      "BreakTime": 2.0
    },
    "Interact": {
      "InteractionId": "Interact_MyWorkbench",
      "OpenUI": "CraftingMenu",
      "CraftingStationId": "MyWorkbench"
    }
  },
  "BlockType": {
    "Material": "Wood",
    "DrawType": "Model",
    "CustomModel": "Resources/MyWorkbench.blockymodel",
    "CustomModelTexture": [{"Texture": "Resources/MyWorkbench_Texture.png", "Weight": 1}],
    "HitboxType": "Block_Full",
    "ParticleColor": "#8B4513",
    "CustomModelScale": 1.0
  }
}
```

### 2. **Hitbox Definition** (`Server/Item/Block/Hitboxes/MyWorkbench_Hitbox.json`)

Copy from: `EXAMPLE_CraftingTableHitbox.json`

```json
{
  "Bounds": {
    "X": 16,
    "Y": 14,
    "Z": 16
  }
}
```

### 3. **Interaction Definition** (`Server/Item/Interactions/Interact_MyWorkbench.json`)

Copy from: `EXAMPLE_CraftingTableInteraction.json`

The `CraftingStationId` must match what's in the item definition.

```json
{
  "InteractionType": "Interact",
  "BlockId": "MyWorkbench",
  "CraftingStationId": "MyWorkbench",
  "OpenUI": "CraftingMenu",
  "Sound": "UIOpen",
  "RequiresFacing": "Top",
  "InteractionRange": 5.0
}
```

### 4. **Drop Table** (`Server/Drops/Item/Drops_MyWorkbench.json`)

Copy from: `EXAMPLE_CraftingTableDrop.json`

```json
{
  "Container": {
    "Type": "Single",
    "Weight": 100.0,
    "Item": {
      "ItemId": "MyWorkbench"
    }
  }
}
```

### 5. **Translations** (Add to `Server/Languages/en-US/server.lang`)

```
server.items.MyWorkbench.name=My Custom Workbench
server.items.MyWorkbench.description=A specialized crafting table for unique recipes.
```

### 6. **Recipes** (Create in `Server/Item/Recipes/`)

Any recipe using this table must reference the `CraftingStationId`:

```json
{
  "RecipeName": "Recipe_SpecialItem",
  "CraftingStation": "MyWorkbench",
  "Inputs": [
    {"ItemId": "Material1", "Quantity": 3},
    {"ItemId": "Material2", "Quantity": 2}
  ],
  "Outputs": [
    {"ItemId": "SpecialItem", "Quantity": 1}
  ],
  "CraftingTime": 5.0
}
```

### 7. **3D Model** (Save to `Common/Resources/`)

Create in Hytale's Block Editor:
1. Design your workbench
2. Export as `MyWorkbench.blockymodel`
3. Create texture as `MyWorkbench_Texture.png`

### 8. **Icon** (Save to `Common/Icons/ItemsGenerated/`)

Create a 64x64 PNG icon: `MyWorkbench.png`

## Summary of ID References

Everything connects through these IDs:

| File | ID Used | Purpose |
|------|---------|---------|
| Item Definition | `CraftingStationId: "MyWorkbench"` | Identifies the crafting table |
| Interaction | `CraftingStationId: "MyWorkbench"` | Must match item definition |
| Recipes | `CraftingStation: "MyWorkbench"` | References the crafting station |
| Drop Table | `ItemId: "MyWorkbench"` | Drops when broken |
| Translations | `server.items.MyWorkbench.*` | Display text |

**All "MyWorkbench" references must be identical!**

## Step-by-Step Creation Process

```
Step 1: Choose a Name
  → "MyWorkbench" (use descriptive names like "VineWeaver", "CrimsonForge")

Step 2: Create Item Definition
  → Copy EXAMPLE_CustomCraftingTable.json
  → Replace all instances of "CustomWorkbench" with "MyWorkbench"
  → Change icon/model paths to match

Step 3: Create Hitbox
  → Copy EXAMPLE_CraftingTableHitbox.json
  → Save as MyWorkbench_Hitbox.json
  → Adjust dimensions if needed

Step 4: Create Interaction
  → Copy EXAMPLE_CraftingTableInteraction.json
  → Save as Interact_MyWorkbench.json
  → Update CraftingStationId to "MyWorkbench"

Step 5: Create Drop Table
  → Copy EXAMPLE_CraftingTableDrop.json
  → Save as Drops_MyWorkbench.json
  → Update ItemId to "MyWorkbench"

Step 6: Add Translations
  → Add 2 lines to server.lang
  → server.items.MyWorkbench.name=...
  → server.items.MyWorkbench.description=...

Step 7: Create Recipes
  → Create recipe files in Server/Item/Recipes/
  → Reference "MyWorkbench" in CraftingStation

Step 8: Create 3D Model
  → Use Block Editor
  → Export as MyWorkbench.blockymodel
  → Create MyWorkbench_Texture.png

Step 9: Create Icon
  → Design 64x64 PNG
  → Save as MyWorkbench.png

Step 10: Test
  → Load mod in Hytale
  → Place crafting table
  → Use it to craft
  → Break it and verify drop
```

## Common Customization

### Different Tool Required

```json
"Hit": {
  "RequiredTool": "Axe",  // Changed from Pickaxe
  "DropContainer": "Drops_MyWorkbench"
}
```

### Multiple Textures

```json
"CustomModelTexture": [
  {"Texture": "Resources/MyWorkbench_Main.png", "Weight": 1},
  {"Texture": "Resources/MyWorkbench_Alt.png", "Weight": 0.5}
]
```

### Requires Specific Level

```json
"Interactions": {
  "Interact": {
    "RequiredLevel": 20,
    "CraftingStationId": "MyWorkbench"
  }
}
```

## Tips

- Use consistent naming (e.g., "VineWeaver" not "vine_weaver")
- Group related recipes by crafting station
- Create multiple tiers (Basic, Intermediate, Advanced)
- Make icons distinctive so players can identify stations
- Test all recipes at your custom table
- Consider crafting times relative to item value

## Validation Before Release

- [ ] Item loads without errors
- [ ] Can place workbench in world
- [ ] Can right-click to open crafting menu
- [ ] Recipes show in crafting menu
- [ ] Can actually craft recipes
- [ ] Workbench drops when broken
- [ ] No console errors
- [ ] Icon displays correctly
- [ ] Name and description are correct
