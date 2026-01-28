# Server/Item/Recipes

This folder contains crafting, cooking, and other recipe definitions.

## What Goes Here

JSON files that define recipes for your items. Each recipe specifies:
- Input items and quantities
- Output items and quantities
- Required crafting station
- Crafting time

## File Naming Convention

```
Recipe_ItemName.json
EXAMPLE_*.json  (Examples - see files in this folder)
```

## Recipe Structure

```json
{
  "RecipeName": "Recipe_ItemName",
  "CraftingStation": "Workbench",
  "Inputs": [
    {"ItemId": "Material1", "Quantity": 2},
    {"ItemId": "Material2", "Quantity": 1}
  ],
  "Outputs": [
    {"ItemId": "CraftedItem", "Quantity": 1}
  ],
  "CraftingTime": 3.0
}
```

## Common Crafting Stations

```
Workbench              - General crafting
Stove                  - Cooking food
Furnace                - Smelting ores
Loom                   - Textile crafting
Anvil                  - Metal working
Brewing_Station        - Alchemy/brewing
Woodworking_Bench      - Wood crafting
Cauldron               - Potion making
```

## Example Files in This Folder

- **EXAMPLE_SimpleRecipe.json** - Basic 2-3 item recipe
- **EXAMPLE_CookingRecipe.json** - Cooking at a stove
- **EXAMPLE_MultiInputRecipe.json** - Complex recipe with 4+ inputs

**Copy these and modify for your recipes!**

## Crafting Times

Guide for how long crafting should take:

```
0.5 seconds  - Very quick (simple combination)
1-2 seconds  - Quick (basic crafting)
3-5 seconds  - Normal (standard recipes)
5-10 seconds - Slow (complex items)
10+ seconds  - Very slow (endgame items)
```

## Tips

- Keep early recipes quick (less than 3 seconds)
- Make expensive recipes take longer
- Test that all ItemIds actually exist
- Remember to add output to drops or loot tables
- Avoid circular recipes (A needs B, B needs A)

## Validation Checklist

- [ ] Recipe name is unique
- [ ] CraftingStation exists in game
- [ ] All Input ItemIds exist
- [ ] All Output ItemIds exist
- [ ] Quantities are realistic
- [ ] CraftingTime is reasonable
