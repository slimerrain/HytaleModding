# 📍 Examples Quick Reference

All examples are now **distributed throughout the folder structure**. Navigate to the right folder and copy the EXAMPLE_* file!

## Example Files by Category

### 🎁 Items
**Folder**: `Server/Item/Items/`
- `EXAMPLE_BasicItem.json` - Simple generic item
- `EXAMPLE_FoodItem.json` - Consumable food  
- `EXAMPLE_BlockItem.json` - Placeable block
- `EXAMPLE_BlockWithInteraction.json` - Block with interaction
- **README.md** - Detailed guide

### 👨‍🍳 Recipes
**Folder**: `Server/Item/Recipes/`
- `EXAMPLE_SimpleRecipe.json` - Basic recipe
- `EXAMPLE_CookingRecipe.json` - Cooking at stove
- `EXAMPLE_MultiInputRecipe.json` - Complex recipe
- **README.md** - Detailed guide

### 🎁 Drops
**Folder**: `Server/Drops/Item/`
- `EXAMPLE_SingleDrop.json` - One item always drops
- `EXAMPLE_MultiplePossibleDrops.json` - Multiple options
- `EXAMPLE_VariableQuantityDrop.json` - Random amount drops
- **README.md** - Detailed guide

### 🏷️ Resource Types
**Folder**: `Server/Item/ResourceTypes/`
- `EXAMPLE_BasicResourceType.json` - Generic category
- `EXAMPLE_ColoredResourceType.json` - Colored category
- **README.md** - Detailed guide

### 📐 Hitboxes
**Folder**: `Server/Item/Block/Hitboxes/`
- `EXAMPLE_SmallItem.json` - 8x8x8 items
- `EXAMPLE_MediumItem.json` - 12x12x12 items
- `EXAMPLE_FullBlock.json` - 16x16x16 blocks
- `EXAMPLE_CustomHitbox.json` - Custom sizes
- **README.md** - Detailed guide

### ⚡ Effects
**Folder**: `Server/Entity/Effects/`
- `EXAMPLE_Effect.json` - Status effect/buff
- **See folder README.md** for details

### 📊 Stats
**Folder**: `Server/Entity/Stats/`
- `EXAMPLE_Stat.json` - Entity attribute
- **See folder README.md** for details

### 🔄 Interactions
**Folder**: `Server/Item/Interactions/`
- `EXAMPLE_Interaction.json` - Block interaction
- **See folder README.md** for details

### 🎨 Icons
**Folder**: `Common/Icons/`
- **README.md** - How to create item icons (PNG)

### 📦 Resources
**Folder**: `Common/Resources/`
- **README.md** - How to create 3D models and textures

### 🌍 Translations
**Folder**: `Server/Languages/en-US/`
- **README.md** - How to add translations
- `server.lang` - Example translation file

---

## How to Use Examples

### 1. Navigate to the Folder
Go to the folder where your file type belongs (e.g., `Server/Item/Items/`)

### 2. Read the README
Each folder has a README.md explaining:
- What goes in that folder
- File structure and format
- Common values and options
- Tips and best practices

### 3. Copy an Example
Copy an EXAMPLE_* file that's closest to what you want to create

### 4. Rename and Edit
- Rename the file to your item ID
- Edit the values to match your needs
- Reference QUICK_REFERENCE.md for common values

### 5. Test
Load your mod in Hytale and verify it works!

---

## Quick Links

| Need | Go To |
|------|-------|
| How to make an item? | `Server/Item/Items/README.md` |
| How to make a recipe? | `Server/Item/Recipes/README.md` |
| How to define drops? | `Server/Drops/Item/README.md` |
| How to create icons? | `Common/Icons/README.md` |
| How to make 3D models? | `Common/Resources/README.md` |
| How to add translations? | `Server/Languages/en-US/README.md` |

---

## Why Distributed Examples?

✅ **Faster** - Examples right where you need them
✅ **Clearer** - See the folder context
✅ **Easier** - Just copy and rename
✅ **Local** - No need to reference separate file
✅ **Organized** - Everything in its place

---

## All Examples at a Glance

```
📁 Server/Item/Items/
  ├─ EXAMPLE_BasicItem.json
  ├─ EXAMPLE_FoodItem.json
  ├─ EXAMPLE_BlockItem.json
  ├─ EXAMPLE_BlockWithInteraction.json
  ├─ ExampleItem.json (original)
  └─ README.md

📁 Server/Item/Recipes/
  ├─ EXAMPLE_SimpleRecipe.json
  ├─ EXAMPLE_CookingRecipe.json
  ├─ EXAMPLE_MultiInputRecipe.json
  └─ README.md

📁 Server/Drops/Item/
  ├─ EXAMPLE_SingleDrop.json
  ├─ EXAMPLE_MultiplePossibleDrops.json
  ├─ EXAMPLE_VariableQuantityDrop.json
  ├─ ExampleDrop.json (original)
  └─ README.md

📁 Server/Item/ResourceTypes/
  ├─ EXAMPLE_BasicResourceType.json
  ├─ EXAMPLE_ColoredResourceType.json
  ├─ ExampleResourceType.json (original)
  └─ README.md

📁 Server/Item/Block/Hitboxes/
  ├─ EXAMPLE_SmallItem.json
  ├─ EXAMPLE_MediumItem.json
  ├─ EXAMPLE_FullBlock.json
  ├─ EXAMPLE_CustomHitbox.json
  ├─ ExampleHitbox.json (original)
  └─ README.md

📁 Server/Entity/Effects/
  ├─ EXAMPLE_Effect.json
  └─ (Add README.md)

📁 Server/Entity/Stats/
  ├─ EXAMPLE_Stat.json
  └─ (Add README.md)

📁 Server/Item/Interactions/
  ├─ EXAMPLE_Interaction.json
  └─ (Add README.md)

📁 Common/Icons/
  └─ README.md

📁 Common/Resources/
  └─ README.md

📁 Server/Languages/en-US/
  ├─ README.md
  └─ server.lang (with examples)
```

---

**The EXAMPLES.md file is now just this quick reference!**

**All actual examples are in their proper folders for easier access.**
