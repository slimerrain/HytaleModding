# Custom Date Fruit Tree Mod for Hytale

A Hytale mod that adds plantable Date Fruit trees based on the vanilla Apple Tree mechanics. Date Fruit trees spawn naturally in the wild and can be planted and grown by players.

## Features

- **Date Fruit Tree Block**: A growable tree that produces delicious date fruits
- **Natural Spawning**: Date Fruit trees spawn in plains and desert biomes alongside regular trees
- **Growth Stages**: 4 growth stages from sapling to mature fruiting tree
- **Harvestable**: Harvest date fruits from mature trees
- **Plantable**: Plant and grow your own date fruit trees on soil

## Items Added

### Plant_Sapling_Date
- **Name**: Date Tree Sapling
- **Type**: Plantable block/seed
- **Crafting**: Requires 4x Date Fruits + 1x Life Essence (Concentrated) at Farming Bench (Tier 4)
- **Growth Time**: ~4 in-game days for full growth

### Plant_Fruit_Date
- **Name**: Date Fruit
- **Type**: Resource/Food
- **Obtained**: Harvesting mature Date Fruit trees
- **Harvest Yield**: 2-4 fruits per harvest

### Plant_Crop_Date_Block
- **Name**: Date Tree (various growth stages)
- **Type**: Growing tree block
- **Growth Stages**: Stage 0, Stage 1, Stage 2, Stage Final (harvestable)

## Growth Mechanics

The Date Fruit tree follows the vanilla tree farming system:

1. **Stage 0** (Sapling): Small sapling
2. **Stage 1**: Young tree growth
3. **Stage 2**: Maturing tree with more foliage
4. **Stage Final**: Mature tree with harvestable fruits

Growth times for each stage are approximately 1 in-game day per stage.

## Drop Tables

```json
Stage0: Plant_Crop_Date_Block (sapling)
Stage1: Plant_Crop_Date_Block (seedling)
Stage2: Plant_Crop_Date_Block (young tree)
StageFinal_Harvest: 2-4x Plant_Fruit_Date
StageFinal_Break: 1-2x Sticks, 1-2x Fibre
```

## Technical Details

- **Parent Class**: Based on Plant_Sapling_Apple template
- **Model/Texture**: Currently uses vanilla Apple Tree models/textures (for editing)
- **Block Entity**: FarmingBlock component for growth mechanics
- **Growth Modifiers**: Fertilizer, Water, Light Level

## Installation

1. Copy the entire `CustomTree` folder to your Hytale mods directory
2. Launch Hytale

## Usage

### Finding Date Fruit Trees
- Explore plains and desert biomes
- Look for trees with date fruits
- They spawn naturally like vanilla trees

### Planting Date Fruit Trees
1. Obtain a Date Tree Sapling (from crafting or natural drops)
2. Place it on grass, dirt, or other soil blocks
3. Wait for it to grow through 4 stages
4. Growth takes approximately 4 in-game days for full maturity

### Harvesting Date Fruits
1. Wait until the tree reaches final stage (fruits visible)
2. Right-click (Use) the mature tree
3. Collect 2-4 date fruits
4. Tree can be harvested multiple times

## Current Status

✅ **Fully Functional** - All game mechanics work
✅ **Growth System** - Complete 4-stage farming
✅ **Harvesting** - Right-click mature trees
✅ **Drop Tables** - Proper loot at all stages

⚠️ **Needs Custom Textures/Models** - Currently uses vanilla apple tree assets (included for editing)

## Future Enhancements

- Custom 3D models for date trees
- Custom fruit models and textures
- Different fruit types (light dates, dark dates)
- Desert biome generation integration
- Recipe additions for date-based food items
