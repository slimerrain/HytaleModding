# Assets Needed for Example Files

This document lists all Common folder assets referenced by the example files.

## Custom Crafting Table Assets

### Icons
- **Path**: `Common/Icons/ItemsGenerated/CustomWorkbench.png`
- **Type**: 64x64 PNG icon
- **Purpose**: Inventory icon for the crafting table item
- **Referenced in**: `Server/Item/Items/EXAMPLE_CustomCraftingTable.json`

### 3D Model
- **Path**: `Common/Resources/CustomWorkbench.blockymodel`
- **Type**: Hytale 3D block model
- **Purpose**: The 3D appearance of the placed crafting table
- **Referenced in**: `Server/Item/Items/EXAMPLE_CustomCraftingTable.json`

### Texture
- **Path**: `Common/Resources/CustomWorkbench_Texture.png`
- **Type**: PNG texture (128x128 or higher recommended)
- **Purpose**: Texture applied to the 3D model
- **Referenced in**: `Server/Item/Items/EXAMPLE_CustomCraftingTable.json`

---

## Custom Crop Assets

### Seed Icon
- **Path**: `Common/Icons/ItemsGenerated/CustomCropSeed.png`
- **Type**: 64x64 PNG icon
- **Purpose**: Inventory icon for crop seeds
- **Referenced in**: `Server/Item/Items/EXAMPLE_CustomCropSeed.json`

### Crop Product Icon
- **Path**: `Common/Icons/ItemsGenerated/CustomCrop.png`
- **Type**: 64x64 PNG icon
- **Purpose**: Inventory icon for harvested crop
- **Referenced in**: `Server/Item/Items/EXAMPLE_CustomCropProduct.json`

### Crop Growth Models (Optional but Recommended)
If creating custom growth visuals:
- **Paths**: 
  - `Common/Resources/CustomCrop_Stage1.png` (seedling)
  - `Common/Resources/CustomCrop_Stage2.png` (early growth)
  - `Common/Resources/CustomCrop_Stage3.png` (mid growth)
  - `Common/Resources/CustomCrop_Stage4.png` (mature)
- **Type**: PNG textures or .blockymodel files
- **Purpose**: Visual appearance at each growth stage
- **Note**: Can use default crop models if not specified

---

## Quick Creation Checklist

### For Custom Crafting Table:
- [ ] Create 64x64 icon: `CustomWorkbench.png`
- [ ] Create 3D model: `CustomWorkbench.blockymodel`
- [ ] Create texture: `CustomWorkbench_Texture.png`
- [ ] Place all in correct Common folder paths
- [ ] Test in-game to verify appearance

### For Custom Crop:
- [ ] Create 64x64 seed icon: `CustomCropSeed.png`
- [ ] Create 64x64 crop icon: `CustomCrop.png`
- [ ] (Optional) Create growth stage textures/models
- [ ] Place all in correct Common folder paths
- [ ] Test in-game to verify appearance

---

## Placeholder Files

We've created placeholder README files for each required asset:
- `CustomWorkbench.png.README.md` - Icon guide
- `CustomWorkbench.blockymodel.README.md` - Model guide
- `CustomWorkbench_Texture.png.README.md` - Texture guide
- `CustomCropSeed.png.README.md` - Seed icon guide
- `CustomCrop.png.README.md` - Crop icon guide

**Replace these placeholders with actual assets before using the mod!**

---

## Why These Are Needed

The **Server/** folder contains all the game logic (stats, recipes, drops), but the **Common/** folder contains all the visual assets that players see:

- **Icons**: What items look like in inventory
- **Models**: What blocks/items look like in the world
- **Textures**: The surface appearance of models

Without these Common assets, items will either:
- Show as missing textures (purple/black checkerboard)
- Use default/fallback appearances
- Not render at all

---

## Tools for Creating Assets

### For Icons (64x64 PNG):
- Aseprite (pixel art)
- Photoshop
- GIMP (free)
- Paint.NET (free)
- Pixelorama (free, pixel art)

### For 3D Models:
- Hytale Block Editor (in-game, recommended)
- Blockbench (free, supports block models)
- Blender (advanced, requires export plugins)

### For Textures:
- Same as icon tools
- Substance Painter (advanced texturing)
- Krita (free)

---

## Next Steps

1. Decide which examples you want to use
2. Design/create the visual assets
3. Place them in the correct Common folder paths
4. Delete placeholder README files
5. Test the mod in-game
6. Adjust visuals as needed
