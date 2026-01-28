# Server/Item/ResourceTypes

This folder defines resource categories that items belong to (like "Foods", "Ores", "Tools", etc).

## What Goes Here

JSON files that define resource type categories. Items can belong to multiple resource types.

## File Naming Convention

```
ResourceType.json
YourCategory.json
EXAMPLE_*.json  (Examples - see files in this folder)
```

## Resource Type Structure

```json
{
  "Name": "Foods",
  "Color": "#FFAA00",
  "Weight": 1
}
```

## Fields

| Field | Purpose | Example |
|-------|---------|---------|
| `Name` | Category identifier | `"Foods"`, `"Ores"`, `"Weapons"` |
| `Color` | Hex color for UI display | `"#FF0000"` (red) |
| `Weight` | Priority/importance | `1` (normal), `2` (high), `0.5` (low) |

## Example Files in This Folder

- **EXAMPLE_BasicResourceType.json** - White generic resource
- **EXAMPLE_ColoredResourceType.json** - Colored rare resource

## Common Resource Types

```
Foods           - Food items
Ores            - Mining/ore resources
Metals          - Processed metals
Weapons         - Combat weapons
Tools           - Harvesting tools
Armor           - Wearable armor
Blocks          - Placeable blocks
Seeds           - Farming seeds
Ingredients     - Crafting ingredients
Miscellaneous   - Everything else
```

## Color Reference

Common colors:

```
#FF0000 - Red (important, valuable)
#00FF00 - Green (common, nature)
#0000FF - Blue (water, cold)
#FFFF00 - Yellow (light, sun)
#FF00FF - Purple (rare, magic)
#FFA500 - Orange (crafted items)
#808080 - Gray (stone, neutral)
#FFFFFF - White (generic)
#FFD700 - Gold (very valuable)
```

## Using Resource Types

Reference in your item JSON:

```json
{
  "ResourceTypes": [
    {"Id": "Foods"},
    {"Id": "Ingredients"}
  ]
}
```

An item can belong to multiple resource types!

## Tips

- Create categories for logical grouping
- Use consistent naming
- Colors help players identify item types
- Weight determines priority in menus
- Test that items correctly reference categories

## Validation Checklist

- [ ] Resource type name is unique
- [ ] Color is valid hex code
- [ ] Weight is reasonable (0.1 to 3.0)
- [ ] Items reference this type correctly
