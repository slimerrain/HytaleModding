# CustomFood Mod

## Overview
The CustomFood mod adds custom consumable food items to Hytale. This version includes a soothing **Herbal Tea** crafted from herbs and water.

## Features

### Herbal Tea
- **Name:** Herbal Tea
- **Item ID:** `Food_Tea_Herbal`
- **Quality:** Uncommon
- **Item Level:** 8
- **Max Stack:** 25

#### Effects
- Instantly restores 20% health
- Drinking animation uses the standard potion consume animation
- Custom particle effects when consumed
- Crafting sound effects

#### Recipe
- **Ingredients:**
  - 2x Plant_Herb_Mint
  - 1x Water_Bucket
- **Crafting Bench:** Cooking Bench
- **Category:** Brewing
- **Crafting Time:** 8 seconds
- **Output:** 1x Herbal Tea, 1x Container_Bucket (returned)

## Mod Details

### Version
1.0.0

### Mod ID
CustomFood

### Dependencies
None

### Optional Dependencies
None

### Load Before
None

## Asset Structure

```
CustomFood/
├── manifest.json
├── README.md
├── Server/
│   ├── Item/
│   │   └── Items/
│   │       └── Food_Tea_Herbal.json
│   └── Languages/
│       └── en-US/
│           └── server.lang
└── Common/
    ├── Icons/
    │   └── ItemsGenerated/
    │       └── Food_Tea_Herbal.png (placeholder)
    └── Items/
        └── Consumables/
            └── Food/
                └── Tea_Cup.blockymodel (placeholder)
```

## Implementation Notes

### Based On
This mod is based on the vanilla Food template (`Template_Food`) and follows the structure of established food mods like NoCube's Orchard.

### 3D Models and Textures
The mod references the following placeholder assets that should be customized:
- `Items/Consumables/Food/Tea_Cup.blockymodel` - The 3D model of the tea cup
- `Items/Consumables/Food/Tea_Cup_Texture.png` - The texture for the tea cup model
- `Icons/ItemsGenerated/Food_Tea_Herbal.png` - The inventory icon for the item

### Interactions
- **Consumption Method:** Using the item performs the "Root_Secondary_Consume_Food_T2" interaction
- **Animation:** Uses the standard potion drinking animation from the game
- **Sound:** Plays the "SFX_Health_Potion_Low_Drink" sound effect
- **Visual Effect:** Displays food eating particles with a brown/tan color (#D4A574)

## Future Additions
Potential items to add in future versions:
- Stamina Tea (increases stamina regen)
- Spiced Tea (increases resistance)
- Calming Tea (reduces status effect duration)
- Energizing Tea (increases movement speed)

## Credits
Created following the Hytale modding guidelines and structure conventions from existing community mods.
