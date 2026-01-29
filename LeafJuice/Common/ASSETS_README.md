# CustomCrop Common Assets Structure

This folder contains all client-side assets (models, textures, icons) for the CustomCrop mod.

## Directory Structure

```
Common/
├── Blocks/
│   └── (No custom block models needed - using vanilla crop models)
├── Icons/
│   └── ItemsGenerated/
│       ├── CustomCrop_Strawberry.png          (Icon for harvested strawberry)
│       ├── Plant_Seeds_Strawberry.png          (Icon for strawberry seeds)
│       └── Plant_Crop_Strawberry_Block.png     (Icon for strawberry crop block)
└── Items/
    └── (Optional: custom item models if not using vanilla models)
```

## Asset Requirements

### Icons (Required)
**Location:** `Common/Icons/ItemsGenerated/`
**Format:** PNG with transparency, recommended 128x128 pixels

1. **CustomCrop_Strawberry.png**
   - Icon for the harvested strawberry item
   - Should show a red/pink strawberry
   - Used in inventory and item tooltips

2. **Plant_Seeds_Strawberry.png**
   - Icon for the strawberry seeds
   - Should show a seed bag with strawberry imagery
   - Similar style to vanilla seed bags

3. **Plant_Crop_Strawberry_Block.png**
   - Icon for the crop block
   - Should show strawberry plants/crops
   - Used when the block is in inventory

### Models (Optional - Currently Using Vanilla)
The mod currently references vanilla models:
- Seeds: `Resources/Plants/Seeds.blockymodel`
- Growth stages: `Resources/Ingredients/Carrot_01/02/03.blockymodel`

If you want custom models, create them in:
- `Common/Items/Strawberry/` for item models
- `Common/Blocks/Crops/` for crop block models

### Textures (Optional - Currently Using Vanilla)
The mod currently references vanilla textures:
- Seeds: `Resources/Plants/Seeds_Textures/SmallRed.png`
- Crop: `Resources/Ingredients/Strawberry_Texture.png`

If you want custom textures, create them alongside your models:
- `Common/Items/Strawberry/Strawberry_Texture.png`
- `Common/Blocks/Crops/Strawberry_Crop_Texture.png`

## Creating Custom Assets

### To replace vanilla models with custom ones:

1. Create your `.blockymodel` files using BlockBench or similar
2. Place them in appropriate folders (e.g., `Common/Items/Strawberry/`)
3. Update the JSON files in `Server/Item/Items/` to reference your custom models:

```json
"Model": "Items/Strawberry/CustomStrawberry.blockymodel",
"Texture": "Items/Strawberry/CustomStrawberry_Texture.png"
```

### For crop growth stages:

If creating custom growth stage models, update `CustomCrop_Strawberry_Block.json`:

```json
"Stage1": {
  "CustomModel": "Blocks/Crops/Strawberry_Stage1.blockymodel",
  "CustomModelTexture": [
    {
      "Texture": "Blocks/Crops/Strawberry_Texture.png",
      "Weight": 1
    }
  ]
}
```

## Quick Start

**Minimum Required:** Just create the 3 icon PNG files in `Common/Icons/ItemsGenerated/`
**For Full Customization:** Create custom models and textures, then update the Server JSON references

## Reference
Look at the vanilla game's `Assets/Common/` folder structure for examples of models and textures.
