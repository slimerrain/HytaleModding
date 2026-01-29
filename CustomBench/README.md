# Custom Crafting Bench Mod for Hytale

## Description
This mod adds a custom Advanced Workbench to Hytale with unique crafting categories and recipes.

## Features
- **Advanced Workbench**: A new crafting station with three specialized categories:
  - Advanced Crafting: For crafting other benches and advanced items
  - Special Items: For unique crafted items with special properties
  - Custom Tools: For enhanced tools and equipment

- **Upgradeable Bench**: The workbench has 3 tiers with increasing crafting speed
  - Tier 1: Base crafting speed
  - Tier 2: 20% faster crafting
  - Tier 3: 40% faster crafting

## How to Craft the Advanced Workbench
Requires a regular Workbench and the following materials:
- 6x Wood Trunk
- 4x Rock
- 2x Iron Bar

## Sample Recipes
The mod includes three example recipes:
1. **Enhanced Pickaxe**: Crafted from Iron and Copper bars
2. **Builders Bench**: Requires wood, iron, and rock
3. **Special Hammer**: Made from copper, wood, and linen

## Installation
1. Copy the `CustomBench` folder to your Hytale mods directory:
   - Windows: `%AppData%\Roaming\Hytale\UserData\Mods\`
2. Launch Hytale
3. The mod will be automatically loaded

## File Structure
```
CustomBench/
├── manifest.json                    # Mod metadata
├── Common/                          # Client-side assets
│   ├── Blocks/
│   │   └── Benches/                # 3D models and textures
│   └── Icons/                      # Item and category icons
└── Server/                          # Server-side configuration
    ├── Item/
    │   ├── Items/Bench/            # Bench item definition
    │   └── Recipes/                # Crafting recipes
    └── Languages/
        └── en-US/                  # English translations
```

## Customization
You can add your own recipes by creating new JSON files in the `Server/Item/Recipes/` folder. Each recipe should specify:
- Input items and quantities
- Output items
- Bench requirement (use `CustomBench_AdvancedWorkbench` as the bench ID)
- Crafting category (one of the three bench categories)
- Crafting time in seconds

Example recipe format:
```json
{
  "Input": [
    {
      "ItemId": "ItemName",
      "Quantity": 1
    }
  ],
  "PrimaryOutput": {
    "ItemId": "OutputItem",
    "Quantity": 1
  },
  "Output": [
    {
      "ItemId": "OutputItem",
      "Quantity": 1
    }
  ],
  "BenchRequirement": [
    {
      "Type": "Crafting",
      "Categories": ["CustomBench_Advanced_Crafting"],
      "Id": "CustomBench_AdvancedWorkbench"
    }
  ],
  "TimeSeconds": 5
}
```

## Version History
- 1.0.0: Initial release

## Credits
Created using the Hytale Modding API, based on game assets and reference from existing mods.

## License
This mod is provided as-is for educational and entertainment purposes.
