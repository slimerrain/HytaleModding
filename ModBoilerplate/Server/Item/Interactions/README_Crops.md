# Creating a Custom Crop

This folder contains examples for creating custom crops that players can farm.

## What Goes Here

JSON files that define crop interactions like harvesting, replanting mechanics, and growth conditions.

## File Naming Convention

```
CropName_Interaction.json
EXAMPLE_CropInteraction.json
```

## Crop System Structure

A custom crop requires multiple files spread across different folders:

### 1. Seed Item Definition
**Location**: `Server/Item/Items/EXAMPLE_CustomCropSeed.json`

The item you plant:
- Parent: `Template_Seed`
- Properties include `CropType` (the crop identifier)
- `GrowthTime`: Growth duration in seconds (300 = 5 minutes)
- `Stages`: Number of growth stages (4 is typical, 1-6 possible)
- `RequiresTilling`: If true, needs tilled soil
- `BonemealBoost`: Growth speed multiplier from bonemeal

### 2. Crop Product Definition
**Location**: `Server/Item/Items/EXAMPLE_CustomCropProduct.json`

The item you harvest:
- Parent: `Template_Generic`
- Can have `FoodValue` and `SaturationValue` if edible
- Referenced in drop table

### 3. Harvest Interaction
**Location**: `Server/Item/Interactions/EXAMPLE_CropInteraction.json`

What happens when harvested:
- `CropType`: Must match the seed's CropType
- `HarvestTime`: Time to harvest in seconds
- `DropContainer`: References drop table file
- `Particles`: Visual effect on harvest
- `ParticleColor`: Color of particle effect

### 4. Drop Table
**Location**: `Server/Drops/Item/EXAMPLE_CropDrop.json`

What items drop when harvested:
- Typically 1-3 of the crop product
- Often includes seed drop for replanting (50-75% chance)
- Can include secondary drops (e.g., bonus items at high farming skill)

### 5. Hitbox Definition
**Location**: `Server/Item/Block/Hitboxes/EXAMPLE_CropHitbox.json`

Collision box for the crop:
- Crops are typically small: 6x8x6 to 8x10x8
- Should not take up full block space

### 6. Translations
**Location**: `Server/Languages/en-US/server.lang`

Add entries like:
```
server.items.CustomCropSeed.name=Custom Crop Seeds
server.items.CustomCropSeed.description=Plant to grow custom crops.
server.items.CustomCrop.name=Custom Crop
server.items.CustomCrop.description=A harvest from custom crops.
```

## Crop Growth Stages

Stages define how the crop appears as it grows:

### Stage Example (4 stages)
```
Texture changes by growth percentage:
- Stage 1: 0-25% grown (tiny seedling)
- Stage 2: 25-50% grown (small plant)
- Stage 3: 50-75% grown (medium plant)
- Stage 4: 75-100% grown (mature, ready to harvest)
```

## Common Crop Types

### Fast Growing (60 seconds)
```json
"GrowthTime": 60,
"Stages": 2,
"Properties": {
  "CropType": "QuickGreensCrop",
  "GrowthTime": 60,
  "Stages": 2,
  "RequiresTilling": true,
  "BonemealBoost": 1.0
}
```

### Medium Growing (300 seconds)
```json
"GrowthTime": 300,
"Stages": 4,
"Properties": {
  "CropType": "StandardCrop",
  "GrowthTime": 300,
  "Stages": 4,
  "RequiresTilling": true,
  "BonemealBoost": 0.5
}
```

### Slow Growing (900 seconds)
```json
"GrowthTime": 900,
"Stages": 6,
"Properties": {
  "CropType": "PremiumCrop",
  "GrowthTime": 900,
  "Stages": 6,
  "RequiresTilling": true,
  "BonemealBoost": 0.3
}
```

## Drop Table Variations

### Basic Crop (Only harvest)
```json
{
  "Container": {
    "Type": "Single",
    "Weight": 100.0,
    "Item": {
      "ItemId": "CustomCrop",
      "Quantity": {
        "Min": 1,
        "Max": 2
      }
    }
  }
}
```

### Advanced Crop (Harvest + Seeds)
```json
{
  "Container": {
    "Type": "Multiple",
    "Items": [
      {
        "Weight": 100.0,
        "Item": {
          "ItemId": "CustomCrop",
          "Quantity": {"Min": 1, "Max": 3}
        }
      },
      {
        "Weight": 50.0,
        "Item": {
          "ItemId": "CustomCropSeed",
          "Quantity": {"Min": 1, "Max": 2}
        }
      }
    ]
  }
}
```

### Premium Crop (Harvest + Seeds + Bonus)
```json
{
  "Container": {
    "Type": "Multiple",
    "Items": [
      {
        "Weight": 100.0,
        "Item": {
          "ItemId": "CustomCrop",
          "Quantity": {"Min": 2, "Max": 4}
        }
      },
      {
        "Weight": 60.0,
        "Item": {
          "ItemId": "CustomCropSeed",
          "Quantity": {"Min": 1, "Max": 2}
        }
      },
      {
        "Weight": 25.0,
        "Item": {
          "ItemId": "BonusCropItem",
          "Quantity": {"Min": 1, "Max": 1}
        }
      }
    ]
  }
}
```

## Tips for Custom Crops

1. **Balanced Growth**: Quick crops (60s) = less reward; slow crops (900s) = more reward
2. **Seed Drop Rate**: Usually 50-75% to encourage replanting
3. **Visual Design**: Create 4-6 stage textures showing growth progression
4. **Themed Names**: Use descriptive names like "TwineFlower", "SageLeaf", "CrimsonGrain"
5. **Food Values**: Edible crops need `FoodValue` and `SaturationValue`
6. **Unique Yields**: Different crops drop different quantities to make them distinct
7. **Special Variants**: Consider seasonal variants or rare mutations

## Validation Checklist

- [ ] CropType is unique and consistent across files
- [ ] Seed item has matching CropType
- [ ] Interaction has matching CropType
- [ ] All item references exist (seed, product, bonus items)
- [ ] GrowthTime is reasonable (60-1800 seconds)
- [ ] Stages match texture files (if custom model)
- [ ] Drop table references correct items
- [ ] Seed drop probability encourages replanting (50%+)
- [ ] Translations are defined for seed and product
- [ ] Hitbox allows hand harvesting (small, 6-8 blocks)
- [ ] Tested in-game: can plant, grows, harvests correctly

## Example File References

- **EXAMPLE_CustomCropSeed.json** - Plantable seed item
- **EXAMPLE_CustomCropProduct.json** - Harvestable crop
- **EXAMPLE_CropInteraction.json** - Harvest behavior
- **EXAMPLE_CropDrop.json** - What drops when harvested
- **EXAMPLE_CropHitbox.json** - Collision box
