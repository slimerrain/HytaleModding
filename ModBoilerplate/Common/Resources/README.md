# Common/Resources

This folder contains all 3D models and textures for your items and blocks.

## File Types

### .blockymodel Files
- **Purpose**: 3D model files for items/blocks
- **Format**: Binary Hytale block model format
- **How to Create**: Use Hytale's Block Editor tool
- **Naming Convention**: `ItemName.blockymodel`
- **Examples**:
  - `Sword_Iron.blockymodel`
  - `Potion_Blue.blockymodel`
  - `CoffeeBeans.blockymodel`

### .png Files (Textures)
- **Purpose**: Texture/material files for 3D models
- **Format**: PNG (32-bit recommended for alpha channel)
- **Size**: 16x16, 32x32, or 64x64 pixels
- **Naming Convention**: `ItemName_Texture.png` or `ItemName_Normal.png`
- **Background**: Use transparency (PNG alpha channel)
- **Examples**:
  - `Sword_Iron_Texture.png`
  - `Wood_Plank_Texture.png`
  - `Copper_Ore_Texture.png`

## Organization Tips

You can organize this folder further if you have many items:

```
Resources/
├─ Models/
│  ├─ Sword_Iron.blockymodel
│  ├─ Shield_Wood.blockymodel
│  └─ ...
└─ Textures/
   ├─ Sword_Iron_Texture.png
   ├─ Shield_Wood_Texture.png
   └─ ...
```

Or by category:

```
Resources/
├─ Weapons/
│  ├─ Sword_Iron.blockymodel
│  └─ Sword_Iron_Texture.png
├─ Tools/
│  ├─ Pickaxe_Stone.blockymodel
│  └─ Pickaxe_Stone_Texture.png
└─ ...
```

## How to Create

### 3D Models
1. Open Hytale's Block Editor
2. Design your model
3. Export as `.blockymodel` file
4. Save to this folder
5. Reference in your item JSON with `"CustomModel": "Resources/ItemName.blockymodel"`

### Textures
1. Create texture in image editor
2. Save as PNG file
3. Ensure transparency is preserved
4. Name appropriately
5. Reference in your item JSON with texture array

## File Paths in JSON

When referencing files in your item JSON, use paths relative to the mod root:

```json
{
  "CustomModel": "Resources/MyItem.blockymodel",
  "CustomModelTexture": [
    {
      "Texture": "Resources/MyItem_Texture.png",
      "Weight": 1
    }
  ]
}
```

## Tips
- Keep model scale reasonable (typically 0.5-2.0)
- Test textures on the actual model before finalizing
- Use consistent art style across all items
- Create multiple variants with different textures for variety
