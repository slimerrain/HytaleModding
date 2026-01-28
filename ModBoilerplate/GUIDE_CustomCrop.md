# Custom Crop - Complete Example Guide

## Overview

This guide shows how to create a complete custom crop system with seeds, growth stages, and harvesting mechanics.

## Files You Need to Create

### 1. **Seed Item** (`Server/Item/Items/MyCustomSeed.json`)

Copy from: `EXAMPLE_CustomCropSeed.json`

```json
{
  "TranslationProperties": {
    "Name": "server.items.MyCustomSeed.name",
    "Description": "server.items.MyCustomSeed.description"
  },
  "Parent": "Template_Seed",
  "Icon": "Icons/ItemsGenerated/MyCustomSeed.png",
  "ResourceTypes": [{"Id": "Seeds"}, {"Id": "Agriculture"}],
  "Quality": "Common",
  "Consumable": false,
  "Properties": {
    "CropType": "MyCustomCrop",
    "GrowthTime": 300,
    "Stages": 4,
    "RequiresTilling": true,
    "BonemealBoost": 0.5
  },
  "Scale": 0.8,
  "IconProperties": {
    "Scale": 0.9,
    "Rotation": [0, 45, 0],
    "Translation": [0, -2]
  }
}
```

**Key points:**
- Parent: `Template_Seed` (special for plantable items)
- `CropType`: "MyCustomCrop" (must be unique, referenced everywhere)
- `GrowthTime`: 300 seconds = 5 minutes (adjust to difficulty)
- `Stages`: 4 typical (more stages = more visual variety)
- `RequiresTilling`: true (needs farmland), false (grows on regular dirt)
- `BonemealBoost`: 0.5 (how much bonemeal speeds growth)

### 2. **Crop Product Item** (`Server/Item/Items/MyCustomCrop.json`)

Copy from: `EXAMPLE_CustomCropProduct.json`

```json
{
  "TranslationProperties": {
    "Name": "server.items.MyCustomCrop.name",
    "Description": "server.items.MyCustomCrop.description"
  },
  "Parent": "Template_Generic",
  "Icon": "Icons/ItemsGenerated/MyCustomCrop.png",
  "ResourceTypes": [{"Id": "Crops"}, {"Id": "Agriculture"}],
  "Quality": "Common",
  "Consumable": false,
  "Properties": {
    "Harvestable": true,
    "FoodValue": 4,
    "SaturationValue": 2.5
  }
}
```

**Key points:**
- Parent: `Template_Generic` (regular item)
- `FoodValue`: Hunger restored (0 if not edible)
- `SaturationValue`: How long saturation lasts
- `Harvestable`: Identifies it as a crop product

### 3. **Harvest Interaction** (`Server/Item/Interactions/Interact_MyCustomCrop.json`)

Copy from: `EXAMPLE_CropInteraction.json`

```json
{
  "InteractionType": "Harvest",
  "BlockId": "MyCustomCrop",
  "CropType": "MyCustomCrop",
  "RequiredTool": "Hands",
  "HarvestTime": 0.5,
  "DropContainer": "Drops_MyCustomCrop",
  "Sound": "CropHarvest",
  "Particles": "LeafParticles",
  "ParticleColor": "#90EE90"
}
```

**Key points:**
- `CropType`: Must match seed and block definitions
- `RequiredTool`: Usually "Hands" for crops
- `HarvestTime`: How fast to harvest (0.5s typical)
- `DropContainer`: File name in Drops/Item/ folder
- `Particles`: Visual effect type
- `ParticleColor`: Color in hex format

### 4. **Drop Table** (`Server/Drops/Item/Drops_MyCustomCrop.json`)

Copy from: `EXAMPLE_CropDrop.json`

```json
{
  "Container": {
    "Type": "Multiple",
    "Items": [
      {
        "Weight": 100.0,
        "Item": {
          "ItemId": "MyCustomCrop",
          "Quantity": {
            "Min": 1,
            "Max": 3
          }
        }
      },
      {
        "Weight": 50.0,
        "Item": {
          "ItemId": "MyCustomSeed",
          "Quantity": {
            "Min": 1,
            "Max": 2
          }
        }
      }
    ]
  }
}
```

**Key points:**
- First item (Weight 100): Always drops 1-3 of the crop
- Second item (Weight 50): 50% chance to drop seeds (1-2)
- Always include seed drops so players can replant
- Can add a third item for rare bonus drops

### 5. **Hitbox Definition** (`Server/Item/Block/Hitboxes/MyCustomCrop_Hitbox.json`)

Copy from: `EXAMPLE_CropHitbox.json`

```json
{
  "Bounds": {
    "X": 6,
    "Y": 8,
    "Z": 6
  }
}
```

**Key points:**
- Crops should be small (6-8 blocks on each side)
- Allows players to walk through
- Doesn't block placement of other crops

### 6. **Translations** (Add to `Server/Languages/en-US/server.lang`)

```
server.items.MyCustomSeed.name=My Custom Seeds
server.items.MyCustomSeed.description=Plant in tilled soil to grow custom crops.
server.items.MyCustomCrop.name=My Custom Crop
server.items.MyCustomCrop.description=A fresh harvest from tended crops. Restores hunger.
```

### 7. **3D Model** (Save to `Common/Resources/`)

Create growth stage textures:
- `MyCustomCrop_Stage1.png` - Seedling
- `MyCustomCrop_Stage2.png` - Early growth
- `MyCustomCrop_Stage3.png` - Mid growth
- `MyCustomCrop_Stage4.png` - Mature

Or create model files:
- `MyCustomCrop.blockymodel` - The crop block
- `MyCustomCrop_Texture.png` - Base texture

### 8. **Icon** (Save to `Common/Icons/ItemsGenerated/`)

Create two 64x64 PNG icons:
- `MyCustomSeed.png` - Small seed icon
- `MyCustomCrop.png` - Harvested crop icon

## Summary of ID References

Everything connects through these IDs:

| File | ID Used | Purpose |
|------|---------|---------|
| Seed Item | `CropType: "MyCustomCrop"` | Identifies crop type |
| Interaction | `CropType: "MyCustomCrop"` | Must match seed |
| Drop Table | `ItemId: "MyCustomCrop"` + `ItemId: "MyCustomSeed"` | Drop references |
| Translations | `server.items.MyCustomSeed.*` and `server.items.MyCustomCrop.*` | Display text |

**All "MyCustomCrop" references must be identical!**

## Step-by-Step Creation Process

```
Step 1: Choose Crop Name
  → "MyCustomCrop" (descriptive: "SageLeaf", "TwineFlower", "CrimsonGrain")

Step 2: Create Seed Item
  → Copy EXAMPLE_CustomCropSeed.json
  → Replace "CustomCropSeed" with "MyCustomSeed"
  → Replace "CustomCrop" with "MyCustomCrop"
  → Set GrowthTime based on difficulty
  → Set Stages for visual variety

Step 3: Create Crop Product Item
  → Copy EXAMPLE_CustomCropProduct.json
  → Replace "CustomCrop" with "MyCustomCrop"
  → Set FoodValue if edible

Step 4: Create Harvest Interaction
  → Copy EXAMPLE_CropInteraction.json
  → Replace "CustomCrop" with "MyCustomCrop"
  → Adjust HarvestTime if needed

Step 5: Create Drop Table
  → Copy EXAMPLE_CropDrop.json
  → Replace "CustomCrop" with "MyCustomCrop"
  → Replace "CustomCropSeed" with "MyCustomSeed"
  → Adjust drop quantities

Step 6: Create Hitbox
  → Copy EXAMPLE_CropHitbox.json
  → Save as MyCustomCrop_Hitbox.json
  → Keep dimensions 6x8x6 unless unique shape

Step 7: Add Translations
  → Add 4 lines to server.lang
  → Name and description for both seed and product

Step 8: Create Growth Textures
  → Design 4 PNG textures showing growth stages
  → Sizes: 16x16 or 32x32
  → Save as Stage1, Stage2, Stage3, Stage4

Step 9: Create Icons
  → Design 64x64 PNG for seed
  → Design 64x64 PNG for crop
  → Make them visually distinct

Step 10: Test In-Game
  → Load mod
  → Plant seeds in tilled soil
  → Watch growth progression
  → Harvest and verify drops
  → Confirm seed replanting
```

## Growth Time Recommendations

| Type | Time | Stages | Reward | Use Case |
|------|------|--------|--------|----------|
| Quick | 60s | 2-3 | Low (1-2) | Utility crops, low-level |
| Standard | 300s | 4 | Medium (2-3) | Main crops |
| Slow | 900s | 5-6 | High (3-5) | Premium crops, late-game |

## Common Customization

### Non-Tillage Crop (Grows on Regular Soil)

```json
"Properties": {
  "CropType": "WildCrop",
  "RequiresTilling": false,  // Grows on any dirt
  "GrowthTime": 300,
  "Stages": 4
}
```

### Edible Vs Non-Edible

**Edible (restores hunger):**
```json
"Properties": {
  "FoodValue": 4,
  "SaturationValue": 2.5,
  "Harvestable": true
}
```

**Non-Edible (crafting ingredient):**
```json
"Properties": {
  "Harvestable": true
}
```

### High Seed Drop Rate (Easier to Farm)

```json
{
  "Weight": 75.0,  // 75% chance instead of 50%
  "Item": {
    "ItemId": "MyCustomSeed",
    "Quantity": {"Min": 2, "Max": 3}  // More seeds
  }
}
```

### Bonus Rare Drop

```json
{
  "Weight": 15.0,  // 15% chance
  "Item": {
    "ItemId": "SpecialBonusItem",
    "Quantity": {"Min": 1, "Max": 1}
  }
}
```

## Tips

- **Growth Balance**: Faster crops = less reward, slower crops = more reward
- **Seed Sustainability**: Always include seed drops (60%+ chance)
- **Visual Polish**: 4+ stage textures make growth satisfying
- **Theming**: Use descriptive names (SageLeaf, not sage_leaf)
- **Progression**: Create multiple tiers (beginner, intermediate, advanced crops)
- **Special Mechanics**: Consider seasonal crops or weather-dependent growth

## Validation Before Testing

- [ ] CropType is unique across all files
- [ ] Seed item defined correctly
- [ ] Product item defined correctly
- [ ] Interaction references correct CropType
- [ ] Drop table references both seed and product
- [ ] GrowthTime is reasonable (60-1800 seconds)
- [ ] Stages matches texture count
- [ ] Translation keys match item properties
- [ ] Icons created and referenced
- [ ] No missing item references in drops

## Testing Checklist

- [ ] Plant seed in tilled soil
- [ ] Observe growth through all stages
- [ ] Harvest at maturity
- [ ] Verify crop product drops
- [ ] Verify seed drops for replanting
- [ ] Check food values if edible
- [ ] No console errors
- [ ] Icons display correctly in inventory
