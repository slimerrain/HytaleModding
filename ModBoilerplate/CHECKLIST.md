# Mod Creation Checklist

Use this checklist when creating your mod to ensure you don't miss any important steps.

## Pre-Development
- [ ] Decide on your mod concept and features
- [ ] Create a folder name for your mod (use ModName_Version format)
- [ ] Plan your item naming convention (e.g., Prefix_ItemName)

## Manifest Setup
- [ ] Copy manifest.json from ModBoilerplate as template
- [ ] Set "Group" to your name/organization
- [ ] Set "Name" to your mod's display name
- [ ] Set "Version" following semantic versioning (1.0.0)
- [ ] Write descriptive "Description" of what mod does
- [ ] Fill in "Authors" with your info
- [ ] Set "IncludesAssetPack" to true (if you have Common/ folder content)
- [ ] Validate JSON syntax (use jsonlint.com if unsure)

## Item Creation (per item)
- [ ] Create JSON file in `Server/Item/Items/`
- [ ] Choose appropriate "Parent" template type
- [ ] Add translation key to "Name" field
- [ ] Add translation key to "Description" field
- [ ] Set "Quality" (Common, Uncommon, Rare, etc.)
- [ ] Reference icon path in "Icon" field
- [ ] If using 3D model, reference model in "CustomModel"
- [ ] If using model, add texture reference in "CustomModelTexture"
- [ ] Set appropriate "HitboxType" for collision

## Assets (per item)
- [ ] Create `.blockymodel` file in `Common/Resources/` (if 3D model needed)
- [ ] Create texture `.png` file in `Common/Resources/` (if using model)
- [ ] Create icon `.png` file in `Common/Icons/ItemsGenerated/`
- [ ] Icon file name matches item ID (e.g., YourItem.png)
- [ ] All texture files are proper PNG format with transparency

## Translations
- [ ] Add all translation keys to `Server/Languages/en-US/server.lang`
- [ ] Use consistent naming pattern for keys (e.g., `server.items.ItemName.name`)
- [ ] Add descriptions for all items
- [ ] Check for typos in translations

## Drops and Interactions (if applicable)
- [ ] Create drop files in `Server/Drops/Item/` for each block
- [ ] Define correct ItemId in drop files
- [ ] Create interaction files in `Server/Item/Interactions/` (if needed)
- [ ] Test drop behavior in-game

## Recipes (if applicable)
- [ ] Create recipe files in `Server/Item/Recipes/` for each recipe
- [ ] Verify input ItemIds exist
- [ ] Verify output ItemIds exist
- [ ] Set realistic crafting times
- [ ] Add recipe translations if needed

## Resource Types (if creating new categories)
- [ ] Create resource type JSON in `Server/Item/ResourceTypes/`
- [ ] Add items to correct resource types
- [ ] Define appropriate color for resource type
- [ ] Set weight/priority values

## Testing
- [ ] Verify manifest.json syntax is valid
- [ ] Check all JSON files for syntax errors
- [ ] Ensure all referenced file paths exist
- [ ] Ensure all translation keys are defined
- [ ] Copy mod to Hytale mods folder
- [ ] Launch game and enable mod
- [ ] Verify all items appear in creative/inventory
- [ ] Test crafting recipes work
- [ ] Test drops occur correctly
- [ ] Check for game log errors
- [ ] Test with other mods enabled (compatibility)

## Polish and Documentation
- [ ] Create comprehensive README for your mod
- [ ] Document item list and stats
- [ ] Create recipe documentation
- [ ] Add usage instructions
- [ ] Take screenshots for mod page
- [ ] Verify version number matches manifest

## Before Release
- [ ] Final playtest with fresh game load
- [ ] Test mod disable/removal doesn't break game
- [ ] Verify no console errors or warnings
- [ ] Update version number in manifest
- [ ] Create mod distribution package
- [ ] Write release notes

## Optional Advanced Features
- [ ] Custom entity effects in `Server/Entity/Effects/`
- [ ] Custom stats in `Server/Entity/Stats/`
- [ ] Block interaction systems
- [ ] Mob drop tables
- [ ] Farming/crop systems
- [ ] Workbench/crafting station definitions

---

**Progress: ___/50 core tasks completed**

Keep this checklist handy as you develop your mod!
