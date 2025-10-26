# Arc Raiders Tools/Guides Page Structure
This document outlines the structure and content for my Arc Raiders Tools/Guides page including pages, data sources, and examples of data formats.

## Technical Stack
### Known:
- React.js, Next.js, TypeScript, vercel or Netlify for hosting, clerk for auth
### Unknown:
- Databse? Convex, Prisma?
- State Manegemement required?


# Pages

## 1. Arc-dex (wait for Fandom data updates)
- List of all enemies with pictures
- spawn points
- weak parts
- drops

## 2. Maps for out of raid access (wait for Fandom data updates)
- pngs of all maps
- locations of sentry and sniper turrets?
- weapon crate spawns


## 4. Quest Tracker
**Decisions:**
1. DEPENDENCIES: metro view or flow chart view?
2. OVERVIEW: quest cards with/without kanban style?
- User Tipps page with upvoting like reddit


## 5. Required quest and workstation upgrade items
- List of all required quest items 
- card components for each item with interactive +/- buttons
- links to related quest
- requirements should update when quests are completed and workstations are upgraded

## 6. Skill Tree
- Skill tree with all skills
- interactive

## 7. Workstation Upgrades
- List of all workstations with upgrade requirements
- interactive upgrade tracker


# Data 

## How to consume data?
- Data is available in the [Github repo](https://github.com/RaidTheory/arcraiders-data/tree/main)
- Should I set up my own (document/keay-value) db or use the github repo directly? Maybe set up a cron job to pull all json data every 24h  and use pngs off cdn links?


## Unknown data
- interactive Maps
- arc enemy drops 
- arc enemy spawns?

## Github repo data example data:
- **Workstation Upgrades**
``` json
[
  {
    "id": "scrappy",
    "name": "Scrappy",
    "maxLevel": 6,
    "levels": [
      { "level": 1, "requirementItemIds": [] },
      { "level": 2, "requirementItemIds": [{ "itemId": "dog_collar", "quantity": 1 }, { "itemId": "torn_blanket", "quantity": 1 }] },
      { "level": 3, "requirementItemIds": [{ "itemId": "lemon", "quantity": 5 }, { "itemId": "apricot", "quantity": 5 }] },
      { "level": 4, "requirementItemIds": [{ "itemId": "prickly_pear", "quantity": 8 }, { "itemId": "olives", "quantity": 8 }, { "itemId": "cat_bed", "quantity": 1 }] },
      { "level": 5, "requirementItemIds": [{ "itemId": "apricots", "quantity": 12 }, { "itemId": "mushrooms", "quantity": 12 }, { "itemId": "very_comfortable_pillow", "quantity": 3 }] },
      { "level": 6, "requirementItemIds": [{ "itemId": "unknown_item", "quantity": 99 }] , "prerequisites": ["Unknown at this time"] }
    ]
  },
  {
    "id": "weapon_bench",
    "name": "Weapon Bench",
    "maxLevel": 3,
    "levels": [
      { "level": 1, "requirementItemIds": [{ "itemId": "metal_parts", "quantity": 20 }, { "itemId": "rubber_parts", "quantity": 30 }], "otherRequirements": ["3x Raids"] },
      { "level": 2, "requirementItemIds": [{ "itemId": "rusted_tools", "quantity": 3 }, { "itemId": "mechanical_components", "quantity": 3 }, { "itemId": "wasp_driver", "quantity": 8 }] },
      { "level": 3, "requirementItemIds": [{ "itemId": "rusted_gear", "quantity": 5 }, { "itemId": "advanced_mechanical_components", "quantity": 3 }, { "itemId": "sentinel_core", "quantity": 3 }] }
    ]
  },
]
```

- **Items**
``` json
[
  {
    "id": "fabric",
    "name": "Fabric",
    "description": "A common crafting material.",
    "type": "Material",
    "imageFilename": "https://cdn.arctracker.io/items/fabric.png"
  },
  {
    "id": "tick_pod",
    "name": "Tick Pod",
    "description": "The explosive pod from a Tick.",
    "type": "Material",
    "imageFilename": "https://cdn.arctracker.io/items/tick_pod.png"
  },
  {
    "id": "metal_parts",
    "name": "Metal Parts",
    "description": "Used to craft a wide range of items.",
    "type": "Material",
    "rarity": "Common",
    "value": 75,
    "weightKg": 0.15,
    "imageFilename": "https://cdn.arctracker.io/items/metal_parts.png"
  },
]
```

- **Quests**
``` json
[
  {
    "id": "m1",
    "name": "Topside",
    "trader": "Shani",
    "objectives": ["Go topside for the first time", "Optional - Ping any ARC"],
    "rewardItemIds": [
      { "itemId": "ferro_i", "quantity": 1 },
      { "itemId": "heavy_ammo", "quantity": 20 }
    ],
    "xp": 4000
  },
  {
    "id": "m2",
    "name": "The Bandage Run",
    "trader": "Lance",
    "objectives": ["Search 5 containers", "Get 15 pieces of Fabric for Lance"],
    "requiredItemIds": [{ "itemId": "fabric", "quantity": 15 }],
    "rewardItemIds": [{ "itemId": "herbal_bandages", "quantity": 3 }],
    "xp": 4000
  },
]
```

- **Skills**
``` json
[
  {
    "id": "cond_1",
    "name": "Youthful Lungs",
    "description": "Increase your max stamina.",
    "impactedSkill": "Max Stamina",
    "knownValue": [],
    "category": "CONDITIONING",
    "maxPoints": 5,
    "iconName": "skill_running.png",
    "isMajor": true,
    "position": {
      "x": 25,
      "y": 75
    },
    "prerequisiteNodeIds": []
  },
  {
    "id": "cond_2l",
    "name": "Stubborn Mule",
    "description": "Your stamina regeneration is less affected by being over-encumbered.",
    "impactedSkill": "Stamina Regneration",
    "knownValue": [],
    "category": "CONDITIONING",
    "maxPoints": 5,
    "iconName": "skill_weight.png",
    "isMajor": false,
    "position": {
      "x": 20,
      "y": 65
    },
    "prerequisiteNodeIds": [
      "cond_1"
    ]
  },
  {
    "id": "mob_1",
    "name": "Nimble Climber",
    "description": "You can climb and vault more quickly.",
    "impactedSkill": "Climb and Vault Speed",
    "knownValue": [],
    "category": "MOBILITY",
    "maxPoints": 5,
    "iconName": "skill_climbing.png",
    "isMajor": true,
    "position": {
      "x": 50,
      "y": 75
    },
    "prerequisiteNodeIds": []
  },
  {
    "id": "surv_1",
    "name": "Looter's Instincts",
    "description": "When searching a container, loot is revealed faster",
    "impactedSkill": "Loot Speed",
    "knownValue": [],
    "category": "SURVIVAL",
    "maxPoints": 5,
    "iconName": "skill_crate.png",
    "isMajor": true,
    "position": {
      "x": 75,
      "y": 75
    },
    "prerequisiteNodeIds": []
  },
]
```
