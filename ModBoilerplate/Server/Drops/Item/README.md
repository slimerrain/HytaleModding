# Server/Drops/Item

This folder contains drop tables defining what items are dropped when blocks are broken.

## What Goes Here

JSON files that define what items drop from each block type. Each file specifies:
- Drop type (single item, multiple options, variable quantity)
- Item ID and quantity
- Drop probability/weight

## File Naming Convention

```
Drops_BlockName.json
EXAMPLE_*.json  (Examples - see files in this folder)
```

The filename should match what's referenced in your block's interaction.

## Drop Types

### Single Drop
One item always drops:

```json
{
  "Container": {
    "Type": "Single",
    "Weight": 100.0,
    "Item": {"ItemId": "YourItem"}
  }
}
```

### Multiple Possible Drops
Pick one of several options (weight-based):

```json
{
  "Container": {
    "Type": "Multiple",
    "Containers": [
      {"Type": "Single", "Weight": 50.0, "Item": {"ItemId": "CommonDrop", "Quantity": 1}},
      {"Type": "Single", "Weight": 30.0, "Item": {"ItemId": "RareDrop", "Quantity": 1}},
      {"Type": "Single", "Weight": 20.0, "Item": {"ItemId": "VeryRareDrop", "Quantity": 1}}
    ]
  }
}
```

### Variable Quantity
Drop random amount:

```json
{
  "Container": {
    "Type": "Single",
    "Weight": 100.0,
    "Item": {
      "ItemId": "Seeds",
      "Quantity": {"Min": 2, "Max": 5}
    }
  }
}
```

## Example Files in This Folder

- **EXAMPLE_SingleDrop.json** - One item always drops
- **EXAMPLE_MultiplePossibleDrops.json** - Several options (weighted)
- **EXAMPLE_VariableQuantityDrop.json** - Random quantity drops

**Copy these and modify for your blocks!**

## Weight System

Weights determine drop probability in Multiple drops:

```
Total weight = 50 + 30 + 20 = 100

CommonDrop: 50/100 = 50% chance
RareDrop: 30/100 = 30% chance  
VeryRareDrop: 20/100 = 20% chance
```

## Tips

- Make common drops frequent (40-60%)
- Make rare drops infrequent (5-15%)
- Use variable quantities for resources (2-5)
- Keep drop quantities realistic
- Test drops in game to verify

## Validation Checklist

- [ ] Filename matches reference in block interaction
- [ ] All ItemIds exist
- [ ] Drop type is valid (Single, Multiple, or has Quantity)
- [ ] Weights add up to reasonable total
- [ ] Quantities are appropriate
- [ ] Tested in game
