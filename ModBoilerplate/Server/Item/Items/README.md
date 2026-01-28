# Server/Item/Items

This is the **most important folder** in your mod. Item definitions control everything about how items work in Hytale.

## What Goes Here

JSON files that define each item in your mod. Each file describes:
- Item display name and description
- Parent type (what template to inherit from)
- Icon and 3D model
- Item properties and behavior
- Resource category
- Quality level

## File Naming Convention

```
YourItemName.json
EXAMPLE_*.json  (Examples - see files in this folder)
```

Keep names descriptive and match your item ID.

## Item Structure Example

```json
{
  "TranslationProperties": {
    "Name": "server.items.YourItem.name",
    "Description": "server.items.YourItem.description"
  },
  "Parent": "Template_Generic",
  "Icon": "Icons/ItemsGenerated/YourItem.png",
  "ResourceTypes": [{"Id": "YourCategory"}],
  "Quality": "Common",
  "Consumable": false,
  "BlockType": {
    "Material": "Empty",
    "DrawType": "Model",
    "CustomModel": "Resources/YourItem.blockymodel",
    "CustomModelTexture": [{"Texture": "Resources/YourItem_Texture.png", "Weight": 1}],
    "HitboxType": "Item_Small",
    "ParticleColor": "#FFFFFF"
  }
}
```

## Parent Templates

Choose the right parent for your item type:

| Parent | Use For |
|--------|---------|
| `Template_Generic` | Basic items, materials, components |
| `Template_Food` | Consumable food items |
| `Template_Tool` | Tools with durability |
| `Template_Block` | Placeable blocks |
| `Template_Armor` | Wearable armor |
| `Template_Weapon` | Combat weapons |

## Quality Levels

```
"Quality": "Common"      # Basic items
"Quality": "Uncommon"    # Better items
"Quality": "Rare"        # Valuable items
"Quality": "Epic"        # Very valuable
"Quality": "Legendary"   # Rarest items
```

## Hitbox Types

```
"HitboxType": "Item_Small"    # 8x8x8 (seeds, coins)
"HitboxType": "Item_Medium"   # 12x12x12 (ingredients)
"HitboxType": "Item_Large"    # 14x14x14 (tools)
"HitboxType": "Block_Full"    # 16x16x16 (full blocks)
"HitboxType": "Block_Half"    # 16x16x8 (slabs)
```

## Example Files in This Folder

- **EXAMPLE_BasicItem.json** - Simple generic item
- **EXAMPLE_FoodItem.json** - Consumable food
- **EXAMPLE_BlockItem.json** - Placeable block
- **EXAMPLE_BlockWithInteraction.json** - Block with special interaction
- **ExampleItem.json** - Original basic example

**Copy these files and modify them for your items!**

## Quick Checklist for New Items

- [ ] Created JSON file in this folder
- [ ] Set correct "Parent" template type
- [ ] Added translation keys
- [ ] Created icon PNG file
- [ ] Added entry to server.lang for name/description
- [ ] Set Quality level
- [ ] Specified HitboxType
- [ ] (Optional) Created 3D model and texture

## Tips

- Start simple - create basic items before complex ones
- Copy an example that's similar to what you want
- Test frequently - load mod after each new item
- Keep naming consistent throughout your mod
- Use meaningful translation keys
