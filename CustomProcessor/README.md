# CustomProcessor Mod - Asset Requirements

This mod adds a Tea Processor bench that dries tea leaves into White Tea.

## Required Assets

You will need to create or source the following assets for the mod to display properly in-game:

### Icons

1. **Common/Icons/ItemsGenerated/CustomProcessor_TeaProcessor.png**
   - Icon for the Tea Processor bench block
   - Recommended size: 64x64 pixels
   - Should show a drying rack or processing station with tea theme

2. **Common/Icons/ItemsGenerated/CustomProcessor_WhiteTea.png**
   - Icon for the White Tea item
   - Recommended size: 64x64 pixels
   - Should show dried white tea leaves

3. **Common/Icons/CraftingCategories/CustomProcessor/TeaDrying.png**
   - Icon for the Tea Drying crafting category
   - Recommended size: 64x64 pixels
   - Should represent the tea drying process

### 3D Models and Textures

1. **Common/Blocks/Benches/CustomProcessor_TeaProcessor.blockymodel**
   - 3D model for the Tea Processor bench
   - Should resemble a workbench with drying racks
   - Reference: CustomBench_AdvancedWorkbench.blockymodel

2. **Common/Blocks/Benches/CustomProcessor_TeaProcessor_Texture.png**
   - Texture for the Tea Processor bench model
   - Reference: CustomBench_AdvancedWorkbench_Texture.png

3. **Common/Blocks/Benches/CustomProcessor_TeaProcessor_Processing.blockyanim** (Optional)
   - Animation for when the bench is processing
   - Reference: CustomBench_AdvancedWorkbench_Crafting.blockyanim

## Temporary Solution

Until you create custom assets, you can:
1. Copy similar assets from CustomBench and rename them
2. Use placeholder images (the game will show missing texture indicators)
3. Reference existing game assets if compatible

## File Structure

```
CustomProcessor/
├── manifest.json
├── README.md (this file)
├── Common/
│   ├── Blocks/
│   │   └── Benches/
│   │       ├── CustomProcessor_TeaProcessor.blockymodel
│   │       ├── CustomProcessor_TeaProcessor_Texture.png
│   │       └── CustomProcessor_TeaProcessor_Processing.blockyanim
│   └── Icons/
│       ├── CraftingCategories/
│       │   └── CustomProcessor/
│       │       └── TeaDrying.png
│       └── ItemsGenerated/
│           ├── CustomProcessor_TeaProcessor.png
│           └── CustomProcessor_WhiteTea.png
└── Server/
    ├── Item/
    │   ├── Items/
    │   │   ├── Bench/
    │   │   │   └── CustomProcessor_TeaProcessor.json
    │   │   └── CustomProcessor_WhiteTea.json
    │   └── Recipes/
    │       └── CustomProcessor_Recipe_WhiteTea.json
    └── Languages/
        └── en-US/
            └── server.lang
```

## Mod Functionality

- **Tea Processor Bench**: Can be crafted at a Furniture Bench using 2 Wood Trunks, 4 Iron Bars, and 8 Sticks
- **Recipe**: 3 Tea Leaves → 1 White Tea (8 seconds processing time)
- **White Tea Effects**: Provides minor health and energy regeneration when consumed
- **Upgradeable**: The bench has 3 tier levels for faster processing

## Dependencies

This mod references items from the CustomCrop mod:
- `CustomCrop_TeaLeaves_Item` - Tea leaves harvested from tea crops

Make sure the CustomCrop mod is installed and enabled for this mod to work properly.
