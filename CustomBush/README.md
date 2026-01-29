# Custom Camellia Bush Mod for Hytale

A Hytale mod that adds plantable Camellia bushes based on the vanilla berry bush mechanics. Camellia bushes spawn naturally in the wild and can be planted and grown by players.

## Features

- **Camellia Bush Block**: A growable bush that produces beautiful pink camellia flowers
- **Natural Spawning**: Camellia bushes spawn in plains and forest biomes alongside regular bushes
- **Growth Stages**: 5 growth stages from sapling to flowering bush
- **Harvestable**: Harvest camellia flowers from mature bushes
- **Plantable**: Place and grow your own camellia bushes on soil

## Items Added

### Plant_Crop_Camellia_Block
- **Name**: Camellia Bush
- **Type**: Plantable block/crop
- **Growth Time**: ~2-4 minutes (120,000-160,000 ticks) for full growth
- **Regrowth**: ~30-40 seconds (30,000-40,000 ticks) after harvest
- **Drops on Break**: Fibre (1-2) and Sticks (1-2)

### Plant_Camellia_Flower  
- **Name**: Camellia Flower
- **Type**: Resource/Ingredient
- **Obtained**: Harvesting mature Camellia bushes
- **Harvest Yield**: 2-4 flowers per harvest (with chance for bonus)

## Growth Mechanics

The Camellia bush follows the vanilla crop farming system:

1. **Stage 0** (Base): Small bush with no flowers
2. **Stage 1**: Bush grows larger
3. **Stage 2**: More leaves appear
4. **Stage 3**: Bush preparing to flower
5. **Stage Final**: Full bush with pink camellia flowers - **Harvestable**

After harvesting, the bush returns to Stage 3 and regrows flowers.

## World Generation

Camellia bushes spawn naturally in:
- Plains biomes (Zone 1 Tier 1)
- Forest biomes (Zone 1 Tier 1)
- Areas where vanilla berry bushes spawn

They use the same noise patterns as berry bushes but with adjusted density to remain less common.

## Drop Tables

### Breaking the Bush
- Ingredient_Fibre: 1-2
- Ingredient_Stick: 1-2

### Harvesting Flowers (Final Stage)
- Plant_Camellia_Flower: 2-4 (guaranteed)
- Plant_Camellia_Flower: 1-2 (30% chance bonus)
- Ingredient_Life_Essence: 1 (20% chance)
- Ingredient_Stick: 1 (15% chance)

### Breaking While Growing
Stages 1-3 drop the bush block itself (Plant_Crop_Camellia_Block) so you can replant it.

## Installation

1. Copy the `CustomBush` folder to your Hytale mods directory
2. Ensure the mod structure is intact:
   ```
   CustomBush/
   ├── manifest.json
   ├── Common/
   │   └── ASSETS_README.md (instructions for adding textures)
   └── Server/
       ├── Drops/
       ├── Item/
       ├── Languages/
       └── World/
   ```
3. Add custom textures (see Asset Requirements below)
4. Launch Hytale

## Asset Requirements

This mod requires custom textures to be created. See `Common/ASSETS_README.md` for detailed instructions.

### Required Textures

**Block Textures** (Common/Blocks/Foliage/Plants/):
- Bush_Camellia.png
- Bush_Camellia_Stage1.png
- Bush_Camellia_Stage2.png
- Bush_Camellia_Stage3.png
- Bush_Camellia_Flowers.png

**Resource Textures** (Common/Resources/Plants/):
- Camellia_Flower.png

**Icons** (Common/Icons/ItemsGenerated/):
- Plant_Crop_Camellia_Block.png
- Plant_Camellia_Flower.png

**Note**: The mod will function without custom textures but will use vanilla fallback models/textures until custom ones are provided.

## Technical Details

### File Structure

```
Server/
├── Drops/
│   ├── Drops_Plant_Crop_Camellia_Block.json
│   ├── Drops_Plant_Crop_Camellia_Stage1.json
│   ├── Drops_Plant_Crop_Camellia_Stage2.json
│   ├── Drops_Plant_Crop_Camellia_Stage3.json
│   ├── Drops_Plant_Crop_Camellia_StageFinal.json
│   └── Drops_Plant_Crop_Camellia_StageFinal_Harvest.json
├── Item/
│   └── Items/
│       ├── Plant_Crop_Camellia_Block.json
│       └── Plant_Camellia_Flower.json
├── Languages/
│   └── en-US/
│       └── Items.json
└── World/
    └── Zone1_Camellia_Spawns.json
```

### Based On

This mod is based on the vanilla berry bush system:
- `Plant_Crop_Berry_Block` (item structure)
- `Template_Crop_Berry_Block` (farming mechanics)
- Berry bush world generation patterns

### Compatibility

- **Hytale Version**: Designed for Hytale Beta/Release
- **Dependencies**: None
- **Conflicts**: Should not conflict with other mods unless they modify berry bush behavior

## Future Ideas

Potential expansions for this mod:
- Different camellia varieties (red, white, pink)
- Camellia tea crafting recipe
- Camellia oil extraction
- Seasonal blooming patterns
- Biome-specific camellia variants

## Credits

- **Developer**: CustomBush Developer
- **Based On**: Vanilla Hytale berry bush mechanics
- **Inspiration**: Real-world Camellia plants (Camellia japonica, Camellia sinensis)

## Version History

### v1.0.0 (Initial Release)
- Added Camellia Bush block with 5 growth stages
- Added Camellia Flower harvestable item
- Implemented natural world spawning in plains/forest biomes
- Complete growth and farming mechanics
- Drop tables for all stages

## License

This mod is provided as-is for use with Hytale. Feel free to modify and redistribute with credit.

## Support

For issues, suggestions, or questions about this mod, please refer to the Hytale modding community resources.
