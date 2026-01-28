# Common/Icons/ItemsGenerated

This folder contains item icons displayed in the game's UI (inventory, crafting menus, etc).

## File Requirements
- **Format**: PNG (with transparency/alpha channel)
- **Size**: 64x64 pixels (recommended)
- **Naming**: Must match your item ID exactly
  - Example: If your item ID is `CoffeeBeans`, the icon should be `CoffeeBeans.png`
- **Color Space**: Use Hytale's 16-bit color palette for consistency (optional but recommended)

## Examples
- `YourItem.png` - Icon for your item
- `Sword_Iron.png` - Icon for an iron sword
- `Potion_Health.png` - Icon for a health potion

## How to Create
1. Create artwork in your image editor (Photoshop, GIMP, Aseprite, etc)
2. Create a 64x64 transparent canvas
3. Draw/render your item
4. Save as PNG with transparency
5. Name it to match your item ID exactly
6. Place in this folder

## Pro Tips
- Icon appearance affects how players perceive item value
- Use consistent lighting/style throughout your mod
- Leave some space around edges for better visibility
- Test at full size (not zoomed in) to ensure readability
- Consider the icon rotation settings in your item JSON
