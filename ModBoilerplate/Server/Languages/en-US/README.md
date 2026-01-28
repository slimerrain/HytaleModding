# Server/Languages/en-US

This folder contains translation files for all text in your mod.

## Files in This Folder

### server.lang
This is your translation file. It uses a simple key=value format where:
- **Left side (before =)**: Translation key (used in JSON files)
- **Right side (after =)**: The actual text displayed to players

## Format

```
server.items.ItemName.name=Display Name Here
server.items.ItemName.description=Description text here.
server.recipes.RecipeId.name=Recipe Name
server.effects.EffectName.name=Effect Display Name
```

## Key Naming Convention

Follow this pattern for organization:

```
server.CATEGORY.itemid.property=Text

Categories:
- items
- recipes
- effects
- stats
- blocks

Properties:
- name (display name)
- description (what it does)
```

## Examples

```
# Items
server.items.CoffeeBeans.name=Coffee Beans
server.items.CoffeeBeans.description=Roasted coffee beans, ready to brew.
server.items.AppleRed.name=Red Apple
server.items.AppleRed.description=A delicious red apple.

# Recipes
server.recipes.Recipe_Coffee.name=Brew Coffee
server.recipes.Recipe_Coffee.description=Create a warm cup of coffee.

# Effects
server.effects.Caffeine.name=Caffeinated
server.effects.Caffeine.description=Increased movement speed.

# Stats
server.stats.Hunger.name=Hunger
server.stats.Energy.name=Energy
```

## Tips for Translation Keys

1. **Be Consistent**: Use same pattern throughout
2. **Use Lowercase**: Keys should be lowercase (names can be uppercase)
3. **Use Underscores**: Separate words with underscores if needed
4. **Alphabetize**: Keep entries alphabetized for easy finding
5. **Be Descriptive**: Keys should hint at what they represent

## Adding Other Languages

To support other languages, create additional folders:

```
en-US/
  server.lang     (English)
  
fr-FR/
  server.lang     (French)
  
de-DE/
  server.lang     (German)
  
es-ES/
  server.lang     (Spanish)
```

Each file uses the same key format, just with translated text.

## How to Use in JSON Files

Reference translation keys in your JSON files:

```json
{
  "TranslationProperties": {
    "Name": "server.items.CoffeeBeans.name",
    "Description": "server.items.CoffeeBeans.description"
  }
}
```

Then define them in server.lang:

```
server.items.CoffeeBeans.name=Coffee Beans
server.items.CoffeeBeans.description=Roasted coffee beans, ready to brew.
```

## Validation

- [ ] All translation keys in JSON files exist in server.lang
- [ ] No duplicate keys
- [ ] All keys are defined
- [ ] Text matches the context
- [ ] Spelling and grammar are correct
