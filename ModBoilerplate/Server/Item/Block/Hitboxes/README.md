# Server/Item/Block/Hitboxes

This folder contains collision box definitions for blocks and items.

## What Goes Here

JSON files that define hitbox dimensions for your items and blocks.

## File Naming Convention

```
ItemName_Hitbox.json
BlockName_Hitbox.json
EXAMPLE_*.json  (Examples - see files in this folder)
```

## Hitbox Structure

```json
{
  "Bounds": {
    "X": 8,
    "Y": 8,
    "Z": 8
  }
}
```

The values are dimensions in pixels (where 16 = full block size).

## Common Hitbox Sizes

### Items

| Type | Size | ItemIds | Use For |
|------|------|---------|---------|
| **Small** | 8x8x8 | Item_Small | Seeds, coins, small items |
| **Medium** | 12x12x12 | Item_Medium | Ingredients, basic items |
| **Large** | 14x14x14 | Item_Large | Tools, weapons, bulky items |

### Blocks

| Type | Size | ItemIds | Use For |
|------|------|---------|---------|
| **Full** | 16x16x16 | Block_Full | Standard blocks, full-size |
| **Half** | 16x16x8 | Block_Half | Slabs, stairs, half-height |
| **Thin** | 16x2x16 | Block_Thin | Plates, thin blocks |
| **Custom** | Variable | Block_Custom | Special shaped blocks |

## Example Files in This Folder

- **EXAMPLE_SmallItem.json** - 8x8x8 (seeds, coins)
- **EXAMPLE_MediumItem.json** - 12x12x12 (ingredients)
- **EXAMPLE_FullBlock.json** - 16x16x16 (standard blocks)
- **EXAMPLE_CustomHitbox.json** - 14x10x14 (custom size)

## Designing Custom Hitboxes

For custom shapes:

1. Think about the item/block visually
2. Estimate how much space it takes up
3. Use measurements relative to full block (16 pixels)
4. Round to even numbers
5. Test in-game to verify

**Examples:**

```
Thin platform:    16x2x16
Narrow pillar:    6x16x6
Wide plank:       16x4x16
Slope:            16x8x16
Small container:  10x10x10
Large pot:        12x14x12
```

## Using Hitboxes

Reference in your item's Interactions:

```json
{
  "Interactions": {
    "Hit": {
      "HitboxId": "MyBlock_Hitbox"
    }
  }
}
```

Or create a separate file and reference by ID.

## Tips

- Hitboxes affect how items stack/pack
- Smaller = more compact, more can fit
- Larger = more space-consuming, harder to handle
- Test hitboxes in-game for proper feel
- Keep consistent with visual size

## Validation Checklist

- [ ] Hitbox matches item/block visual size
- [ ] Dimensions are reasonable
- [ ] All values are positive integers
- [ ] File is referenced correctly in items
