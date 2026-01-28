# Creating a Custom Crafting Table

This folder contains examples for creating custom crafting stations where players can craft items.

## What Goes Here

JSON files that define custom workbenches, forges, looms, and other crafting stations.

## File Naming Convention

```
ItemName_Interaction.json
EXAMPLE_CraftingTableInteraction.json
```

## Crafting Table Structure

A crafting table requires multiple files:

### 1. Item Definition
**Location**: `Server/Item/Items/EXAMPLE_CustomCraftingTable.json`

Defines the table itself:
- Parent: `Template_Block` (it's a placeable block)
- Includes both "Hit" interaction (for breaking) and "Interact" (for using)
- References the crafting station ID in Interact section

### 2. Hitbox Definition
**Location**: `Server/Item/Block/Hitboxes/EXAMPLE_CraftingTableHitbox.json`

Defines collision box:
- Typically 16x14x16 for workbench-style tables
- Slightly shorter (Y=14) to look right proportionally
- Referenced in item's BlockType

### 3. Interaction Definition
**Location**: `Server/Item/Interactions/EXAMPLE_CraftingTableInteraction.json`

Defines what happens when player interacts:
- `CraftingStationId`: Must match the ID used in recipes
- `OpenUI`: Opens the crafting menu
- `RequiresFacing`: Usually "Top" (must click top surface)
- `InteractionRange`: How far player can interact from

### 4. Drop Table
**Location**: `Server/Drops/Item/EXAMPLE_CraftingTableDrop.json`

Defines what drops when broken:
- Always drops the table itself
- Can add secondary drops if desired

### 5. Translations
**Location**: `Server/Languages/en-US/server.lang`

Add entries like:
```
server.items.CustomWorkbench.name=Custom Workbench
server.items.CustomWorkbench.description=A specialized crafting table for advanced items.
```

## Example Crafting Stations

### Basic Workbench
```json
{
  "CraftingStationId": "CustomWorkbench",
  "Name": "Custom Workbench",
  "MaxCraftingSlots": 9,
  "RequiredLevel": 1,
  "RecipeFilter": "YourModRecipes"
}
```

### Advanced Forge
```json
{
  "CraftingStationId": "AdvancedForge",
  "Name": "Advanced Forge",
  "MaxCraftingSlots": 6,
  "RequiredLevel": 20,
  "RecipeFilter": "Metalworking",
  "Temperature": "Hot",
  "FuelRequired": true
}
```

### Specialized Loom
```json
{
  "CraftingStationId": "SpecializedLoom",
  "Name": "Specialized Loom",
  "MaxCraftingSlots": 4,
  "RequiredLevel": 15,
  "RecipeFilter": "TextileCrafting",
  "Speed": 1.5
}
```

## Crafting Station ID

The `CraftingStationId` is crucial - it's what recipes reference:

```json
// In your recipe file:
{
  "RecipeName": "Recipe_AdvancedItem",
  "CraftingStation": "CustomWorkbench",  // Must match the ID!
  "Inputs": [...],
  "Outputs": [...]
}
```

## Tips for Custom Crafting Tables

1. **Unique IDs**: Use descriptive IDs like "VineWeaver", "CrimsonForge"
2. **Themed Recipes**: Group recipes by theme (e.g., "Metalworking", "Alchemy")
3. **Visual Design**: Create distinctive 3D models so tables are recognizable
4. **Progression**: Create multiple tiers (Basic → Advanced → Master)
5. **Clear Names**: Translation keys like "server.items.VineWeaver.name"

## Complete Workflow

```
1. Create item JSON:
   - Use EXAMPLE_CustomCraftingTable.json as template
   - Set unique CraftingStationId
   - Create unique 3D model reference

2. Create hitbox JSON:
   - Use EXAMPLE_CraftingTableHitbox.json as template
   - Adjust dimensions if needed

3. Create interaction JSON:
   - Use EXAMPLE_CraftingTableInteraction.json as template
   - Set CraftingStationId to match item

4. Create drop table JSON:
   - Use EXAMPLE_CraftingTableDrop.json as template

5. Add translations to server.lang:
   - Name of crafting table
   - Description of what it does

6. Create recipes:
   - Reference CraftingStationId in recipe
   - Add to Server/Item/Recipes/

7. Create 3D model:
   - Design in Block Editor
   - Export to Common/Resources/

8. Create icon:
   - Design or render icon
   - Save as PNG to Common/Icons/ItemsGenerated/

9. Test:
   - Place crafting table
   - Try crafting recipes
   - Break and check drops
```

## Validation Checklist

- [ ] CraftingStationId is unique
- [ ] Item JSON references correct crafting station
- [ ] Interaction JSON has matching CraftingStationId
- [ ] All recipes reference correct CraftingStationId
- [ ] Drop table returns the crafting table item
- [ ] Translations are defined for name and description
- [ ] 3D model is created and referenced
- [ ] Icon PNG exists in correct folder
- [ ] Hitbox dimensions are appropriate
- [ ] Tested in-game: can place, interact, and craft

## Example File References

- **EXAMPLE_CustomCraftingTable.json** - Complete item definition
- **EXAMPLE_CraftingTableHitbox.json** - Collision box
- **EXAMPLE_CraftingTableInteraction.json** - Interaction behavior
- **EXAMPLE_CraftingTableDrop.json** - Drop when broken
