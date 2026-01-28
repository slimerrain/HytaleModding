# Complete ModBoilerplate Directory Structure

This file documents the complete directory structure of the ModBoilerplate with descriptions of what goes in each folder.

```
ModBoilerplate/
│
├── manifest.json                          ★ CRITICAL - Mod metadata file
├── README.md                              📖 Full documentation (start here!)
├── CHECKLIST.md                           ✓ Development checklist
├── EXAMPLES.md                            📋 Copy-paste JSON examples
├── DIRECTORY_STRUCTURE.md                 📁 This file
│
├── Common/                                🎨 CLIENT-SIDE ASSETS
│   │                                         (Visual appearance)
│   │
│   ├── Blocks/                            📦 Block definition files
│   │   │                                      (If creating custom blocks)
│   │   └── [YourBlockName.json]
│   │
│   ├── BlockTextures/                     🖼️  Block texture files
│   │   │                                      (Maps textures to block faces)
│   │   └── [YourTexture.json]
│   │
│   ├── Icons/
│   │   └── ItemsGenerated/                👁️  Item inventory icons
│   │       │                                   (PNG files - 64x64 recommended)
│   │       ├── YourItem.png               
│   │       ├── AnotherItem.png
│   │       └── ...
│   │
│   ├── Items/                             🎁 Item visual definitions
│   │   │                                      (How items look in world)
│   │   └── [YourItem.json]
│   │
│   └── Resources/                         📦 3D models and textures
│       │
│       ├── Models/                        🎭 3D blockymodel files
│       │   ├── YourItem.blockymodel
│       │   ├── AnotherItem.blockymodel
│       │   └── ...
│       │
│       └── Textures/                      🖼️  Texture PNG files
│           ├── YourItem_Texture.png
│           ├── YourItem_Normal.png
│           └── ...
│
└── Server/                                ⚙️  SERVER-SIDE CONFIGURATION
    │                                          (Game logic & mechanics)
    │
    ├── Drops/                             🎁 Item drop tables
    │   ├── Item/
    │   │   ├── Drops_YourBlock.json       (What drops when broken)
    │   │   └── ...
    │   │
    │   ├── Crop/                          🌾 Farm drop tables
    │   │   ├── Coffee/
    │   │   │   └── Drops_Plant_Crop_Coffee_Block.json
    │   │   └── ...
    │   │
    │   └── Mob/                           👹 Mob drop tables
    │       └── ...
    │
    ├── Entity/                            👤 Entity-related configs
    │   │
    │   ├── Effects/                       ⚡ Status effects/buffs
    │   │   ├── Poison.json                (Damage over time, etc)
    │   │   ├── Regeneration.json
    │   │   └── ...
    │   │
    │   ├── Stats/                         📊 Entity attributes
    │   │   ├── Health.json
    │   │   ├── Strength.json
    │   │   └── ...
    │   │
    │   └── Interactions/
    │       └── ...
    │
    ├── Item/                              🎒 Item system configs
    │   │
    │   ├── Block/
    │   │   └── Hitboxes/                  📐 Block collision boxes
    │   │       ├── YourBlock_Hitbox.json
    │   │       └── ...
    │   │
    │   ├── Interactions/                  🔄 Block interactions
    │   │   ├── YourBlock_Hit.json         (Break/harvest behavior)
    │   │   └── ...
    │   │
    │   ├── Items/                         ★ MOST IMPORTANT
    │   │   │                                 (All item definitions go here)
    │   │   ├── ExampleItem.json           (Start with these as templates)
    │   │   ├── YourItem.json
    │   │   ├── AnotherItem.json
    │   │   └── ...
    │   │
    │   ├── Recipes/                       👨‍🍳 Crafting/cooking recipes
    │   │   ├── Recipe_YourItem.json
    │   │   ├── Recipe_CookedFood.json
    │   │   └── ...
    │   │
    │   └── ResourceTypes/                 🏷️  Resource categories
    │       ├── Foods.json
    │       ├── Ores.json
    │       ├── YourResourceType.json
    │       └── ...
    │
    ├── Languages/                         🌍 Localization/translations
    │   │
    │   ├── en-US/
    │   │   ├── server.lang                📝 English translations
    │   │   │   server.items.YourItem.name=Your Item Name
    │   │   │   server.items.YourItem.description=...
    │   │   │   server.recipes.Recipe_YourItem.name=...
    │   │   │   server.effects.Poison.name=...
    │   │   │   
    │   │   └── (other en-US translations)
    │   │
    │   ├── fr-FR/                         (French - optional)
    │   │   └── server.lang
    │   │
    │   ├── de-DE/                         (German - optional)
    │   │   └── server.lang
    │   │
    │   └── [other language codes]/        (More languages - optional)
    │       └── server.lang
    │
    └── Other Potential Folders/           (Advanced - optional)
        ├── Sounds/                        🔊 Audio files
        ├── Particles/                     ✨ Particle effects
        ├── VFX/                           💥 Visual effects
        ├── NPC/                           👨 NPC definitions
        ├── World/                         🌍 World generation
        ├── Weathers/                      ⛈️  Weather effects
        └── ...
```

## File Type Reference

| Extension | Purpose | Location | Notes |
|-----------|---------|----------|-------|
| `.json` | Configuration | All folders | Must be valid JSON |
| `.png` | Textures & Icons | Common/Resources, Common/Icons | 32-bit PNG with transparency |
| `.blockymodel` | 3D Models | Common/Resources | Created in Hytale Block Editor |
| `.lang` | Translations | Server/Languages/ | Key=Value format |
| `.md` | Documentation | Root folder | Markdown format |

## Folder Organization Strategy

### By Content Type

**Visual Assets (Common/):**
- Everything related to how things look
- Models, textures, icons
- Client downloads these

**Game Mechanics (Server/):**
- Everything related to how things work
- Items, recipes, drops, effects
- Server processes these

### By Function

**Must Have:**
- ✓ manifest.json
- ✓ Server/Item/Items/ (item definitions)
- ✓ Server/Languages/en-US/server.lang (translations)
- ✓ Common/Icons/ItemsGenerated/ (item icons)

**Usually Have:**
- ✓ Common/Resources/ (models & textures)
- ✓ Server/Drops/ (drop tables)
- ✓ Server/Item/Recipes/ (crafting recipes)

**Depends on Mod:**
- ○ Server/Entity/Effects/ (status effects)
- ○ Server/Item/Block/Hitboxes/ (custom collision)
- ○ Server/Item/Interactions/ (special interactions)
- ○ Additional language folders

**Optional/Advanced:**
- ○ Server/Entity/Stats/ (custom attributes)
- ○ Server/Sounds/ (audio)
- ○ Server/Particles/ (particle effects)

## Naming Conventions

### Folder Names
- Use PascalCase: `Common`, `Server`, `BlockTextures`
- Use descriptive names: `ItemsGenerated`, not `Items2`

### File Names
- Use snake_case: `your_item_name.json`, `coffee_bean.blockymodel`
- Be descriptive: `Drops_YourBlock.json`, not `drops.json`
- Use prefixes for organization: `Recipe_`, `Drops_`, `Effect_`

### JSON Keys (Inside Files)
- Use camelCase: `"customModel"`, `"hitboxType"`
- Be consistent within your mod
- Follow Hytale's conventions (see example files)

### Translation Keys
- Use dot notation: `server.items.YourItem.name`
- Pattern: `server.category.itemname.property`
- Keep alphabetically organized in .lang files

## Quick Copy-Paste Structure

When creating a new mod, copy-paste this folder structure:

```bash
ModName_1.0.0/
├── manifest.json
├── Common/
│   ├── Blocks/
│   ├── BlockTextures/
│   ├── Icons/ItemsGenerated/
│   ├── Items/
│   └── Resources/
└── Server/
    ├── Drops/Item/
    ├── Entity/Effects/
    ├── Entity/Stats/
    ├── Item/Block/Hitboxes/
    ├── Item/Interactions/
    ├── Item/Items/
    ├── Item/Recipes/
    ├── Item/ResourceTypes/
    └── Languages/en-US/
```

## File Count Reference

A minimal mod might have:
- 1-5 JSON files in Server/Item/Items/
- 1-3 icon PNG files in Common/Icons/ItemsGenerated/
- 1-3 model/texture files in Common/Resources/
- 1 server.lang file in Server/Languages/en-US/
- 1 manifest.json
- **Total: ~10-15 files**

A medium mod might have:
- 10-20 item definitions
- 10-20 icons
- 10-20 models/textures
- 5-10 recipes
- 5-10 drops
- 1 manifest.json
- **Total: ~50-80 files**

A large mod might have:
- 50+ items
- Full recipe system
- Multiple workbenches
- Entity effects
- Custom effects/sounds
- Multiple languages
- **Total: 200+ files**

## Minimum Viable Mod

The absolute minimum to get a working mod:
```
MinimalMod/
├── manifest.json
├── Common/
│   └── Icons/ItemsGenerated/
│       └── MyItem.png
└── Server/
    ├── Item/Items/
    │   └── MyItem.json
    └── Languages/en-US/
        └── server.lang
```

(With a 64x64 PNG icon and proper JSON files)

---

This structure is designed to be scalable - start minimal and add folders as your mod grows!
